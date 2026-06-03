---
date: 2026-06-01
description: "SSTI case — nonpurulent cellulitis discovered incidentally during admission for NSTEMI, no systemic signs, oral antibiotics appropriate"
disease_state: "SSTI"
difficulty: easy
author: Spencer
status: pending
case_number: "SSTI-01"
challenge_types: [incidental-finding, severity-classification, oral-therapy, antibiotic-stewardship]
tags:
  - sanity-test
  - case
  - ssti
source: generated
---

# SSTI Case 1: Incidental Nonpurulent Cellulitis During Cardiac Admission

**Difficulty:** easy
**Author:** Spencer

## Prompt

SS is a 58-year-old male with a past medical history significant for hypertension, hyperlipidemia, and former tobacco use (quit 12 years ago) who presents to the emergency department with 4 hours of substernal chest pressure radiating to the left arm. Initial ECG shows new ST depression in leads V4–V6. Troponin-I returns elevated at 0.44 ng/mL (reference <0.04 ng/mL). He is admitted to the cardiology service for acute coronary syndrome workup and management.

During admission nursing skin assessment, a 3 × 2 cm area of erythema, mild warmth, and tenderness to palpation is noted incidentally on the left shin. There is no purulence, no drainage, no fluctuance, no crepitus, and no bullae. The erythema is blanchable and the borders are well-demarcated. The patient reports first noticing mild redness there approximately 2 days ago. He denies trauma, insect bite, or any wound at the site. He reports no fevers at home, no chills, and no systemic symptoms related to the skin finding.

On arrival, vitals are: T 36.9°C, HR 76, BP 146/90, RR 14, SpO2 96% on room air. He takes amlodipine, atorvastatin, and lisinopril. He has no known drug allergies.

**Ht:** 5'11"   **Wt:** 88 kg   **BMI:** 27.3   **Baseline SCr:** 1.0 mg/dL   **Allergies:** NKDA

## Labs

### CBC

| Test | Result | Reference Range |
|------|--------|----------------|
| WBC | 10.4 k/µL | 4.5 – 11.0 k/µL |
| Neutrophils (abs.) | 7.4 k/µL | 1.8 – 7.7 k/µL |
| Bands | 3% | < 10% |
| Lymphocytes (abs.) | 2.1 k/µL | 1.0 – 4.8 k/µL |
| Monocytes (abs.) | 0.6 k/µL | 0.2 – 1.0 k/µL |
| RBC | 4.7 M/µL | 4.5 – 5.9 M/µL |
| Hemoglobin | 14.2 g/dL | 13.5 – 17.5 g/dL |
| Hematocrit | 42.1% | 41 – 53% |
| MCV | 89 fL | 80 – 100 fL |
| MCH | 30.2 pg | 27 – 33 pg |
| MCHC | 33.7 g/dL | 32 – 36 g/dL |
| RDW | 13.2% | 11.5 – 14.5% |
| Platelets | 238 k/µL | 150 – 400 k/µL |
| MPV | 9.8 fL | 7.5 – 10.5 fL |

### CMP

| Test | Result | Reference Range |
|------|--------|----------------|
| Sodium | 138 mEq/L | 136 – 145 mEq/L |
| Potassium | 4.2 mEq/L | 3.5 – 5.1 mEq/L |
| Chloride | 101 mEq/L | 98 – 106 mEq/L |
| CO₂ (bicarb) | 24 mEq/L | 22 – 29 mEq/L |
| BUN | 18 mg/dL | 7 – 20 mg/dL |
| Creatinine | 1.0 mg/dL | 0.7 – 1.3 mg/dL |
| eGFR | > 60 mL/min/1.73m² | > 60 |
| Glucose | 98 mg/dL | 70 – 100 mg/dL |
| Total protein | 7.0 g/dL | 6.3 – 8.2 g/dL |
| Albumin | 3.8 g/dL | 3.5 – 5.0 g/dL |
| Total bilirubin | 0.5 mg/dL | 0.2 – 1.2 mg/dL |
| AST | 28 U/L | 10 – 40 U/L |
| ALT | 22 U/L | 7 – 56 U/L |
| Alkaline phosphatase | 72 U/L | 44 – 147 U/L |
| Calcium (total) | 9.1 mg/dL | 8.5 – 10.5 mg/dL |

### Sepsis Markers

| Test | Result | Reference Range |
|------|--------|----------------|
| Lactate | 1.1 mmol/L | < 2.0 mmol/L |
| Procalcitonin | 0.08 ng/mL | < 0.25 ng/mL |
| CRP | 12 mg/L | < 10 mg/L |

## Expected Output

- **Presentation:** Nonpurulent SSTI without systemic signs
- **Antibiotic Initiation** *(if applicable):* Cephalexin 500 mg PO QID x5 days. No IV antibiotics required. No anti-MRSA coverage indicated — no purulence, no MRSA risk factors.
- **Treatment Optimization** *(if applicable):* Reassess at 48–72h; if erythema expands beyond marked borders or systemic signs develop, reassess severity and consider escalation. Cardiac workup should not be interrupted or delayed for the SSTI. Antibiotics can be continued through hospitalization and completed as outpatient.

## Related

- [[brain/Case Style Guide]]
- [[reference/Navigator/Cases/guidelines/README]]
