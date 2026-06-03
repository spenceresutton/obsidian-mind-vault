---
date: 2026-06-01
description: "SSTI case — moderate nonpurulent cellulitis with documented Type 1 penicillin anaphylaxis; cefazolin safe despite anaphylaxis history; vancomycin fallback; clindamycin PO for step-down"
disease_state: "SSTI"
difficulty: medium
author: Spencer
status: pending
case_number: "SSTI-02"
challenge_types: [beta-lactam-allergy, nonpurulent-SSTI, IV-therapy, oral-step-down]
tags:
  - sanity-test
  - case
  - ssti
source: generated
---

# SSTI Case 2: Nonpurulent Cellulitis with Beta-Lactam Allergy

**Difficulty:** medium
**Author:** Spencer

## Prompt

SS is a 63-year-old female with a past medical history significant for type 2 diabetes mellitus, hypertension, and chronic venous insufficiency who presents to the emergency department with 4 days of worsening redness, warmth, and swelling of the right lower leg. She reports the area has been expanding despite leg elevation at home. She denies fever but notes increasing fatigue over the past 24 hours. She has no prior MRSA infections, no recent hospitalization, and no penetrating trauma to the extremity.

On arrival, vitals are: T 38.3°C, HR 106, BP 118/72, RR 18, SpO2 97% on room air. The right lower extremity shows diffuse erythema from the ankle to mid-calf with advancing borders marked by triage nursing. The skin is warm, tender, and edematous. No fluctuance, no drainage, no purulence. No bullae, no crepitus. Her allergy history is reviewed prior to antibiotic selection.

She takes metformin, lisinopril, and compression stockings. Her last HbA1c was 7.6%.

**Ht:** 5'5"   **Wt:** 79 kg   **BMI:** 29.4   **Baseline SCr:** 0.9 mg/dL   **Allergies:** Penicillin (anaphylaxis — throat swelling, hypotension; documented age 45, no prior allergy testing or desensitization)

## Labs

### CBC

| Test | Result | Reference Range |
|------|--------|----------------|
| WBC | 13.8 k/µL | 4.5 – 11.0 k/µL |
| Neutrophils (abs.) | 11.2 k/µL | 1.8 – 7.7 k/µL |
| Bands | 8% | < 10% |
| Lymphocytes (abs.) | 1.4 k/µL | 1.0 – 4.8 k/µL |
| Monocytes (abs.) | 0.6 k/µL | 0.2 – 1.0 k/µL |
| RBC | 4.2 M/µL | 4.0 – 5.2 M/µL |
| Hemoglobin | 11.8 g/dL | 12.0 – 16.0 g/dL |
| Hematocrit | 35.4% | 36 – 46% |
| MCV | 88 fL | 80 – 100 fL |
| MCH | 28.1 pg | 27 – 33 pg |
| MCHC | 33.4 g/dL | 32 – 36 g/dL |
| RDW | 13.6% | 11.5 – 14.5% |
| Platelets | 318 k/µL | 150 – 400 k/µL |
| MPV | 9.8 fL | 7.5 – 10.5 fL |

### CMP

| Test | Result | Reference Range |
|------|--------|----------------|
| **Electrolytes** | | |
| Sodium | 136 mEq/L | 136 – 145 mEq/L |
| Potassium | 4.0 mEq/L | 3.5 – 5.1 mEq/L |
| Chloride | 101 mEq/L | 98 – 106 mEq/L |
| CO₂ (bicarb) | 23 mEq/L | 22 – 29 mEq/L |
| BUN | 18 mg/dL | 7 – 20 mg/dL |
| Creatinine | 0.9 mg/dL | 0.7 – 1.3 mg/dL |
| eGFR | > 60 mL/min/1.73m² | > 60 |
| Glucose | 152 mg/dL | 70 – 100 mg/dL |
| **Liver function** | | |
| Total protein | 6.8 g/dL | 6.3 – 8.2 g/dL |
| Albumin | 3.6 g/dL | 3.5 – 5.0 g/dL |
| Total bilirubin | 0.5 mg/dL | 0.2 – 1.2 mg/dL |
| AST | 24 U/L | 10 – 40 U/L |
| ALT | 28 U/L | 7 – 56 U/L |
| Alkaline phosphatase | 76 U/L | 44 – 147 U/L |
| **Minerals** | | |
| Calcium (total) | 8.8 mg/dL | 8.5 – 10.5 mg/dL |

### Sepsis Markers

| Test | Result | Reference Range |
|------|--------|----------------|
| Lactate | 1.8 mmol/L | < 2.0 mmol/L |
| Procalcitonin | 0.62 ng/mL | < 0.25 ng/mL |
| CRP | 88 mg/L | < 10 mg/L |

## Expected Output

- **Presentation:** Nonpurulent moderate SSTI with systemic signs and documented IgE-mediated penicillin anaphylaxis
- **Antibiotic Initiation** *(if applicable):* Cefazolin 2g IV q8h. Cefazolin can be safely used in documented Type 1 (IgE-mediated) penicillin hypersensitivity. Other beta-lactams must be avoided. Vancomycin may be utilized if there is concern for a Type 2–4 hypersensitivity reaction or preference to avoid all beta-lactams.
- **Treatment Optimization** *(if applicable):* Step down to clindamycin 450 mg PO q8h when clinically indicated.

## Related

- [[brain/Case Style Guide]]
- [[reference/Navigator/Cases/guidelines/README]]
