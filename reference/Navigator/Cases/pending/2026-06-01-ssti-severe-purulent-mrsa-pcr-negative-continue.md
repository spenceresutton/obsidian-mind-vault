---
date: 2026-06-01
description: "SSTI case — severe purulent SSTI with systemic signs and negative MRSA nasal PCR; continue empiric vancomycin until wound cultures confirm; PCR de-escalation rule applies to pneumonia, not purulent SSTI"
disease_state: "SSTI"
difficulty: hard
author: Claude
status: pending
case_number: "SSTI-09"
challenge_types: [severe-purulent-SSTI, MRSA-PCR-negative, empiric-anti-MRSA-continuation, de-escalation-discipline]
tags:
  - sanity-test
  - case
  - ssti
source: generated
---

# SSTI Case 9: Severe Purulent SSTI — MRSA Nasal PCR Negative, Maintain Coverage

**Difficulty:** hard
**Author:** Claude

## Prompt

SS is a 52-year-old male with a past medical history significant for type 2 diabetes mellitus and obesity who presents to the emergency department with a 5-day history of a rapidly enlarging, painful lump on the right lower back and flank. He reports fevers at home over the past 2 days. He denies prior MRSA infections or recent hospitalizations.

On arrival, vitals are: T 38.9°C, HR 116, BP 102/64, RR 20, SpO2 96% on room air. Exam reveals a large fluctuant carbuncle spanning approximately 8 × 6 cm on the right lumbar region, with surrounding erythema extending an additional 4–5 cm from the abscess border. Moderate purulent drainage is present at the surface. No crepitus. No skin discoloration beyond the erythematous border.

Incision and drainage is performed with a large volume of thick, purulent material expressed and the wound packed. Blood cultures x2 sets are collected prior to the procedure. Per hospital protocol, a MRSA nasal PCR swab was obtained on arrival and the result is now available. Wound cultures from the I&D drainage are sent. The patient is admitted for IV antibiotic therapy. Vancomycin IV is initiated empirically.

**Ht:** 5'10"   **Wt:** 112 kg   **BMI:** 36.1   **Baseline SCr:** 1.2 mg/dL   **Allergies:** NKDA

## Culture Results

Blood cultures: 2 sets collected prior to I&D — no growth at 24 hours; pending final result

Wound culture — right lumbar carbuncle drainage: Sent — no growth at 24 hours; pending final result

MRSA Nasal PCR: Negative

## Labs

### CBC

| Test | Result | Reference Range |
|------|--------|----------------|
| WBC | 18.4 k/µL | 4.5 – 11.0 k/µL |
| Neutrophils (abs.) | 15.2 k/µL | 1.8 – 7.7 k/µL |
| Bands | 12% | < 10% |
| Lymphocytes (abs.) | 1.4 k/µL | 1.0 – 4.8 k/µL |
| Monocytes (abs.) | 0.8 k/µL | 0.2 – 1.0 k/µL |
| RBC | 4.6 M/µL | 4.5 – 5.9 M/µL |
| Hemoglobin | 13.2 g/dL | 13.5 – 17.5 g/dL |
| Hematocrit | 39.6% | 41 – 53% |
| MCV | 86 fL | 80 – 100 fL |
| MCH | 28.7 pg | 27 – 33 pg |
| MCHC | 33.3 g/dL | 32 – 36 g/dL |
| RDW | 13.4% | 11.5 – 14.5% |
| Platelets | 188 k/µL | 150 – 400 k/µL |
| MPV | 10.0 fL | 7.5 – 10.5 fL |

### CMP

| Test | Result | Reference Range |
|------|--------|----------------|
| **Electrolytes** | | |
| Sodium | 136 mEq/L | 136 – 145 mEq/L |
| Potassium | 4.4 mEq/L | 3.5 – 5.1 mEq/L |
| Chloride | 100 mEq/L | 98 – 106 mEq/L |
| CO₂ (bicarb) | 22 mEq/L | 22 – 29 mEq/L |
| BUN | 22 mg/dL | 7 – 20 mg/dL |
| Creatinine | 1.4 mg/dL | 0.7 – 1.3 mg/dL |
| eGFR | 56 mL/min/1.73m² | > 60 |
| Glucose | 188 mg/dL | 70 – 100 mg/dL |
| **Liver function** | | |
| Total protein | 6.8 g/dL | 6.3 – 8.2 g/dL |
| Albumin | 3.4 g/dL | 3.5 – 5.0 g/dL |
| Total bilirubin | 0.7 mg/dL | 0.2 – 1.2 mg/dL |
| AST | 32 U/L | 10 – 40 U/L |
| ALT | 36 U/L | 7 – 56 U/L |
| Alkaline phosphatase | 82 U/L | 44 – 147 U/L |
| **Minerals** | | |
| Calcium (total) | 8.6 mg/dL | 8.5 – 10.5 mg/dL |

### Sepsis Markers

| Test | Result | Reference Range |
|------|--------|----------------|
| Lactate | 2.4 mmol/L | < 2.0 mmol/L |
| Procalcitonin | 2.6 ng/mL | < 0.25 ng/mL |
| CRP | 124 mg/L | < 10 mg/L |

## Expected Output

- **Presentation:** Severe purulent SSTI with systemic signs; MRSA nasal PCR negative — continue empiric vancomycin until wound cultures confirm organism; negative nasal PCR does not govern anti-MRSA de-escalation in purulent SSTI
- **Antibiotic Initiation** *(if applicable):* Continue vancomycin IV (initiated in ED). Source control achieved with I&D. Note eGFR 56 — pharmacist to assess vancomycin dosing (at SJN, CrCl >60 threshold for cefepime dose adjustment does not apply here, but vancomycin requires AUC-based monitoring with this degree of renal function).
- **Treatment Optimization** *(if applicable):* **Do not discontinue vancomycin based on negative MRSA nasal PCR.** Await wound and blood culture results (48–72h). If cultures confirm MSSA, step down to nafcillin/oxacillin IV or cephalexin/dicloxacillin PO when IV-to-PO criteria are met. If MRSA confirmed, step down to TMP-SMX DS or doxycycline when eligible. This differs from the pneumonia context, where a negative MRSA nasal PCR is sufficient to remove empiric vancomycin.

**INCORRECT:**
- Discontinuing vancomycin based on negative MRSA nasal PCR — the nasal PCR de-escalation rule applies to HAP/VAP; it is not validated for purulent SSTI and MRSA is the most common cause of severe community-acquired abscesses regardless of nasal colonization
- Narrowing to cefazolin or cephalexin empirically — MRSA cannot be excluded without culture data; de-escalation requires organism confirmation, not PCR guidance

## Related

- [[brain/Case Style Guide]]
- [[reference/Navigator/Cases/guidelines/README]]
