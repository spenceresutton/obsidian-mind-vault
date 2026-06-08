---
date: 2026-06-03
description: "Living roadmap and tracker for the Apollo Studio MUE synthetic-data engine — config-driven generation, evidence-grounded distributions, validation, and Apollo integration. Anticoagulation is the first build."
tags:
  - work-note
  - active
  - project
status: active
quarter: Q2-2026
aliases:
  - Apollo MUE
  - MUE Data Engine
  - Synthetic Data Engine
---

# Apollo MUE Data Engine — Roadmap & Tracker

Living document. Built across many sessions. Read the **Status** block first, then the **Session Log** for where we left off. Update both at the end of every working session.

Build synthetic-but-clinically-faithful patient datasets that demo and stress-test Apollo Studio's MUE modules. Datasets are fake at the row level, faithful at the distributional and causal level. Every distribution traces to published literature. The framework is reusable across therapeutic areas; **anticoagulation is the first build and the architecture stress test**.

This is the data-generation build. The GTM/sales project is [[Apollo Studio]]. Related: [[Q2 2026 OKRs]].

> [!info] Source context
> Design and lessons live in [[Apollo MUE Handoff]] (imported 2026-06-03 from the Claude.ai build). Worked base case: calcitonin. Stress case and first build: anticoagulation.

---

## Status

| Field | Value |
|---|---|
| **Current phase** | Phase 0 — Foundation & Decisions |
| **Last worked** | 2026-06-03 |
| **Next action** | Resolve the open architecture decisions (D1–D5 below) and locate existing code/data assets |
| **Blockers** | Awaiting answers to Open Questions Q1–Q6 |
| **First build** | Anticoagulation |
| **Model in use** | Opus 4.8 (clinical accuracy + multi-step reasoning) |

---

## Architecture Decisions

Decision log. Resolve the open ones before deep building. Promote significant ones to [[Key Decisions]] when settled.

| ID | Decision | Status | Resolution / Lean |
|---|---|---|---|
| D1 | **Project location** — separate `apollo-mue` repo vs nested in `obsidian-mind` | OPEN | Lean: separate code repo for engine/configs/validation; provenance + lessons notes in vault, cross-linked |
| D2 | **Port vs rebuild** the existing calcitonin/anticoag build scripts | OPEN | Lean: rebuild engine clean (config-driven), lift calibrated numbers + validation assertions wholesale |
| D3 | **Modal vs local** generation | OPEN | Lean: local-first; keep typed contract so a Modal/UI layer can wrap later |
| D4 | **Patient ecosystem** — shared synthetic patient master vs disjoint per-MUE cohorts | OPEN | Lean: design the master layer now (cheap), build anticoag self-contained first, wire shared population in at MUE #2 |
| D5 | **Provenance enforcement** — citation-per-parameter as a hard validation gate vs advisory | OPEN | Lean: advisory for v1 headline rates, tighten to gate as library matures |
| — | Engine pattern: latent drivers (failure correlation) + logistic outcomes (pharmacology anchor) | SETTLED (carried) | From handoff §2 / Lessons #2, #5 |
| — | DAG with topological sampling; conditional existence declarative | SETTLED (carried) | From handoff §2 |
| — | Dual-cohort model (Drug vs Disease-State-Only → appropriately-withheld vs care-gap) | SETTLED (carried) | From handoff §3 |
| — | Validation = separate rerunnable pass; assert directional clinical relationships, not just summary stats | SETTLED (carried) | From handoff §6 |

---

## Roadmap

Phases are sequential but overlap. Checkboxes track milestones.

### Phase 0 — Foundation & Decisions
Goal: settle architecture, locate assets, stand up the skeleton.
- [ ] Resolve decisions D1–D5
- [ ] Locate existing build scripts + generated datasets (calcitonin 653pt; anticoag 5,675pt / 29,228 DOT)
- [ ] Import handoff doc into the vault as a reference note
- [ ] Stand up repo/vault skeleton (`engine/`, `configs/`, `validation/`, `outputs/`, evidence vault)
- [ ] Commit shared `_design_system.yaml` (Apollo tokens: navy/teal/amber/red, frozen header, autofilter)
- [ ] Lock the typed request/response contract (TS interface + Pydantic model)

### Phase 1 — Anticoagulation Engine v1 (the hard first build)
Goal: generate one literature-grounded anticoagulation dataset end to end.
- [ ] DAG engine (~300–400 lines): topological sampling, cycle check at load
- [ ] `anticoagulation.yaml` config: indications, agents, process measures, outcomes, flags
- [ ] Patient-index + DOT-day (longitudinal) grain; DOT reconciliation to target total
- [ ] Agent-specific monitoring with NA-≠-failure (Warfarin/INR, UFH/aPTT, Enox/anti-Xa, DOACs/none)
- [ ] HIT state machine (concern → Ab → SRA → argatroban substitution, NOT a withhold)
- [ ] Warfarin bridge + PK ramp (TTR day 7+ only)
- [ ] Latent driver + prescriber random effect for correlated failures
- [ ] Generate first dataset; eyeball against reference numbers

### Phase 2 — Evidence Backbone (provenance)
Goal: every headline distribution traces to a source, queryable.
- [ ] Literature note format: extracted parameter, source sentence, population, page/table ref
- [ ] Ingest RE-LY (NEJMoa1107039) and other anticoag anchors
- [ ] Link each config parameter to its evidence note
- [ ] Query: "show every parameter with no linked source"

### Phase 3 — Validation Hardening
Goal: clinical-integrity assertions that catch the silent bugs.
- [ ] `checks_common.py`: distributional + outcome-ordering + NA-denominator
- [ ] `checks_anticoag.py`: DOAC-NA, TTR day-7+, HIT cascade legality, clot-enrichment-on-untreated
- [ ] Reconcile to validation targets (agent-appropriate 85.4%, DOT-appropriate 49.8%, perfect-mgmt 43%, TTR 59.8%, bleeds 20 / clots 30)
- [ ] Determinism check: same config + seed → identical dataset

### Phase 4 — Apollo Output Contract & Integration
Goal: datasets are navigable in Apollo Studio across six tabs + Active Patients.
- [ ] Confirm Apollo's actual input schema/format
- [ ] Apollo-formatted XLSX emit (design system applied)
- [ ] `active_patients` long-format table (currently-firing flags, real-time vs retrospective)
- [ ] Validate the six-tab story renders end to end

### Phase 5 — Generalization & Calcitonin Retrofit
Goal: prove the framework is reusable.
- [ ] Retro-fit calcitonin onto the generic engine
- [ ] Document calcitonin→anticoag carry-forward vs net-new as links
- [ ] Patient-master layer (if D4 = shared ecosystem)

### Phase 6 — Scale & Self-Serve
Goal: scale to 100k rows and reduce manual loops.
- [ ] Scale + performance pass
- [ ] Automated learning from feedback (calibration loop)
- [ ] Optional Modal endpoint + UI consumer of the same contract
- [ ] Onboard MUE #3 (IVIG / albumin / cangrelor / PN / nonformulary) as config-only

---

## Capabilities to Build

The reusable AI tooling layer (Spencer's goals: targeted skills, workflow, automated learning, research, export). All proposed until Phase 0 closes.

| Capability | Form | Purpose | Status |
|---|---|---|---|
| Literature → evidence | skill/agent | Pull a paper, extract calibrated params + source quotes into an evidence note | proposed |
| Config generate | skill | Run the engine from a YAML config, emit CSV/XLSX | proposed |
| Validate | skill | Run the rerunnable validation pass, report target + clinical-integrity results | proposed |
| Calibrate (learn) | skill/loop | Feed validation deltas + reviewer feedback back into config params | proposed |
| Apollo export | skill | Emit Apollo-formatted XLSX + active_patients table | proposed |
| Evidence gate | agent | Flag config parameters with no linked source | proposed |

---

## Open Questions

Tracked until answered. See the conversation of 2026-06-03 for full framing.

- [ ] **Q1 — Assets:** Where do the existing build scripts + generated datasets live? Port or rebuild?
- [ ] **Q2 — Structure:** Repo location (D1), Modal vs local (D3), patient ecosystem (D4)?
- [ ] **Q3 — Evidence:** Citation granularity, ingestion method (PDF vs abstract), gate vs advisory (D5)?
- [ ] **Q4 — Apollo contract:** What format/schema does Apollo Studio actually ingest?
- [ ] **Q5 — First build scope:** Indications in scope; literature anchors on hand; 100k = patients or DOT-rows; target size?
- [ ] **Q6 — Claude.ai review:** Top 2–3 frustrations from the prior build to design away?

---

## Session Log

Newest first. One entry per working session: what we did, what we decided, where to resume.

### 2026-06-03 — Project kickoff
- Read the Claude.ai handoff doc; established shared understanding of architecture, dual-cohort model, lessons, and validation philosophy.
- Created this roadmap/tracker as the cross-session system of record.
- Raised Open Questions Q1–Q6 and architecture decisions D1–D5; logged my leans.
- **Resume here:** Spencer answers Q1–Q6 (priority: Q1 assets, Q2 structure, Q4 Apollo contract, Q5 first-build scope). Then close Phase 0.

---

## Related

- [[Apollo Studio]] — GTM/sales project this feeds
- [[Q2 2026 OKRs]] — Apollo Studio POC is an OKR line
- [[Key Decisions]] — promote settled D-items here
- [[Gotchas]] — clinical-modeling traps (NA-≠-failure, clot-on-untreated, etc.) land here as they bite
