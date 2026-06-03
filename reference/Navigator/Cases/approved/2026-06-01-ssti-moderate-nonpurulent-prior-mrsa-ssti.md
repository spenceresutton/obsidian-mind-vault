---
date: 2026-06-01
description: "SSTI case — nonpurulent lower extremity cellulitis with MRSA SSTI history within the prior year; prior infection is an established risk factor requiring empiric anti-MRSA coverage"
disease_state: "SSTI"
difficulty: medium
author: Spencer
status: approved
case_number: "SSTI-04"
challenge_types: [MRSA-risk-prior-SSTI, nonpurulent-SSTI, empiric-MRSA-coverage]
tags:
  - sanity-test
  - case
  - ssti
source: generated
---

# SSTI Case 4: Nonpurulent Cellulitis with Prior MRSA SSTI History

**Difficulty:** medium
**Author:** Spencer

## Prompt

SS is a 55-year-old male with a past medical history significant for hypertension and a prior skin infection who presents to the emergency department with 5 days of worsening redness, warmth, and swelling of the left lower leg. He denies any purulent drainage at the site. He had a similar infection approximately 8 months ago that was treated as an outpatient; wound culture at that time grew MRSA and he was prescribed trimethoprim-sulfamethoxazole, which resolved the infection.

On arrival, vitals are: T 38.1°C, HR 96, BP 134/82, RR 16, SpO2 97% on room air. The left lower extremity shows erythema from the ankle to mid-calf with advancing borders marked at triage. The skin is warm, tender, and edematous. No fluctuance, no drainage, no purulence. No bullae, no crepitus. He takes lisinopril and hydrochlorothiazide.

**Ht:** 5'9"   **Wt:** 86 kg   **BMI:** 28.4   **Baseline SCr:** 1.1 mg/dL   **Allergies:** NKDA

## Labs

### CBC

| Test | Result | Reference Range |
|------|--------|----------------|
| WBC | 14.2 k/µL | 4.5 – 11.0 k/µL |
| Neutrophils (abs.) | 11.4 k/µL | 1.8 – 7.7 k/µL |
| Bands | 10% | < 10% |
| Lymphocytes (abs.) | 1.6 k/µL | 1.0 – 4.8 k/µL |
| Monocytes (abs.) | 0.7 k/µL | 0.2 – 1.0 k/µL |
| RBC | 4.8 M/µL | 4.5 – 5.9 M/µL |
| Hemoglobin | 13.6 g/dL | 13.5 – 17.5 g/dL |
| Hematocrit | 41.2% | 41 – 53% |
| MCV | 86 fL | 80 – 100 fL |
| MCH | 28.3 pg | 27 – 33 pg |
| MCHC | 33.0 g/dL | 32 – 36 g/dL |
| RDW | 13.4% | 11.5 – 14.5% |
| Platelets | 296 k/µL | 150 – 400 k/µL |
| MPV | 9.6 fL | 7.5 – 10.5 fL |

### CMP

| Test | Result | Reference Range |
|------|--------|----------------|
| **Electrolytes** | | |
| Sodium | 137 mEq/L | 136 – 145 mEq/L |
| Potassium | 4.2 mEq/L | 3.5 – 5.1 mEq/L |
| Chloride | 100 mEq/L | 98 – 106 mEq/L |
| CO₂ (bicarb) | 24 mEq/L | 22 – 29 mEq/L |
| BUN | 16 mg/dL | 7 – 20 mg/dL |
| Creatinine | 1.1 mg/dL | 0.7 – 1.3 mg/dL |
| eGFR | > 60 mL/min/1.73m² | > 60 |
| Glucose | 106 mg/dL | 70 – 100 mg/dL |
| **Liver function** | | |
| Total protein | 7.0 g/dL | 6.3 – 8.2 g/dL |
| Albumin | 3.8 g/dL | 3.5 – 5.0 g/dL |
| Total bilirubin | 0.5 mg/dL | 0.2 – 1.2 mg/dL |
| AST | 26 U/L | 10 – 40 U/L |
| ALT | 30 U/L | 7 – 56 U/L |
| Alkaline phosphatase | 72 U/L | 44 – 147 U/L |
| **Minerals** | | |
| Calcium (total) | 9.0 mg/dL | 8.5 – 10.5 mg/dL |

### Sepsis Markers

| Test | Result | Reference Range |
|------|--------|----------------|
| Lactate | 1.6 mmol/L | < 2.0 mmol/L |
| Procalcitonin | 0.58 ng/mL | < 0.25 ng/mL |
| CRP | 76 mg/L | < 10 mg/L |

## Expected Output

- **Presentation:** Nonpurulent SSTI with systemic signs and MRSA risk factor (documented MRSA SSTI within the past 12 months) — empiric anti-MRSA coverage indicated
- **Antibiotic Initiation** *(if applicable):* Vancomycin IV. History of MRSA SSTI within the prior year is an established MRSA risk factor; empiric anti-MRSA coverage is appropriate even in the absence of purulence.
- **Treatment Optimization** *(if applicable):* If wound cultures confirm susceptibility to a narrower oral agent, step down when IV-to-PO criteria are met. If MRSA is confirmed, oral step-down options include TMP-SMX DS tablets BID (confirm susceptibility) or doxycycline 100 mg BID. Total course 5–10 days.

**INCORRECT:**
- Cefazolin alone — lacks MRSA coverage
- TMP-SMX or doxycycline — lack sufficient strep coverage. Despite the MRSA risk factor, *Streptococcus* is the leading cause of nonpurulent SSTI and empiric therapy must cover it.

## Related

- [[brain/Case Style Guide]]
- [[reference/Navigator/Cases/guidelines/README]]
