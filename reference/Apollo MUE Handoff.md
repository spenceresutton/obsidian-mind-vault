---
title: Apollo Studio MUE — Claude Code Project Handoff
date: 2026-06-03
description: "Foundational context for the Apollo MUE synthetic-data engine — architecture, dual-cohort model, calcitonin base case, anticoagulation stress case, validation lessons. Imported from the Claude.ai build."
type: project-context
status: living-document
backbone: Obsidian + Claude Code
tags:
  - reference
  - apollo-studio
  - mue
  - synthetic-data
  - anticoagulation
aliases:
  - MUE Handoff
  - Apollo MUE Handoff
---

> [!info] Vault context
> Imported source-of-truth context for the [[Apollo MUE Data Engine]] project. Original captured from the Claude.ai build on 2026-06-03 (`~/Downloads/Apollo_Studio_MUE_ClaudeCode_Handoff.md`). The lessons in §6 should be promoted to atomic notes in [[Gotchas]] / [[Patterns]] as they're applied.

# Apollo Studio MUE — Claude Code Project Handoff

> **Purpose of this document.** This is the context-ingest file for moving the Apollo Studio MUE synthetic-dataset work into Claude Code with an Obsidian vault as the knowledge backbone. It captures what we are building, how we build it, the hard-won validation lessons, and where the work is going. Calcitonin is used as the worked base case because it is the most mature. Anticoagulation is treated separately and at length because its complexity is the real test of the architecture — and the place where a live Claude Code loop creates the most leverage.

---

## 1. What Apollo Studio Is, and What We Are Doing

**Apollo Studio** is InsightRX's analytics AI engine. It sits above a clinical data lake and supports *chat-to-plot* and bespoke investigation across that lake. The bar for a useful demo is not "it produces charts" — it is "it surfaces a non-obvious clinical pattern that a pharmacy manager would actually act on."

Apollo's provider-facing layer is organized as **Medication Use Evaluation (MUE) modules**. Every MUE module has the same six-tab architecture:

1. **Utilization** — volume, agent/indication mix, DOT trends
2. **Clinical Outcomes** — the outcome measures the whole module rolls up to
3. **Process Measures** — the assessments that *flow up into* the outcome of "appropriately managed"
4. **Operational** — staffing, monitoring gaps, intervention acceptance
5. **Provider Performance** — prescriber-level attribution and case fallout
6. **Reports** — P&T-ready summaries

Layered on top is an **Active Patients** worklist: a real-time triage surface where flags are sorted by urgency (**Critical / High / Routine**), each carrying enough auto-populated clinical context for a pharmacist to act without opening the chart.

**Our role in the project:** we build *synthetic but clinically-calibrated* datasets that (a) drive product demos and (b) stress-test Apollo's analytics engine across all six tabs plus the Active Patients layer. The datasets are fake at the row level but faithful at the distributional and causal level — that fidelity is the entire point.

### The MUE roadmap
- **Calcitonin** — most mature; two builds completed (POC, then in-depth). Base case for everything below.
- **Anticoagulation** — built (5,675 patients, 29,228 DOT rows); the complexity stress case. See §5.
- **Planned:** IVIG, albumin, cangrelor, parenteral nutrition, nonformulary. Each is a new *config*, not a new codebase.

### The Apollo design system (apply to every export and dashboard)
| Token | Value | Use |
|---|---|---|
| Navy | `#1A2E3B` | Headers |
| Teal | `#E1F5EE` | Row banding |
| Amber | `#FFF3CD` | Process-failure flag columns |
| Red | `#FFE8E8` | Appropriateness flag columns |

Excel exports additionally use a frozen header row and enabled auto-filters. Treat these tokens as a **shared design-system artifact** (`apollo_design_system.yaml`), separate from any single MUE — they change on a rebrand, not on a clinical update.

---

## 2. Target Architecture (where the code is going)

The proof-of-concept was a monolithic Python build script per MUE. The direction is a **config-driven engine**:

```
Lovable React App (TypeScript)          ← UI: literature upload, parameter review,
   │   POST /generate                      column config, DAG view, validation dashboard
   │   { config_yaml, seed, column_overrides, design_system_version }
   ▼
Modal Python Worker (HTTP endpoint)     ← the validated statistical engine
   ├─ parse_config(yaml) → MUEConfig
   ├─ build_dag(config) → DAG           ← topologically sorted, cycle-checked at load
   ├─ sample_cohort(dag, seed) → DataFrame
   ├─ validate(df, config) → ValidationReport   ← post-generation pass, rerunnable
   ├─ emit_csv / emit_xlsx(design_system)
   ▼
Response: { csv_b64, xlsx_b64, validation, row_count, generation_time_ms }
```

**Decisions already made and why they hold:**

- **YAML config per MUE, one shared engine.** A clinical pharmacist thinks in indication / agent / process-measure / outcome blocks — YAML maps to that mental model and is editable without touching generation code. New MUE = new config file.
- **External Python worker on Modal**, not a TypeScript port and not Pyodide. The engine does statistically serious work (NumPy distributions, scipy copulas for latent drivers, pandas, openpyxl). It earned trust over ~a dozen calibration iterations; rewriting it in a language without the scientific stack throws that away. Modal scales to zero (generation is a 2–5s burst, not a sustained load) and returns binary files cleanly.
- **Typed contract on both sides first.** Define the request/response as a TypeScript interface *and* a Pydantic model before writing generation logic. Nearly every integration bug in this architecture is a frontend/worker schema mismatch; a typed contract eliminates the class.
- **DAG with topological sampling.** Each node is sampled after its parents, receiving their values as context. This is what lets the engine enforce *conditional existence* of variables (e.g. a monitoring parameter only exists for agents that are monitored) and the universal-drug-effect rule (see Lesson #2) declaratively rather than through scattered if-statements. ~300–400 lines, then it stops changing — only configs change.
- **Engine pattern: latent drivers + logistic outcomes (both).** Latent drivers handle *failure correlation* (Lesson #5); logistic models keep *outcomes anchored to pharmacology* (Lesson #2). The latent driver appears in outcome models only as a tiny coefficient — enough that a chaotic care episode correlates weakly with worse outcomes, never enough to let appropriateness drive outcomes through the back door.

> **Practical sequencing note carried over:** do not build a fully generic engine first. Let the *anticoagulation* config (the hard one) reveal what the engine must handle generically, then retro-fit calcitonin. Abstracting before two concrete configs exist produces an engine that is over-engineered and under-specified at the same time.

There is also a parallel **Lovable "Literature-to-Dataset Studio"** (four workspaces: Literature ingest → Schema Builder → Rate Calibration → Dataset Generator) intended to make the above self-serve. Claude Code should treat that as the eventual UI consumer of the same engine + contract.

---

## 3. Dataset Architecture Requirements (every MUE, regardless of drug)

These are invariant. They are the reason the data survives clinical scrutiny.

**Dual cohort model.** Three structural columns on every dataset:
- `cohort` — `Drug Cohort` | `Disease State Only`
- `drug_administered` — `True` | `False`
- `withheld_reason` — `null` for the drug cohort; a reason string otherwise

The *Disease State Only* cohort splits into:
- **Appropriately withheld** — the correct clinical decision; outcomes reflect the natural disease trajectory.
- **Care gap** — indicated but not given; outcomes reflect the penalty of untreated disease. **This is the single most important demo signal** — care-gap patients must carry the worst outcomes, or the comparison the whole module exists to make collapses.

**Outcome drivers.** Outcomes are driven by *clinical variables, never by the appropriateness classification.* A drug's pharmacological effect applies equally to everyone who received it, regardless of whether the prescribing decision was correct. Drivers: starting disease severity, co-therapy and its timing, etiology-specific modifiers, and patient-level factors (renal function, weight, age).

**Prescribing-behavior model.** Service-level shortcut probabilities model real-world guideline non-adherence — documentation gaps and workflow shortcuts, modeled *independently per service* and kept distinct from clinical-appropriateness logic.

**Distributional realism.** No hard percentages anywhere. Every rate is a distribution around a target with natural variation. (The engine should warn if independent failure rates would make the perfect-management target unreachable — see Lesson #5.)

---

## 4. Base Case — Calcitonin (the worked example)

Final state: **653 patients, 62 columns, two cohorts** (Drug n=500, Disease State Only n=153). Patient-level grain (one row per patient). Single flat CSV + Apollo-formatted XLSX.

**Etiologies:** Solid Tumor Malignancy, Hematologic Malignancy, Primary Hyperparathyroidism (PHPT).

**Process measures (three):** bisphosphonate co-administration, appropriate discontinuation, lab completeness.

**Primary outcome:** time to eucalcemia (TTE), plus worsening hypercalcemia during admission, eucalcemia by discharge, 28-day readmission.

**Key calibrations that landed (and why they mattered):**
- **Fluid responsiveness is etiology-specific.** PTHrP-mediated / osteoclast-driven malignancy hypercalcemia is largely fluid-*refractory* (~7–10% solid tumor, ~10% heme), whereas PHPT has a volume-depletion component (~38–40%). An early model had malignancy responsiveness at ~20–30% — wrong, and it took fixing in *three* code paths, including a prescribing-shortcut path that was independently drawing a flat 48% regardless of etiology.
- **TTE driven by pharmacology, not appropriateness.** The original model cut TTE based on whether calcitonin was "appropriate." That was the central bug (see Lesson #2). The fix: make `drug_administered` the parent node and express drug effect as an additive `time_to_eucalcemia` modifier.
- **Bisphosphonate timing rebuild** and TTE recalibration to literature.
- Added `calcitonin_withheld_reason` distinguishing appropriate-withhold reasons (fluid responsive, moderate/asymptomatic, PHPT conservative) from care-gap reasons (fluid non-responsive but not ordered, severe symptoms but not ordered).

**Flag design pattern worth reusing everywhere:** distinguish *retrospective* analytics flags from *real-time* action flags.
- `flag_dose_count_exceeded` — retrospective; by the time it fires the intervention window has closed.
- `flag_dose_4_reached` — real-time; fires *at* dose 4 while a clinical decision still exists.

The config declares each flag with a trigger expression, severity (Critical/High/Routine), display name, and a `context_fields` list. The engine emits all `flag_*` booleans into the main dataset **and** a filtered long-format `active_patients` table containing only currently-firing rows where `active_patients: true`. `context_fields` (corrected calcium, symptoms, fluid status, etc.) belong in the flag definition, not hardcoded in the UI.

---

## 5. The Hard One — Anticoagulation (complexity, challenges, and where Claude Code earns its keep)

Final state: **5,675 patients, 29,228 DOT (day-of-therapy) rows**, spanning 2024. Three CSVs + one XLSX: `patient_index.csv` (one row/patient), `dot_table.csv` (one row per patient-day), and a denormalized flat join. Cohorts: Drug n=5,500; Care Gap n=108; Delayed n=67. 24 unique providers.

### Why anticoagulation is categorically harder than calcitonin

Calcitonin is patient-level and largely static. Anticoagulation is **longitudinal, conditional, and stateful** — four distinct sources of complexity, all of which are exactly the kind of thing a live Claude Code loop is good at and a one-shot script is bad at:

1. **Daily grain with temporal structure.** Outcomes and process failures accrue *over* a length of stay, not at a point. DOT-day allocation must reconcile to a target total (29,228) *and* respect per-patient LOS — an allocation/rounding problem that needs iterative correction passes to hit exactly.

2. **Conditional existence of variables (and the NA-≠-failure trap).** Monitoring only exists for monitored agents. DOACs (apixaban, rivaroxaban, dabigatran) have *no* routine monitoring requirement, so their monitoring fields are **NA — and NA must be excluded from denominators, never counted as a failure.** This is the most common way the analytics silently go wrong. Agent-specific monitoring: Warfarin → INR (2.0–3.0), UFH → aPTT (60–100), Enoxaparin → Anti-Xa (0.5–1.0), DOACs → none.

3. **State machines inside a patient.** The **HIT cascade** is a genuine state machine: concern → HIT antibody → SRA confirmation → therapeutic substitution to argatroban. Critically, **HIT is a *substitution*, not a withholding** — getting that wrong corrupts both the "appropriately withheld" process measure and the agent-mix utilization. Warfarin also carries a **bridge** (UFH/enox, days 1–5) and a **PK ramp-up**: warfarin TTR is only computed from **day 7+** because days 1–6 are subtherapeutic loading and must not be scored as failures.

4. **Multiple denominators and indication-specific outcomes.** There are *five* daily process assessments, each with its own applicable-population denominator, and outcomes that **cannot be averaged across indications** (untreated AFib stroke risk ≠ untreated DVT risk). The flat file *inflates* patient counts — always `DISTINCT patient_id`.

### The five daily process assessments (these flow up into "Anticoagulation appropriately managed")
| Assessment | Note |
|---|---|
| Renal & body-habitus dose | CrCl thresholds; BMI >40 / wt >140 kg triggers anti-Xa monitoring for enoxaparin |
| Monitoring appropriately managed | Correct parameter + frequency; **NA for DOACs, excluded** |
| Dose adjustment follows protocol | Adjust when out of range; correctly *don't* adjust when in range |
| Anticoagulation appropriately withheld | Valid documented reason (active bleed, imminent surgery, thrombocytopenia, traumatic ICH, refusal); **HIT substitutions excluded** |
| Duration appropriate | Within evidence-based treatment window for the indication |

### Reference numbers the dataset reconciles to (validation targets)
- Agent appropriate (drug cohort): **85.4%**
- DOT appropriate (all non-NA): **49.8%**
- Perfect management (patient-level, *strict* — a single monitoring gap = imperfect): **43%**
- Warfarin TTR (day 7+): **59.8%** — sits right in the moderate band (≥60% high, 50–70% moderate, <50% low), which is clinically meaningful, not an accident
- Bleeding events: **20**; Clot events: **30** (clots **enriched on untreated/care-gap rows** — the headline care-gap signal)
- Dabigatran patients: **8** (deliberately rare)

### Calcitonin → Anticoagulation mapping (what carries, what changes, what's net-new)
**Direct carry-forward:** monthly volume/appropriateness trends, indication/agent mix, cohort comparison table, LOS/cost/disposition, provider scatter + expandable case-fallout rows, reports.
**Materially enhanced:** Clinical Outcomes — TTR replaces eucalcemia as the primary time-to-event metric; bleed/clot replace worsening hypercalcemia; **care-gap consequences must be framed per indication, not averaged.**
**Net-new (no calcitonin analog):** process-failure co-occurrence heatmap; renal dose-appropriateness as a standalone KPI; monitoring-gap reason breakdown (overnight/weekend/not-ordered → staffing signal); reversal-agent appropriateness *and cost* (andexanet alfa ~$23,602 vs PCC ~$6,692); HIT timeline + outcomes section; UFH aPTT in-range alongside warfarin TTR; risk-score distributions (CHA₂DS₂-VASc, HAS-BLED, Padua, Caprini); stewardship intervention-acceptance rate.

---

## 6. Lessons Learned — Validation & Clinical Clarity (the part to internalize)

This is the explicitly requested section. These lessons cost real iteration; they are the difference between a dataset that demos and a dataset that survives a clinician poking at it.

### Clinical-modeling lessons (build these into every config)
1. **Severity and disease-state distributions must be evidence-based, not flat.** Calcitonin used a published palliative-care cohort to calibrate severity splits and symptom rates. Anticoagulation anchors on published VTE/AFib/ACS prevalence, bleeding/stroke risk scores, and renal-function distributions in anticoagulated inpatients. *Every distribution should trace to a source* (this is where the Obsidian backbone pays off — see §7).
2. **Outcomes are driven by clinical variables, never by the appropriateness classification.** The drug's effect is pharmacological, not administrative. Structurally enforce it: make `drug_administered` (not `appropriateness`) the outcome parent, and express drug effect as an additive modifier. Process-failure coefficients may exist in outcome models but must be *small, indirect, and pharmacologically justifiable* (e.g. supratherapeutic dosing genuinely raises bleed risk — that's pharmacology, not paperwork).
3. **Etiology/agent-specific modifiers are mandatory.** Fluid responsiveness by etiology (calcitonin); agent-specific monitoring and PK behavior (anticoagulation). Averaging across etiologies/agents is the most common realism failure.
4. **Conditional existence must be modeled, and NA must never be a failure.** A variable that does not apply (DOAC monitoring, warfarin days 1–6 for TTR) is NA and excluded from its denominator. This is both a modeling rule and a validation rule.
5. **Failures must be correlated, not independently stacked.** The perfect-management target (45–50% calcitonin; 43% anticoagulation) collapses if each failure mode is drawn independently. Early calcitonin iterations wasted passes tuning individual rates *down*; the real fix was a **shared latent driver** ("aggressive prescribing" / "suboptimal care episode") loading onto multiple failure modes so that bad episodes fail *together*. Add a **prescriber-level random effect** on top so some providers are *consistently* worse — that is what makes Provider Performance analytically findable rather than noise.

### Validation methodology (how we proved clarity)
- **Validation is a separate post-generation pass, not inline** — so it can be rerun after parameter tweaks without regenerating.
- **Reconcile against the written deliverables, not intermediate state.** Always validate the actual CSV/XLSX files, not the in-memory pickles — the bug is often in the *write*.
- **Two layers of checks:**
  - *Statistical/target checks* — every headline rate vs its literature target, with tolerance (no exact equality, because no hard percentages).
  - *Clinical-integrity checks* — assertions of clinical truths: DOAC monitoring is all-NA; warfarin TTR computed only day 7+; mechanical-valve patients are mostly warfarin; care-gap patients have a null agent; **clots are enriched on untreated rows**; the HIT cascade is present (Ab+ → SRA+ → argatroban).
- **Outcome-ordering is a first-class check.** Care-gap > treated for bad outcomes must hold *by construction and by test*. The most instructive bug we hit was exactly here: a pandas `None`-vs-`NaN` identity check silently put **zero clots on untreated patients**, neutralizing the central care-gap signal while every summary statistic still looked plausible. **Lesson: assert the directional clinical relationships explicitly — summary stats passing is not the same as the clinical story being intact.**
- **Determinism:** seed the engine; the same config + seed reproduces the dataset exactly. Reproducibility is part of clinical credibility.
- **Inspectability:** the distribution behind every column should be viewable. A reviewer must be able to ask "why is this value what it is" and get a traceable answer.

---

## 7. Claude Code + Obsidian Backbone — Enhancements with a Live Loop

This is the forward-looking section: what becomes possible once Claude Code is operating live against a repo *and* an Obsidian vault, rather than a single chat with an ephemeral container. (We have not built the Obsidian backbone yet — this is the design.)

### Proposed repo + vault layout
```
apollo-mue/
  engine/                 # the ~400-line DAG engine (stable)
  configs/
    calcitonin.yaml
    anticoagulation.yaml
    _design_system.yaml   # shared Apollo tokens
  validation/
    checks_common.py      # outcome-ordering, NA-denominator, distributional
    checks_<mue>.py        # per-MUE clinical-integrity assertions
  outputs/                # generated CSV/XLSX (gitignored)
  vault/                  # ← Obsidian
    MUEs/                 # one note per MUE, cross-linked
    Literature/          # one note per paper: extracted params + source quotes + page refs
    Lessons/             # the §6 lessons as atomic, linkable notes
    Evidence/            # parameter → source provenance (Dataview-queryable)
```

### Why Obsidian specifically fits this work
- **Provenance becomes navigable.** Lesson #1 demands every distribution trace to a source. In Obsidian each literature note holds the extracted parameter, the source sentence, page number, and study population; each MUE config value links to its evidence note. A Dataview query can then answer "show every parameter in the anticoagulation config with no linked source" — turning "is this evidence-based?" into a query instead of an argument.
- **Lessons stop being tribal knowledge.** The §6 lessons live as atomic notes, linked from every MUE that applies them. New MUEs inherit the checklist by backlink rather than by someone remembering.
- **Cross-MUE reuse is visible.** The calcitonin→anticoagulation mapping (§5) is a set of links, not a table buried in a chat. When IVIG/albumin/cangrelor start, the carry-forward vs net-new analysis is a graph traversal.

### What a live Claude Code loop unlocks (especially for anticoagulation)
The anticoagulation complexity (§5) is precisely where the *read → write → run → inspect → fix → re-validate* loop matters:
- **Catch the clot-on-untreated class of bug automatically.** With the engine, the validation suite, and the vault's clinical-integrity assertions all in one workspace, Claude Code can run generation, run `validation/`, see a directional check fail, trace it to the `None`/`NaN` comparison, fix it, and re-run — in one session, instead of a human noticing a flat summary table looked fine.
- **DOT-day reconciliation as a tested loop.** The allocation/rounding-to-target problem is iterative by nature; a live loop converges it and asserts the total, rather than hand-tuning.
- **State-machine validation for HIT.** Encode the HIT cascade's legal transitions as assertions; Claude Code regenerates and verifies no illegal state (e.g. SRA+ without Ab+, or HIT modeled as a withhold) ever appears.
- **Config-first new MUEs.** For IVIG/albumin/etc., Claude Code reads the literature PDFs into vault notes, drafts the YAML config with each value linked to its evidence note, runs the shared engine + common checks, and only the *clinical-integrity* check file is genuinely new per MUE.
- **The typed contract becomes enforceable in-repo.** Keep the TypeScript interface and the Pydantic model in the repo; Claude Code can diff them and fail CI on drift — closing the single largest source of integration bugs.

### Immediate next steps for Claude Code on entry
1. Stand up the repo/vault skeleton above; commit `_design_system.yaml`.
2. Port the **anticoagulation** build script into `engine/` + `configs/anticoagulation.yaml` first (it defines the hard requirements); retro-fit calcitonin.
3. Lift the §6 validation methodology into `validation/checks_common.py` (distributional + outcome-ordering + NA-denominator) and an anticoagulation `checks_*.py` (DOAC-NA, TTR day-7+, HIT cascade, clot-enrichment-on-untreated).
4. Create the vault's Lesson and Evidence notes; link every existing anticoagulation parameter to a source (flag the unsourced ones).
5. Lock the typed request/response contract (TS + Pydantic) before any further engine work.

---

## 8. One-paragraph orientation (if you read nothing else)

We generate synthetic-but-clinically-faithful patient datasets to demo and stress-test InsightRX's Apollo Studio MUE modules (six tabs + an Active Patients worklist). Datasets use a dual-cohort model (drug vs disease-state-only, the latter split into appropriately-withheld vs care-gap), with outcomes driven by *clinical variables and pharmacology — never by the appropriateness label* — and process failures *correlated via a shared latent driver* so the perfect-management rate holds. Calcitonin is the mature patient-level base case; anticoagulation is the hard, longitudinal, stateful case (daily DOT grain, agent-specific monitoring with NA-≠-failure, the HIT state machine, warfarin PK ramp-up, indication-specific outcomes) and is the right thing to port first. Validation is a separate, rerunnable pass that checks both statistical targets *and* explicit clinical-integrity/outcome-ordering assertions against the written files — because the worst bugs (e.g. zero clots on untreated patients) leave every summary statistic looking fine. The destination is a YAML-config-driven Python engine on Modal behind a typed contract, with Obsidian as the provenance-and-lessons backbone so every parameter traces to evidence and every lesson is inherited by link.

---

## Related

- [[Apollo MUE Data Engine]] — the project roadmap/tracker this context feeds
- [[Apollo Studio]] — GTM/sales project
- [[Gotchas]] — clinical-modeling traps (NA-≠-failure, clot-on-untreated)
- [[Patterns]] — reusable engine/validation patterns
