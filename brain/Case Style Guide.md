---
date: 2026-05-26
description: "Style guide for Navigator sanity test case creation — structure conventions, difficulty calibration, challenge archetypes, anti-patterns, and voice markers derived from 18 imported cases"
tags:
  - brain
  - navigator
  - case-management
---

# Case Style Guide

Calibration source for AI-generated Navigator sanity test cases. Based on analysis of 16 Spencer-authored approved cases: 8 UTI (UTI-01 through UTI-08) and 8 CAP (CAP-03 through CAP-10).

**Note on CAP-01 and CAP-02:** These cases exist in `reference/Navigator/Cases/external/` and were authored by Radha. They are excluded from style calibration but their case numbers are reserved. Do not use CAP-01 or CAP-02 as generation targets.

## Overview

These cases test the Navigator clinical decision support tool's ability to recommend appropriate antibiotic therapy. They span two disease states (UTI and CAP) and three difficulty tiers. The taxonomy below reflects what separates a correct from an incorrect Navigator output — not what separates a good from a great clinician.

**Guidelines directory status:** Fully populated. See `reference/Navigator/Cases/guidelines/README.md` for the complete index. All major UTI guidelines ingested; CAP guidelines ingested. Hierarchy for resolving guideline conflicts: see the Guideline Hierarchy section below.

---

## Structure Conventions

### Universal Sections (every case)

| Section | Notes |
|---------|-------|
| YAML frontmatter | `date`, `description`, `disease_state`, `difficulty`, `author`, `status`, `case_number`, `challenge_types`, `tags`, `source` |
| `# Case Title` | Format: `[Disease] Case [N]: [Description]` |
| `**Difficulty:**` and `**Author:**` | Always appear immediately after the H1 heading, as bare bold lines |
| `## Prompt` | Narrative clinical vignette. Always present. See voice conventions below. |
| `## Expected Output` | Three sub-bullets: Presentation, Antibiotic Initiation, Treatment Optimization |
| `## Related` | Always includes `[[brain/Case Style Guide]]` as a minimum link |

### Optional Sections (situational)

| Section | When Present |
|---------|-------------|
| `## Culture Results` | Present when cultures are a key part of the challenge (known pathogen, resistance pattern, AmpC, KPC). Absent in straightforward uncomplicated cystitis (UTI-04) and simple ASB in pregnancy (UTI-05) |
| `## Imaging` | Present when imaging confirms or rules out a diagnosis (pyelonephritis CT, CXR for CAP, CT/AP for prostatitis). All 10 CAP cases have CXR. UTI cases include CT when complications are possible. |
| `## Labs` | All UTI cases with systemic illness have full Labs (CBC + CMP + Sepsis Markers). All 10 CAP cases have full Labs. Simple outpatient cases (UTI-04, UTI-05) have no labs section. UTI-07 and UTI-08 use a condensed single-table format instead of three-section format. |
| `## UA with microscopy` | Present in UTI cases when UA is clinically relevant. Absent in UTI-01 (UA data is embedded in the Prompt paragraph instead). The UA table heading notes collection method: "clean-catch midstream", "straight catheter specimen", "voided specimen, no catheter", "catheter specimen, admission". |

### Canonical Section Order

Every case follows this sequence:

1. YAML frontmatter
2. `# Case Title` with Difficulty and Author lines
3. `## Prompt`
4. `## Imaging` (when present)
5. `## Culture Results` (when present)
6. `## Labs` (CBC with Differential → CMP → Sepsis Markers)
7. `## UA with microscopy` (UTI cases, when present)
8. `## Expected Output`
9. `## Related`

Culture Results always precedes Labs. This ordering reflects the clinical read sequence — imaging and microbiology data before the lab panel.

---

### Physical Exam (ICU and Severe Cases)

ICU and severe inpatient cases include a brief physical exam description in the Prompt, following the vitals line. Three components at minimum:

1. **General appearance** — acuity, distress level (e.g., "acutely ill and in significant respiratory distress")
2. **Relevant system exam** — disease-specific findings (e.g., lung exam for CAP: breath sounds, percussion, crackles; abdominal for prostatitis, etc.)
3. **Mental status** — cooperative, altered, fatigued, etc.

Physical exam is not optional for ICU admissions. Simple outpatient cases (UTI-04, UTI-05) do not require it.

**Exam detail calibration by severity:** For mild and uncomplicated cases, limit physical exam to 2–3 key positive findings that directly support the diagnosis. Negative findings belong only when they rule out a meaningful clinical escalation — "no crepitus" excludes necrotizing fasciitis; "no lymphangitic streaking" matters for an extremity abscess. The test: does this negative change what you would do? If not, cut it. A list of negatives that don't change management signals miscalibration.

**ICU severity narrative convention:** When a patient arrives on vasopressors, state the agent name, dose, and MAP threshold that triggered initiation. Example: "MAP remained below 60 mmHg and norepinephrine was initiated at 0.08 mcg/kg/min." Vitals on ICU arrival should reflect the vasopressor-dependent state (include MAP explicitly). The ED course leading to ICU transfer — fluids given, hemodynamic response, O2 progression — belongs in the Prompt narrative before the ICU arrival vitals line.

### Home Medications

Include the patient's home medication list in the Prompt when medications provide clinical context — COPD inhalers, PPIs, diabetes agents, anticoagulants, immunosuppressants. Place the medication list after the physical exam and before the stats footer line. Medications are contextually relevant when they: (1) inform the clinical picture, (2) create potential drug interactions, or (3) reflect the severity or chronicity of relevant comorbidities.


### Case Richness and Alignment

Cases should feel like real patients, not constructed puzzles. The clinical picture — PMH, medications, labs, HPI — should cohere around the patient, not around the teaching point.

**PMH and medications:** Include chronic diseases and home medications that fit the patient's age and disease context. Most inpatient patients in the 60–75 range carry some chronic disease burden. The goal is authenticity, not complexity. Do not introduce comorbidities or medications to create drug interactions or diagnostic traps — Spencer makes those decisions. Instead, select conditions and medications that would naturally accompany the primary illness. A Parkinson's patient with aspiration pneumonia gets Parkinson's medications; a COPD patient on the inpatient pneumonia service gets their COPD inhalers. The medications listed should be the ones the patient actually takes, present because they belong.

**Labs:** The lab panel should reflect two things simultaneously: the patient's acute illness and their chronic disease state. A patient in septic shock should have labs that look like septic shock. A patient with known CKD should have a creatinine consistent with their baseline. Abnormalities should be purposeful — they follow from the clinical picture, not from a desire to create a teaching point. Do not manufacture lab findings.

**HPI:** The history of present illness should feel like it was written from a real admission. The timeline, symptom progression, and clinical course that led to the current presentation should be consistent with the acute disease state. The HPI sets the clinical context; it is not an opportunity to embed clues.

**Pertinent negatives scope:** Only list negative history items directly relevant to the challenge's risk stratification or clinical decision. "No prior MRSA infections, no recent hospitalizations" belongs in an MRSA risk assessment case — those negatives change the answer. "No diabetes" in the same case does not qualify and reads as filler. If a condition is not a risk factor, a contraindication, or a differential driver for the specific challenge, leave it out.

**Treatment Optimization:** Include this section only when the case provides sufficient clinical information to support a second decision step — known pathogen, returning cultures, clinical improvement milestones, or a de-escalation question. For cases centered on empiric antibiotic initiation, Treatment Optimization does not apply and should be left blank or marked N/A. Do not generate speculative optimization for cases that are presenting an initiation question.

### Lab Panel Conventions

**Default rule: full panels for all inpatient cases.** CBC with full differential (including bands), complete CMP (electrolytes, renal, hepatic, calcium including LFTs), and Sepsis Markers. Do not abbreviate for inpatient or ICU cases regardless of whether every value drives a decision — the full panel reflects authentic clinical context. The determination is based on disposition, not infection severity: a patient admitted for a primary non-infectious diagnosis who has an incidental SSTI still receives the full panel. The panel reflects the admission, not the index infection alone.

**Full 3-panel format (CBC + CMP + Sepsis Markers):** Used in all inpatient and systemic illness cases. Present in UTI-01, 02, 03, CAP-01 through CAP-10.

**Condensed single-table format:** Reserved for ED discharge and outpatient presentations only. UTI-07 and UTI-08 use this format — selected rows from CBC, CMP, and sepsis markers in one table.

**CAP-01 exception:** Labs presented as an inline text sentence in the Prompt section rather than a table. This is the only case that uses inline lab format.

**Sepsis Markers panel** (when present): Always three rows — Lactate, Procalcitonin, CRP.

**PSA** appears in UTI-08 (prostatitis) — disease-specific addition to the condensed panel.

**eGFR** should be explicitly stated in the CMP when renal impairment is present or when renal dose adjustment is a challenge being tested.

**CMP subgroup headers** — Inpatient full-panel CMP tables use bold row separators as visual section dividers within the table: `| **Electrolytes** | | |` followed by sodium through glucose; `| **Liver function** | | |` followed by total protein through alkaline phosphatase; `| **Minerals** | | |` followed by calcium. Second and third columns are empty for header rows. This is the standard format for all inpatient CMP tables (established in CAP-12, CAP-13).

**Labs timestamp** — For ICU cases, add an italic note after the final table to clarify when values were drawn: `*Resulted: ICU admission day*`. This distinguishes admission labs from follow-up panels and contextualizes values that reflect the acute presentation.

### Culture Result Formats

**UTI cases with positive cultures:** Sensitivity table format (Antibiotic | Result columns). Example from UTI-06/07: full susceptibility table listing R/S/I for each agent.

**UTI cases with pending cultures:** Free text. Example: "Urine culture: Pending — no growth at time of case presentation. Gram stain: gram-negative rods."

**Pending culture format (all disease states):** Plain text, one line per result, no bold, no bullets. Example: "Wound culture — right thigh abscess: Sent — no growth at 24 hours; pending final result." Apply this format for any culture result that has not yet finalized, regardless of disease state.

**CAP cases:** Cultures consistently listed in structured text blocks covering: Blood cultures, Sputum culture, Respiratory viral panel, Urine antigen (Streptococcus pneumoniae and Legionella pneumophila). MRSA PCR result bolded when present: `**MRSA PCR: Negative**` or `**MRSA PCR (-)**`.

### UA Table Format

Standard two-column format (Test | Result) without reference ranges. Rows in fixed order:
Color, Specific gravity, pH, Leukocyte esterase, Nitrites, WBC (/hpf), RBC (/hpf), Bacteria, Epithelial cells, Protein, Glucose, Ketones.

### Imaging Format

Numbered radiology report style. Each finding is its own numbered line. Final line is always an "Impression:" statement.

When multiple imaging studies are present (e.g., CXR + CT), use subsection headers — `### Chest X-Ray — PA and Lateral` and `### CT Chest with Contrast` — each with its own numbered list and Impression line.

When CT reveals a finding requiring drainage or specialist involvement (abscess, empyema, loculation), the CT Impression line adds: "Clinical correlation and ID consultation recommended." This signals escalation within the radiology report and makes the case feel clinically authentic.

---

## Difficulty Calibration

### Easy

The clinician needs to recognize the presentation, match it to a first-line guideline recommendation, and execute. No traps, no competing signals, no resistance patterns.

| What makes it easy | Case examples |
|--------------------|--------------|
| Uncomplicated presentation with no comorbidities | UTI-04: healthy 26F, NKDA, textbook cystitis; just pick nitrofurantoin |
| Exception case that appears hard but has a clear rule | UTI-05: no UTI symptoms, but pregnancy = treat ASB; the rule is unambiguous |
| No allergy, no renal impairment, no resistance, hemodynamically stable | CAP-01: healthy 66F, NKDA, CrCl ~54, non-severe CAP; standard ceftriaxone + azithromycin |

**UTI-04 specifics:** Young, healthy, no PMH, NKDA, no renal impairment. Single answer: nitrofurantoin 100 mg BID. The case explicitly prohibits fosfomycin and fluoroquinolones.

**UTI-05 specifics:** Pregnant patient with no UTI symptoms but positive UA. Trap is treating it as a true UTI requiring clinical judgment — the rule is clear: ASB in pregnancy always gets treated.

**CAP-01 specifics:** Non-severe inpatient CAP with no risk factors. CURB-65 = 2, no MRSA/PsA history, no recent antibiotics. Standard ceftriaxone + azithromycin. Wrong answers are explicitly named: "Piperacillin-tazobactam (excessive spectrum); Vancomycin or anti-MRSA coverage (not indicated)."

### Medium

The clinician needs to interpret a competing signal, correctly classify an allergy, or navigate a gray-zone diagnosis. The right answer exists but requires reasoning through a complication.

| What makes it medium | Case examples |
|----------------------|--------------|
| ASB with confounding symptoms that mimic UTI | UTI-02: DKA + BPH creates urgency symptoms; UA is hot but the patient doesn't have a true UTI |
| Allergy that looks like a contraindication but isn't | UTI-03: Augmentin (diarrhea) — GI intolerance, not a beta-lactam allergy |
| Known comorbidities requiring severity assessment | CAP-03: COPD + T2DM, non-severe presentation; must classify correctly and resist over-treating |
| Recent oral abx exposure that raises spectrum concern | CAP-04: Augmentin 80 days prior — doesn't change standard regimen, still ceftriaxone + azithromycin |
| Severe beta-lactam allergy requiring monobactam | CAP-02: documented penicillin anaphylaxis + Pseudomonas risk; aztreonam + azithromycin |

**UTI-02 specifics:** Patient has 3+ leukocyte esterase and >100 WBC/hpf but the "difficulty urinating" is from BPH + DKA, not infection. Clinician must decide whether symptoms are UTI vs. BPH + acute illness. Navigator surfaces the ambiguity and watches off antibiotics if the decision is not-a-UTI.

**UTI-03 specifics:** Augmentin listed as allergy. Expected output explicitly states: "Augmentin allergy is an intolerance and does not preclude use of Beta-Lactams." Treatment Optimization notes that Augmentin 875-125 BID is a valid PO step-down option — the allergy is safe to use.

**UTI-08 specifics (medium):** Acute bacterial prostatitis from Citrobacter koseri with urinary retention. Medium because it requires recognizing: (1) Citrobacter koseri does NOT have inducible AmpC (unlike C. freundii); (2) ceftriaxone continuation is appropriate; (3) oral conversion to TMP/SMX for 2-6 weeks with prostate penetration in mind; (4) urinary retention requires catheterization (source control).

### Hard

Multiple simultaneous challenges. Resistance patterns that require non-standard agents. Diagnostic traps where the obvious answer is wrong. System-level decisions (ID consult, formulary restrictions, de-escalation paths).

| What makes it hard | Case examples |
|--------------------|--------------|
| AmpC induction risk requiring cefepime over ceftriaxone | UTI-01: E. cloacae susceptible to ceftriaxone on sensitivity panel, but ceftriaxone should not be used |
| Septic shock severity requiring immediate aggressive management | UTI-01: vasopressors, leukopenia (WBC 2.1), lactate 5.2, platelets 68 |
| ASB + pan-resistant organism creating pressure to treat | UTI-06: KPC-producing Klebsiella, elderly with AMS; Navigator should not offer treatment even under pressure |
| Pan-resistant cystitis requiring single-dose aminoglycoside in CKD | UTI-07: all oral and IV options resistant except carbapenems and amikacin; CKD stage 3b requires dose calculation |
| Recent IV abx triggering MRSA + Pseudomonas dual risk | CAP-05: IV Unasyn 80 days prior elevates both risks; vancomycin + cefepime + azithromycin |
| MRSA PCR negative overriding IV abx risk factor | CAP-06: same IV abx history, but negative MRSA PCR; drop vancomycin, keep cefepime |
| Known pathogen overriding risk stratification | CAP-07, CAP-08: risk factors present but S. pneumoniae on gram stain supersedes — target the bug, not the risk score |
| Pseudomonas colonization history without confirmed current infection | CAP-09: prior Pseudomonas on sputum 9 months ago; cover empirically with cefepime, de-escalate if cultures negative |
| Aspiration pneumonia without anaerobic coverage requirement | CAP-10: aspiration event with prior Pseudomonas colonization; no anaerobic coverage, no atypical coverage |

---

## Challenge Archetype Taxonomy

| Archetype | Clinical Concept Tested | Example Cases | Wrong Answer Trap |
|-----------|------------------------|---------------|-------------------|
| **ASB vs. true UTI** | UA findings alone don't diagnose a UTI; symptoms are required | UTI-02, UTI-06 | Treating a positive UA in an asymptomatic patient with confounding symptoms (BPH, AMS) |
| **ASB in pregnancy** | Exception to the no-treatment rule for ASB; pregnancy mandates treatment | UTI-05 | Not treating, or using an inappropriate agent (quinolones contraindicated) |
| **AmpC induction risk** | E. cloacae, C. freundii, Serratia, and others with inducible AmpC — ceftriaxone appears susceptible but will select for resistance; use cefepime | UTI-01 | De-escalating to ceftriaxone based on susceptibility report; using cefazolin or ceftriaxone for definitive therapy |
| **KPC / pan-resistant organism** | CRO with KPC requires targeted agents (ceftazidime-avibactam, meropenem-vaborbactam); ASB with KPC still does not require treatment | UTI-06 | Reflexively treating because the organism is resistant, or using an inactive agent |
| **Single-dose aminoglycoside** | Amikacin 15 mg/kg x1 achieves high urinary concentrations without nephrotoxicity; ID-restricted agent | UTI-07 | Using a nephrotoxic multi-day aminoglycoside course, or defaulting to carbapenem when single-dose amikacin is safer |
| **Beta-lactam allergy vs. intolerance** | GI side effects (diarrhea, nausea) are not allergies; true IgE-mediated allergy (anaphylaxis, urticaria) precludes class | UTI-03, CAP-02 | Avoiding all beta-lactams because of a documented GI intolerance, or conversely using a penicillin in documented anaphylaxis |
| **Renal dose adjustment** | CKD alters drug dosing; SJN protocol governs specific thresholds. Key SJN rules: cefepime adjusts at CrCl **<60** (not <30 like most beta-lactams); fluconazole adjusts at CrCl <50; levofloxacin 250mg for uncomplicated UTI requires no adjustment even at CrCl <20; nitrofurantoin contraindicated at CrCl <30; pharmacist adjusts without contacting provider; SCr must be within 72h | UTI-07, CAP-10 | Prescribing nitrofurantoin in CKD stage 3b+ (CrCl <30); failing to adjust cefepime in CrCl 30–60 (the SJN test zone); adjusting levofloxacin 250mg for an uncomplicated UTI when it's explicitly exempt |
| **IV-to-PO conversion** | SJN IV-to-Enteral Policy governs eligibility. Clinical stability criteria required (afebrile ≥24h, SBP >90, no vasopressors, HR <100, ≥24h IV therapy); prostatitis requires prostatic-penetrating agents; ceftriaxone→cefpodoxime is explicitly excluded if urinary catheter remains in place; ciprofloxacin cannot be given via feeding tube (use levofloxacin); sepsis <7 days remains IV | UTI-08, CAP-01 | Continuing IV therapy after clinical stabilization; converting to an oral agent without prostatic penetration for prostatitis; switching ceftriaxone to cefpodoxime when catheter is still present; administering ciprofloxacin via NG/OG tube |
| **Extended infusion beta-lactam** | Pip/tazo at SJN is always extended infusion by default — pharmacist converts all orders. Standard: 3.375g q8h over 4 hours with a 4.5g loading dose over 30 min first. Sepsis, ICU, obesity (>120kg/BMI>40), CrCl >120, and MIC >16 escalate to 4.5g q8h over 4 hours. CrCl <20 and HD/PD: q12h dosing. PK rationale: time-dependent killing, %T>MIC — not peak concentration | None currently (high-value case target) | Ordering pip/tazo as a 30-minute infusion; omitting the loading dose; using 3.375g q8h for a septic patient instead of 4.5g; reducing dose (rather than extending interval) for CrCl <20 |
| **Source control** | Foley catheter replacement in CAUTI; urinary retention drainage in prostatitis | UTI-01, UTI-08 | Treating infection without addressing the source (retained catheter, obstructed bladder) |
| **Septic shock severity recognition** | Lactate >4, vasopressor requirement, leukopenia, elevated inflammatory markers all define shock; treatment must be immediate and aggressive | UTI-01 | Under-treating based on a temperature of 36.1°C (hypothermia in sepsis), or focusing on the respiratory culture without treating the primary source |
| **MRSA risk stratification (CAP)** | Recent IV antibiotics (within 90 days) raises MRSA risk; a negative MRSA nasal PCR is sufficient to remove vancomycin | CAP-05, CAP-06 | Adding vancomycin based on risk factor alone when MRSA PCR is negative; or conversely not adding vancomycin when PCR is pending and risk factors are present |
| **Pseudomonas risk stratification (CAP)** | COPD + recent hospitalization + IV antibiotics raises Pseudomonas risk; colonization history from a prior admission also qualifies | CAP-02, CAP-05, CAP-06, CAP-09 | Using standard ceftriaxone + azithromycin when Pseudomonas coverage is indicated; or not de-escalating when cultures return negative |
| **Known pathogen overrides risk score** | When a pathogen is identified (Strep pneumo on sputum gram stain), target it directly even if empiric risk factors would suggest broader coverage | CAP-07, CAP-08 | Continuing MRSA/PsA empiric therapy after a susceptible pathogen is identified |
| **De-escalation discipline** | Duration and spectrum should narrow as data returns; there is a specific duration difference (5 vs. 7 days) based on whether Pseudomonas is confirmed | CAP-01, CAP-06, CAP-07, CAP-08, CAP-09 | Maintaining broad spectrum despite negative cultures, or not shortening duration when the pathogen doesn't require extended therapy |
| **Aspiration pneumonia scope** | Aspiration pneumonia requires neither anaerobic nor atypical coverage unless CT shows abscess or loculation. When abscess is present: add metronidazole (anaerobic coverage warranted); atypical coverage (azithromycin) is still not indicated — abscess is a polymicrobial gram-negative/anaerobic process, not an atypical infection. Duration without abscess: 5 days (non-Pseudomonas) or 7 days (Pseudomonas confirmed). Duration with lung abscess: 3–6 weeks, driven by clinical improvement and repeat CT. | CAP-10, CAP-12, CAP-13 | Adding metronidazole for aspiration pneumonia without abscess or loculation on CT; adding azithromycin for aspiration pneumonia regardless of abscess status; generating azithromycin reflexively because the broader label is "severe CAP" |
| **Citrobacter species differentiation** | Citrobacter koseri does not harbor inducible AmpC (unlike C. freundii); ceftriaxone is safe as definitive therapy | UTI-08 | Treating Citrobacter koseri like C. freundii and avoiding cephalosporins |
| **Respiratory colonization vs. infection** | Prior Pseudomonas sputum culture from a different admission is colonization history, not active infection — but it informs empiric coverage | CAP-09, CAP-10 | Either ignoring the colonization history entirely, or treating it as confirmed active Pseudomonas infection without further culture data |

---

## Anti-Patterns

These are explicit prohibitions and traps called out in Expected Output sections. Treat these as hard rules.

### Diagnostic Language

- **"Foul smelling urine should not be mentioned. It is language that is thrown around a lot but no data has any association with smell and infection. It would be more professional to glaze over it."** (UTI-01) — Do not reference odor in UTI diagnosis or workup.

- **"Avoid being too specific in additional work-up/alternative sources of altered mental status"** (UTI-06) — When AMS is the presenting complaint and the workup returns ASB, Navigator should not presume to enumerate alternative diagnoses.

### Allergy Scope at SJN

- **Cephalosporin anaphylaxis = withhold all beta-lactams** — at SJN, cephalosporin anaphylaxis precludes cephalosporins, penicillins, AND carbapenems. Do not assume penicillin-class is safe based on cross-reactivity literature alone. Aztreonam (monobactam) is the exception — safe because of its distinct monocyclic ring structure.

- **Aztreonam has no gram-positive activity** — when aztreonam is used as the beta-lactam substitute, vancomycin is required for gram-positive coverage (Strep pneumo, MRSA) regardless of MRSA PCR result. A negative MRSA PCR removes MRSA concern but does not eliminate the gram-positive gap. Do not omit vancomycin when aztreonam is the only beta-lactam on board.

- **Type 1 (IgE-mediated) penicillin anaphylaxis does not preclude cefazolin** — cefazolin can be safely used in documented IgE-mediated penicillin anaphylaxis. Other beta-lactams (penicillins, cephalosporins beyond cefazolin, carbapenems) must be avoided without thorough allergy assessment. When stating beta-lactam avoidance, specify "other beta-lactams" rather than condemning the full class. Vancomycin is appropriate when there is concern for Type 2–4 hypersensitivity or when the patient or provider prefers to avoid all beta-lactams entirely. (Source: SSTI-02)

### Pseudomonas Risk at SJN

- **COPD alone is not a Pseudomonas risk factor at SJN** — Pseudomonas empiric coverage is triggered by IV antibiotic use AND hospitalization within the prior 90 days, per SJN inpatient pneumonia guidelines. Structural lung disease (COPD, bronchiectasis) is a national guideline criterion but does not independently qualify at SJN. Do not apply national guideline Pseudomonas risk criteria directly to SJN cases.

### Overtreatment Traps

- **"Realistically the tool shouldn't even offer an 'if you would treat'. If the user challenges with 'we have made the decision to treat, then provide treatment options'"** (UTI-06) — In clear ASB cases, Navigator should not pre-emptively offer treatment options as a hedge. Only provide them if the user pushes back.

- **"Should NOT recommend fluoroquinolones due to…"** (CAP-09, CAP-10) — Fluoroquinolones are not first-line for CAP when beta-lactams are tolerated. Both CAP-09 and CAP-10 include: **"Do not recommend fluoroquinolones without intolerance to beta-lactams."**


- **"INCORRECT choices: Piperacillin-tazobactam (excessive spectrum, no MRSA/PsA risk factors); Vancomycin or anti-MRSA coverage (not indicated)"** (CAP-01) — For standard non-severe CAP with no risk factors, broad-spectrum coverage is actively wrong.

### Agent Selection Traps

- **"Do not recommend fosfomycin or fluoroquinolones"** (UTI-04) — Uncomplicated cystitis in a young woman with no risk factors: nitrofurantoin is the strong preference. Fosfomycin is single-dose and appropriate in some contexts, but not here.

- **"Culture and imaging are unnecessary given this presentation"** (UTI-04) — Ordering cultures and imaging for uncomplicated cystitis is over-workup.

- AmpC induction trap (UTI-01): E. cloacae reports ceftriaxone as Susceptible. The correct antibiotic is still cefepime. A Navigator that de-escalates to ceftriaxone based on the susceptibility report fails this case.

- Nitrofurantoin + CKD trap (UTI-07): Patient has CrCl ~28 mL/min. Nitrofurantoin is resistant and also contraindicated at this level of renal function. Prescribing it is a double failure.

- Prostatitis tissue penetration trap (UTI-08): Oral conversion requires an agent that penetrates prostatic tissue. Nitrofurantoin and cephalosporins don't. TMP/SMX is the correct oral step-down for 2-6 weeks.

- **IV clindamycin is not appropriate for nonpurulent SSTI** — outside of necrotizing fasciitis, clindamycin is a PO-only agent for SSTIs. For IV therapy in nonpurulent SSTI, use cefazolin (preferred when Type 1 penicillin allergy is present) or vancomycin (Type 2–4 allergy or all-beta-lactam avoidance). IV clindamycin in nonpurulent SSTI without necrotizing fasciitis is a wrong answer. (Source: SSTI-02)

- **Nonpurulent SSTI is predominantly streptococcal** — empiric therapy must cover *Streptococcus*. Anti-MRSA agents with unreliable strep activity (TMP-SMX, doxycycline) are insufficient as empiric monotherapy for nonpurulent SSTI even when MRSA risk factors are present. Vancomycin is correct because it covers both strep and MRSA; cefazolin covers strep but not MRSA. TMP-SMX/doxycycline become appropriate only as oral step-down once MRSA is culture-confirmed. (Source: SSTI-04)

### Allergy Traps

- Augmentin GI intolerance is not a beta-lactam allergy (UTI-03). Avoiding all cephalosporins and penicillins is the wrong move. Augmentin itself is a valid PO step-down option.

- Penicillin anaphylaxis blocks penicillins and structurally related agents. Aztreonam is safe — it is a monobactam and does not share the bicyclic thiazolidine ring driving IgE cross-reactivity (CAP-02).

### Scope of Analysis

- **"Presentation is not concerning for pneumonia given no acute pulmonary process identified in CXR"** (UTI-01) — When respiratory culture grows Stenotrophomonas alongside a negative CXR, Navigator should not treat the respiratory culture. Source attribution matters.

- **"Comment that atypical coverage discontinuation may be warranted"** (CAP-07, CAP-08, CAP-09) — When a beta-only pathogen (Strep pneumo) is identified, atypical coverage (azithromycin) should be explicitly questioned rather than continued by default.

- **"Comment that anaerobic coverage is not indicated for aspiration pneumonia"** (CAP-10, CAP-12) — Modern guidelines do not support routine anaerobic coverage for aspiration pneumonia without abscess or loculation. When CT confirms abscess, metronidazole is appropriate — this is the exception, not the rule. CAP-13 is the exemplar for the abscess variant; CAP-12 is the exemplar for aspiration without abscess.

---

## Voice & Style

### Patient Identifier Convention

Two observed conventions:

- **Initials only, no periods:** `SS` — used in most Spencer-authored cases (UTI-01 through UTI-08 except UTI-05, CAP-03 through CAP-10)
- **Initials with periods:** `M.R.`, `D.T.` — used in Radha-authored cases (CAP-01: M.R.; CAP-02: D.T.)

No full names appear. Stick to two-letter initials. The period style vs. no-period style reflects author preference; either is acceptable. Use the patient's initials consistently throughout the Prompt.

### Prompt Opening Structure

Standard opening: `[Initials] is a [age]-year-old [sex] with [PMH description] who [presents/was admitted/is brought] [to/from/by] [setting] with [chief complaint].`

PMH phrasing: "with a past medical history significant for X, Y, and Z" — use this exact construction for patients with comorbidities. For patients without: "with no significant past medical history."

**Always include in Prompt:**
- Age, sex
- Relevant PMH (or explicit "no significant PMH")
- Chief complaint / presenting illness
- Vitals (T, HR, BP, RR, SpO2 with FiO2 or NC L)
- Allergies

**Include situationally:**
- Ht, Wt, BMI, Baseline SCr — present in most cases; absent in CAP-01 and CAP-02 (labs section carries SCr) and UTI-05 (simple presentation, no renal relevance)
- Weight-based dosing context appears as a footer line: `Ht: 5'9"   Wt: 83 kg   BMI: 27.1   Baseline SCr: 1.8 mg/dL   Allergies: NKDA`
- Gynecologic history (LMP, pregnancy test, contraception) when female and UTI

### Vitals Presentation

Two styles in use:

**Inline paragraph (UTI cases, most Spencer-authored CAP cases):** "On arrival, vitals are: T 38.6°C, HR 102, BP 148/84, RR 18, SpO2 95% on 2L NC."

**Labeled line (Radha-authored cases — CAP-01, CAP-02):** `**Vitals:** Temp 38.9°C | HR 94 | BP 118/74 | RR 22 | SpO2 97% on 2L NC`

The pipe-delimited labeled format is cleaner for readability. Either is acceptable — stay consistent within a case.

### Allergy Notation

Two author styles:

- **Spencer-authored cases:** Brief notation in the Ht/Wt footer — `Allergies: Cephalexin (anaphylaxis)` or `Allergies: NKDA`. Even when allergy is the core challenge, Spencer-authored cases keep the footer brief and add a narrative cue in the Prompt body: "His/Her allergy history is reviewed prior to antibiotic selection." The clinical reasoning lives in Expected Output, not in the Prompt allergy description. CAP-12 and CAP-13 are the exemplars for allergy-challenge cases.
- **Radha-authored cases (CAP-01, CAP-02):** Full detail as a bold labeled line in the Prompt body: `**Allergies:** Penicillin — anaphylaxis (throat swelling, hypotension) documented in medical record from age 52. No prior desensitization or allergy testing.`

When generating cases, use the Spencer-authored format — brief footer plus narrative cue, reasoning in Expected Output. The prior rule "when the allergy is the core challenge, give full detail inline" applies only to Radha-authored cases and does not apply to generated cases.

**Allergy location:** Allergy belongs in the footer only. Do not repeat allergy information in the Prompt narrative — it is redundant and reads as filler.

### Expected Output Tone and Structure

Three labeled sub-bullets, always in this order:
1. `**Presentation:**` — identification of the clinical syndrome
2. `**Antibiotic Initiation** *(if applicable):*` — empiric or targeted regimen
3. `**Treatment Optimization** *(if applicable):*` — step-down, de-escalation, duration

**Presentation line:** State the clinical syndrome concisely. Only add qualifiers that are treatment- or disease-modifying (e.g., "with ileus," "first recurrence," "with Pseudomonas colonization"). Do not include supporting lab values, threshold explanations, or diagnostic reasoning — those belong in the Antibiotic Initiation or INCORRECT sections. Do not embed allergy class statements, therapy route indications, or antibiotic exclusions in the Presentation line — "IV therapy indicated" and "beta-lactam class must be avoided" belong in Antibiotic Initiation, not Presentation. Examples: "Initial Nonsevere CDI", "Fulminant CDI with ileus", "Non-severe aspiration pneumonia with Pseudomonas colonization history," "Nonpurulent moderate SSTI with systemic signs and documented IgE-mediated penicillin anaphylaxis."

**Surgery consult language:** When a surgical consult is indicated, state "Surgery consult recommended" — do not elaborate on timing, indications, or specific surgical interventions (colectomy, diverting ileostomy, etc.). Those decisions belong to the surgical team and are outside Navigator's scope.

**Treatment duration language:** A single line is sufficient — "Treatment duration may be extended based on clinical status." Do not specify triggers, timeframes, or decision criteria for extension.

**IV-to-PO criteria:** When a case involves IV-to-PO conversion, state that the patient is clinically stable and meets conversion criteria. Do not enumerate the specific criteria parenthetically — they live in the SJN IV-to-Enteral Policy. The Expected Output needs the conclusion, not the checklist.

**Antibiotic discontinuation in CDI:** Use "Discontinue all systemic antibiotics if clinically feasible, otherwise use the shortest possible duration." Do not name a specific agent unless there is a CDI-specific reason to call it out (e.g., a high-risk agent like a fluoroquinolone where stopping is the highest-yield intervention).

**Bullet tone:** Imperative or assertive. Not "consider X" — rather "Recommend X" or just state the drug. The tool should give recommendations, not suggestions. **Exception:** Use "Consider X" when antibiotic initiation is genuinely optional or conditional — when the case leaves the decision open (e.g., antibiotics may be withheld after successful I&D). Reserve imperative tone for clear-cut decisions.

**Bold emphasis** is used for three purposes:
1. **Strong preference** — `Nitrofurantoin 100 mg BID **(Strong preference)**` (UTI-04)
2. **Explicit prohibitions** — `**Do not recommend fluoroquinolones without intolerance to beta-lactams**`
3. **Key recognition targets** — `**Navigator should identify that the clinician must decide whether symptoms represent UTI or BPH + acute illness**`

**N/A sections:** When Antibiotic Initiation or Treatment Optimization does not apply, write it inline on the label line — `**Antibiotic Initiation** *(if applicable):* N/A` — never omit the section or leave the line blank.

**Return precautions:** When antibiotics are withheld or the initiation decision is left open, include explicit return precautions as part of the Expected Output. This is not optional — it is the clinical safety net for conditional antibiotic decisions. Standard phrasing: "Patient should return immediately if fever, expanding erythema, or worsening pain develop."

**Conditional outputs** are signaled explicitly:
- `*(if applicable):*` on the section header
- `(assuming decision is that it is not a UTI)` / `(Assuming decision is that it is a UTI)` — inline conditional in UTI-02
- `When Navigator is provided information that the Strep pneumoniae is penicillin susceptible, it should offer:` — triggered treatment optimization in CAP-07/08
- `N/A` — explicit when the section doesn't apply

**Expected Output specificity:** Drug + dose + route + duration, always. Examples:
- `Nitrofurantoin 100 mg BID` (no route specified for oral outpatient — acceptable)
- `Ceftriaxone 2g IV q24h x7 days`
- `Amikacin 15 mg/kg x1 (2400 mg)` — with calculated dose for weight-based agents
- `TMP/SMX 2 DS tablets BID (or 1.5 DS tablets TID) for 2-6 weeks` — with dosing flexibility noted where clinically accepted

**Incorrect choices:** Include an INCORRECT section only when a specific element in the Prompt would predictably lead a clinician to the wrong answer. Two qualifying triggers:

1. **Red herring** — a Prompt detail was deliberately included to tempt the wrong answer (e.g., an MRSA risk factor in a PCR-negative case). The Prompt element is the anchor.
2. **Counter-intuitive exclusion** — the correct answer contradicts a reflexive standard practice (e.g., ceftriaxone appears susceptible on the sensitivity panel, but cefepime is correct). The Prompt element is still the anchor.

Disqualifiers: the wrong answer requires ignoring the Prompt entirely; no traceable archetype in the Challenge Taxonomy or named anti-pattern in this guide; restating the correct answer in negative form when nothing in the case implied the wrong one.

Cap: ≤2 entries per case. Hard cases may carry up to 3 if each maps to a distinct archetype. Easy cases: none — no traps by design.

**INCORRECT rationale must name the clinical gap, not the care setting.** State why the agent fails pharmacologically or microbiologically — spectrum gap, resistance, tissue penetration — not that it belongs to a different setting. "Appropriate for outpatient" is not a reason an agent is wrong. (Source: SSTI-04: TMP-SMX/doxycycline fail empiric nonpurulent SSTI for lacking strep coverage, not for being oral agents.)

### Difficulty and Author Lines

These appear immediately after the H1 heading as bare bold lines, not as a header section:
```
**Difficulty:** hard
**Author:** Spencer
```

CAP-08 uses "Spencer Sutton" instead of "Spencer" — either is acceptable.

**Author is always Spencer.** Both the frontmatter `author:` field and the `**Author:**` body line are always "Spencer" (or "Spencer Sutton"). Never set `author: Claude` — all cases are Spencer-authored regardless of who generated the draft.

---

## Guideline Hierarchy

When guidelines conflict or overlap, apply this priority order:

### Rule 1: Newer supersedes older
A 2025 IDSA recommendation takes precedence over a 2010 IDSA recommendation on the same question. Example: the 2025 IDSA cUTI guideline's definition of uncomplicated infection (symptom-based, not host-factor-based) supersedes the 2010 uncomplicated UTI guideline's scope, which treated DM and urological abnormalities as complicating factors.

### Rule 2: More specific supersedes less specific
Guidance scoped to a narrower clinical context overrides general guidance on that point. Examples:
- **CAUTI duration:** The 2010 IDSA CAUTI guideline specifies treatment duration and catheter management for catheterized patients — use this over the 2025 IDSA cUTI duration recommendations for catheter-specific scenarios.
- **CAUTI source control:** The CAUTI guideline's catheter replacement rule (≥2 weeks in place → replace before treating) is the operative guidance; the general cUTI framework does not address this.
- **General duration:** Once source control is achieved (catheter removed, obstruction relieved), the 2025 IDSA cUTI framework governs duration — more recent and directly addresses the post-source-control scenario.
- **ASB in catheterized patients:** The 2010 CAUTI guideline's no-treatment recommendation is more specific than the general 2019 IDSA ASB guidance for catheter populations.

### Rule 3: SJN local protocol governs case correctness
Cases are calibrated to SJN clinical practice. Where national guidelines and SJN diverge, SJN governs the expected output. National guidelines explain the reasoning; SJN determines the right answer. Document divergences explicitly in the expected output when they arise.

### Rule 4: Gray areas are Spencer's domain
Where newer vs. specific guidance creates genuine ambiguity — or where national guidelines leave the decision to clinical judgment — Spencer resolves it. During case generation, flag these as review points rather than asserting a definitive answer.

### Applied Hierarchy Table

| Scenario | Governing Guideline | Reason |
|----------|-------------------|--------|
| Uncomplicated vs. complicated UTI classification | 2025 IDSA cUTI | Newer; explicitly updates 2010 framework |
| Empiric antibiotic selection for cUTI | 2025 IDSA cUTI → SJN local | National framework; SJN calibrates specific agents |
| Duration for non-bacteremic cUTI, catheter removed | 2025 IDSA cUTI (7 days) | Newer, post-source-control context |
| Duration for cUTI in catheterized patient | 2010 IDSA CAUTI (7d prompt, 10-14d delayed) | More specific to catheter context |
| Catheter replacement before treating | 2010 IDSA CAUTI | Catheter-specific guidance; not addressed in cUTI guideline |
| ASB in catheterized patient | 2019 IDSA ASB + 2010 IDSA CAUTI (consistent) | Both recommend against treatment |
| Prostatitis duration | Kulkarni 2026 CID (≥2 weeks ABP; 6 weeks CBP) | Newer, more specific to prostatitis |
| FQ vs. beta-lactam for cUTI step-down | 2025 IDSA cUTI CQ2 | Most recent, directly addresses IV-to-oral |
| Nitrofurantoin for cUTI | All guidelines (consistent: not appropriate) | Universal; no hierarchy needed |
| Pip/tazo dosing and infusion duration | SJN Extended Infusion Policy (03/2026) | SJN-specific: pharmacist-driven default to extended infusion; 3.375g q8h over 4h standard; 4.5g q8h for sepsis/ICU/obesity/ARC; loading dose required |
| IV-to-PO auto-conversion eligibility | SJN IV-to-Enteral Policy (pending P&T) | SJN-specific: formal inclusion/exclusion criteria; ceftriaxone→cefpodoxime excluded with catheter in place; ciprofloxacin not via feeding tube; sepsis <7 days remains IV |
| Renal dose adjustment thresholds | SJN Renal Dose Adjustment Policy (02/2026) | SJN-specific: cefepime adjusts at CrCl <60; pharmacist authority without provider contact; SCr must be current within 72h |

---

### SJN Local Protocol Key Divergences

The highest-value test points for SJN-calibrated cases — where SJN practice differs from what a national-guideline reader would expect.

| SJN Rule | What a Reader Would Expect | SJN Protocol |
|----------|---------------------------|--------------|
| Cefepime renal threshold | Adjust at CrCl <30 (like most beta-lactams) | **Adjust at CrCl <60** — CrCl 30–60 is the SJN test zone |
| Levofloxacin 250mg UTI at CrCl <20 | Dose-reduce like all other levofloxacin regimens | **No adjustment** for uncomplicated UTI — explicit exception to q48h rule |
| Fluconazole renal threshold | Adjust at CrCl <30 (like most antibiotics) | **Adjust at CrCl <50** — 50% dose reduction; higher threshold than expected |
| Amox-clav 875mg at CrCl <30 | Dose-reduce the 875mg formulation | **Formulation is contraindicated** — switch to 500mg q12h |
| Pip/tazo infusion duration | 30-minute IVPB (standard) | **4-hour extended infusion by default** (3.375g q8h); loading dose 4.5g x1 over 30 min first |
| Pip/tazo in sepsis or ICU | Standard extended infusion dose | **Escalate to 4.5g q8h** extended infusion — not 3.375g |
| Ceftriaxone → cefpodoxime step-down | Routine oral conversion when clinically stable | **Excluded if urinary catheter is present** — additional SJN-specific restriction |
| Ciprofloxacin via feeding tube | Acceptable oral/enteral delivery | **Prohibited** — use levofloxacin (with 2h EN hold before/after) |
| Pharmacist calling provider for dose reduction | Required before any dose change | **Not required** — pharmacist authority to adjust renally-cleared drugs independently |
| TMP/SMX at CrCl 15–30 | May be avoided or discontinued | **50% dose** — reduced but not eliminated; 25% at CrCl <15 |

---

## Cross-Disease Transfer Notes

These patterns apply regardless of disease state and will carry forward to SSTI, bacteremia, endocarditis, and other future categories.

### Disease-Agnostic Challenge Archetypes

| Archetype | Transfers to |
|-----------|-------------|
| **ASB vs. true infection** | Bacteremia workup: positive blood culture vs. contamination; asymptomatic Staph aureus in urine |
| **AmpC induction risk** | Any gram-negative bacteremia: E. cloacae, Serratia, Morganella, Proteus vulgaris all have inducible AmpC |
| **Allergy vs. intolerance** | Any disease state where beta-lactams are first-line |
| **Renal dose adjustment** | Any renally-cleared antibiotic in any setting |
| **IV-to-PO conversion** | Any inpatient course; tissue penetration considerations vary by site (e.g., bone vs. prostate vs. lung) |
| **Source control** | SSTI: incision and drainage; bacteremia: remove line; endocarditis: valve considerations |
| **Septic shock severity** | Any bacteremic presentation; same SOFA/vasopressor/lactate criteria |
| **Known pathogen overrides risk score** | Any infection where culture or gram stain results before empiric therapy decision |
| **De-escalation discipline** | Universal: duration and spectrum narrow as data returns |

### Universal Structural Conventions

- YAML frontmatter with `challenge_types[]` array — always define before writing
- Three-section Expected Output structure (Presentation / Antibiotic Initiation / Treatment Optimization) is the fixed template
- Sensitivity tables in two-column format for positive culture results
- Numbered radiology-report format for all imaging
- Labs section: CBC + CMP + Sepsis Markers for systemic illness; condensed single-table for ambulatory or uncomplicated presentations
- `[[brain/Case Style Guide]]` always appears in `## Related`

### Voice/Style Patterns That Hold Across Disease States

- Patient initials only (no full names)
- Ht/Wt/BMI/Baseline SCr footer line for cases with renal or weight-based dosing relevance
- Vitals inline in narrative OR pipe-delimited labeled line — pick one and stay consistent within the case
- Bold for prohibitions, strong preferences, and key recognition targets
- Conditional outputs signaled with explicit `*(if applicable):*` or inline `(assuming decision is X)`
- Specific calculated doses for weight-based agents
- Explicit `INCORRECT:` callouts for high-stakes wrong answers

### What Does Not Transfer Directly

- **Disease-specific labs:** PSA for prostatitis, BNP for heart failure, LFTs for biliary source. Add relevant disease-specific markers to the condensed lab table.
- **UA with microscopy:** UTI-specific; analogous structures would be wound culture or joint fluid in SSTI/septic arthritis
- **Urine antigen panel for CAP:** Strep pneumo + Legionella — CAP-specific; no equivalent for UTI cases
- **MRSA nasal PCR:** Primarily relevant for pulmonary SSTI and CAP; less validated for UTI source

---

## Related

- [[brain/Memories]]
- [[brain/Key Decisions]]
- [[reference/Navigator/Cases/README]]
- [[reference/Navigator/Cases/guidelines/README]]
- [[reference/Navigator/Cases/guidelines/local/SJN-Renal-Dose-Adjustment-Policy]]
- [[reference/Navigator/Cases/guidelines/local/SJN-IV-to-Enteral-Policy]]
- [[reference/Navigator/Cases/guidelines/local/SJN-Extended-Infusion-Policy]]
