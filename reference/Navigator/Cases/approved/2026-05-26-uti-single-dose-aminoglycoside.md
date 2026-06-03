---
date: 2026-05-26
description: "UTI case — pan-resistant Klebsiella uncomplicated cystitis requiring single-dose amikacin in CKD stage 3b"
disease_state: "UTI"
difficulty: hard
author: "Spencer"
status: approved
case_number: "UTI-07"
challenge_types: [uncomplicated-cystitis, pan-resistance, renal-dosing, single-dose-aminoglycoside]
tags:
  - sanity-test
  - case
  - uti
source: google-doc
---

# UTI Case 7: Single-dose aminoglycoside

**Difficulty:** hard
**Author:** Spencer

## Prompt

SS is a 67-year-old male with a past medical history significant for hypertension, type 2 diabetes mellitus, and stage 3b chronic kidney disease (baseline SCr 1.8 mg/dL, CrCl ~28 mL/min) who was admitted 18 days ago with perforated appendicitis. He underwent laparoscopic appendectomy with peritoneal washout and completed a 12-day course of piperacillin-tazobactam for complicated intra-abdominal infection. His post-operative course was prolonged but improving, and he is currently recovering on the surgical stepdown unit without a urinary catheter in place.

On the morning of post-operative day 18, the patient reports new-onset dysuria and urinary frequency over the past 24 hours. He denies fever, chills, nausea, vomiting, or flank pain. He has no costovertebral angle tenderness on exam. Vitals are stable: T 37.1°C, HR 78, BP 132/80, RR 16, SpO2 97% on room air. A urinalysis is obtained and urine culture is sent.

Ht: 5'9"   Wt: 83 kg   BMI: 27.1   Baseline SCr: 1.8 mg/dL   Allergies: NKDA

UA with microscopy (voided specimen, no catheter):

| Test | Result |
|------|--------|
| Color | Yellow, cloudy |
| Specific gravity | 1.021 |
| pH | 6.0 |
| Leukocyte esterase | 3+ |
| Nitrites | Positive |
| WBC | 50 – 100 /hpf |
| RBC | 5 – 10 /hpf |
| Bacteria | Many |
| Epithelial cells | Rare |
| Protein | Trace |
| Glucose | 1+ |
| Ketones | Negative |

## Culture Results

Urine culture: Klebsiella pneumoniae >100,000 CFU/mL

| Antibiotic | Result |
|------------|--------|
| Ampicillin | R |
| Ampicillin-sulbactam | R |
| Piperacillin-tazobactam | R |
| Ceftriaxone | R |
| Cefepime | R |
| Ceftazidime | R |
| Ciprofloxacin | R |
| Levofloxacin | R |
| TMP/SMX | R |
| Nitrofurantoin | R |
| Ertapenem | S |
| Meropenem | S |
| Gentamicin | I |
| Amikacin | S |
| Fosfomycin | Not reported |

## Labs

| Test | Result | Reference Range |
|------|--------|----------------|
| WBC | 9.1 k/µL | 4.5 – 11.0 k/µL |
| Hemoglobin | 11.2 g/dL | 13.5 – 17.5 g/dL |
| Platelets | 388 k/µL | 150 – 400 k/µL |
| Sodium | 138 mEq/L | 136 – 145 mEq/L |
| Potassium | 5.6 mEq/L | 3.5 – 5.1 mEq/L |
| CO₂ (bicarb) | 21 mEq/L | 22 – 29 mEq/L |
| BUN | 38 mg/dL | 7 – 20 mg/dL |
| Creatinine | 1.8 mg/dL | 0.7 – 1.3 mg/dL |
| eGFR | 28 mL/min/1.73m² | > 60 |
| Glucose | 162 mg/dL | 70 – 100 mg/dL |
| Lactate | 1.2 mmol/L | < 2.0 mmol/L |
| Procalcitonin | 0.21 ng/mL | < 0.25 ng/mL |

## Expected Output

- **Presentation:** Acute uncomplicated cystitis
- **Antibiotic Initiation** *(if applicable):*
  - Amikacin 15 mg/kg x1 (2400 mg)
  - Identify that single-dose aminoglycosides are not associated with nephrotoxicity
  - Identify Amikacin is restricted to Infectious Diseases
- **Treatment Optimization** *(if applicable):* N/A

## Related

- [[brain/Case Style Guide]]
