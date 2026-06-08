---
date: 2026-06-01
description: "SSTI case — purulent SSTI (axillary abscess) s/p I&D on admission, now 48h later meeting IV-to-PO criteria with MRSA culture confirmed; select correct oral step-down agent"
disease_state: "SSTI"
difficulty: medium
author: Spencer
status: approved
case_number: "SSTI-06"
challenge_types: [purulent-SSTI, source-control, oral-step-down, MRSA-oral-agent-selection, IV-to-PO]
tags:
  - sanity-test
  - case
  - ssti
source: generated
---

# SSTI Case 6: Purulent SSTI — Oral Step-Down Post-Drainage

**Difficulty:** medium
**Author:** Spencer

## Prompt

SS is a 38-year-old female with no significant past medical history who was admitted 48 hours ago for a left axillary abscess. Incision and drainage was performed on the day of admission; approximately 8 mL of purulent material was expressed and the wound was packed. She was started on vancomycin IV at that time. Over the past 24 hours, she has been afebrile, pain is substantially improved, and she has been tolerating a regular diet without difficulty.

Current vitals: T 36.8°C, HR 72, BP 118/74, RR 14, SpO2 98% on room air. She denies nausea or vomiting and has no further systemic complaints.

Wound culture results from the drainage at the time of I&D have finalized.

**Ht:** 5'4"   **Wt:** 68 kg   **BMI:** 26.1   **Baseline SCr:** 0.7 mg/dL   **Allergies:** NKDA

## Culture Results

Wound culture — left axillary abscess drainage (collected day of admission): Staphylococcus aureus — methicillin-resistant (MRSA)

| Antibiotic | Result |
|---|---|
| Oxacillin | R |
| Cefazolin | R |
| TMP-SMX | S |
| Doxycycline | S |
| Clindamycin | I (D-zone test indeterminate) |
| Vancomycin | S (MIC 1 µg/mL) |
| Linezolid | S |

## Labs

### CBC

| Test | Result | Reference Range |
|------|--------|----------------|
| WBC | 8.4 k/µL | 4.5 – 11.0 k/µL |
| Neutrophils (abs.) | 5.8 k/µL | 1.8 – 7.7 k/µL |
| Bands | 2% | < 10% |
| Lymphocytes (abs.) | 1.8 k/µL | 1.0 – 4.8 k/µL |
| Monocytes (abs.) | 0.6 k/µL | 0.2 – 1.0 k/µL |
| RBC | 4.2 M/µL | 4.2 – 5.4 M/µL |
| Hemoglobin | 12.6 g/dL | 12.0 – 16.0 g/dL |
| Hematocrit | 37.8% | 37 – 47% |
| MCV | 90 fL | 80 – 100 fL |
| MCH | 30.0 pg | 27 – 33 pg |
| MCHC | 33.3 g/dL | 32 – 36 g/dL |
| RDW | 13.4% | 11.5 – 14.5% |
| Platelets | 286 k/µL | 150 – 400 k/µL |
| MPV | 9.4 fL | 7.5 – 10.5 fL |

### CMP

| Test | Result | Reference Range |
|------|--------|----------------|
| **Electrolytes** | | |
| Sodium | 137 mEq/L | 136 – 145 mEq/L |
| Potassium | 3.9 mEq/L | 3.5 – 5.1 mEq/L |
| Chloride | 100 mEq/L | 98 – 106 mEq/L |
| CO₂ (bicarb) | 25 mEq/L | 22 – 29 mEq/L |
| BUN | 10 mg/dL | 7 – 20 mg/dL |
| Creatinine | 0.7 mg/dL | 0.5 – 1.0 mg/dL |
| eGFR | > 60 mL/min/1.73m² | > 60 |
| Glucose | 88 mg/dL | 70 – 100 mg/dL |
| **Liver function** | | |
| Total protein | 6.9 g/dL | 6.3 – 8.2 g/dL |
| Albumin | 3.6 g/dL | 3.5 – 5.0 g/dL |
| Total bilirubin | 0.4 mg/dL | 0.2 – 1.2 mg/dL |
| AST | 22 U/L | 10 – 40 U/L |
| ALT | 16 U/L | 7 – 56 U/L |
| Alkaline phosphatase | 58 U/L | 44 – 147 U/L |
| **Minerals** | | |
| Calcium (total) | 9.0 mg/dL | 8.5 – 10.5 mg/dL |

### Sepsis Markers

| Test | Result | Reference Range |
|------|--------|----------------|
| Lactate | 1.2 mmol/L | < 2.0 mmol/L |
| Procalcitonin | 0.18 ng/mL | < 0.25 ng/mL |
| CRP | 18 mg/L | < 10 mg/L |

## Expected Output

- **Presentation:** Purulent SSTI (abscess) s/p I&D, clinically improving, MRSA confirmed on culture
- **Antibiotic Initiation** *(if applicable):* N/A
- **Treatment Optimization** *(if applicable):* Patient is clinically stable and meets IV-to-PO conversion criteria. Step down to TMP-SMX DS 1 tablet BID or doxycycline 100 mg PO BID x5 days. **Do not use clindamycin** — D-zone test is indeterminate, indicating inducible MLSB resistance; clindamycin failure risk is unacceptable when susceptible alternatives are available; unnecessary CDI risk. **Do not continue vancomycin IV** — patient fully meets IV-to-PO conversion criteria; continued IV therapy is not justified.

## Related

- [[brain/Case Style Guide]]
- [[reference/Navigator/Cases/guidelines/README]]
- [[reference/Navigator/Cases/guidelines/local/SJN-IV-to-Enteral-Policy]]
