---
date: 2026-05-26
description: "CAP case — non-severe inpatient CAP with Pseudomonas risk factor and documented penicillin anaphylaxis"
disease_state: "CAP"
difficulty: medium
author: "Radha"
status: external
case_number: "CAP-02"
challenge_types: [non-severe-CAP, Pseudomonas-risk, severe-beta-lactam-allergy, de-escalation, aztreonam]
tags:
  - case
  - cap
  - external
source: google-doc
note: "Radha-authored case. Excluded from style calibration. Case number reserved for nomenclature continuity."
---

# CAP Case 2: Inpatient Non-Severe CAP with Pseudomonas Risk Factor and Severe Beta-Lactam Allergy

**Difficulty:** medium
**Author:** Radha

## Prompt

D.T. is a 68-year-old man with a history of COPD (GOLD Stage 2, FEV1 65%) and hypertension who presents to the ED with worsening shortness of breath, productive cough with sputum, and fever. He last used his COPD inhalers this morning. Six weeks ago he was hospitalized for 4 days for a COPD exacerbation and received IV methylprednisolone and IV piperacillin-tazobactam (full course) before discharge. He has had no other hospitalization or antibiotic exposures in the past year. He has no prior history of Pseudomonas or MRSA infections.

**Allergies:** Penicillin — anaphylaxis (throat swelling, hypotension) documented in medical record from age 52. No prior desensitization or allergy testing.

**Weight/Height:** 82 kg, 5'10" (BMI 26)

**Vitals:** Temp 38.6°C | HR 102 | BP 138/86 | RR 24 | SpO2 91% on RA, improves to 96% on 2L NC

**Exam:** Alert, mild respiratory distress. Crackles and decreased breath sounds at right base. No accessory muscle use. JVD absent.

**Labs:** WBC 15.2 (82% neutrophils), BMP: Na 138, K 4.1, Cl 102, CO2 23, BUN 17, SCr 0.9 (baseline), Glu 104. CrCl ~85 mL/min. Procalcitonin 1.8 ng/mL.

**CXR:** Right lower lobe consolidation. No multilobar involvement. No pleural effusion.

**EKG:** Normal sinus rhythm. QTc 432 ms.

The patient is being admitted to the general medicine floor. Blood cultures x2 drawn pre-antibiotic at triage. The admitting team asks pharmacy for antibiotic recommendations given his allergy and recent hospitalization history.

## Expected Output

- **Presentation:** Community-acquired pneumonia (CAP), non-severe, inpatient general ward admission.
  - Key risk factors: (1) COPD — high-risk comorbidity for drug-resistant organisms; (2) Hospitalization with IV antibiotics 6 weeks ago (within past 90 days) — validated Pseudomonas aeruginosa risk factor per 2019 IDSA/ATS guideline Q11; (3) Penicillin anaphylaxis (IgE-mediated, documented) — eliminates standard beta-lactam options without formal allergy evaluation
  - Severity: CURB-65 = 2 (RR 24, age 68); PSI Class III. Does NOT meet severe CAP criteria
  - Clinical flags: Right lower lobe consolidation, SpO2 91% on RA requiring supplemental O2, productive purulent sputum. No ICU-level deterioration at this time
- **Antibiotic Initiation** *(if applicable):*
  - Recommended (per 2019 IDSA/ATS Q11 — Pseudomonas risk factors present; allergy constraint applied): Aztreonam 2 g IV q8h PLUS Azithromycin 500 mg IV/PO daily
  - Teaching point: Aztreonam is SAFE in penicillin anaphylaxis — it is a monobactam, not a penicillin or cephalosporin, and does not share the bicyclic thiazolidine ring driving IgE-mediated cross-reactivity
  - Alternative if QTc borderline or aztreonam unavailable: Ciprofloxacin 400 mg IV q8h PLUS Azithromycin 500 mg IV daily (requires QTc monitoring; baseline QTc 432 ms is acceptable to proceed)
  - INCORRECT: Piperacillin-tazobactam (penicillin-based, contraindicated with anaphylaxis); Cefepime or meropenem (low cross-reactivity ~1–2% but unacceptable without allergy evaluation in documented anaphylaxis); Levofloxacin monotherapy (inadequate Pseudomonas coverage); Standard ceftriaxone + azithromycin (insufficient anti-pseudomonal coverage given validated risk factor)
- **Treatment Optimization** *(if applicable):*
  - De-escalation (critical per Q11): If sputum and blood cultures return NEGATIVE for Pseudomonas, discontinue aztreonam and step down to standard CAP therapy

## Related

- [[brain/Case Style Guide]]
