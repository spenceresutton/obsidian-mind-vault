---
date: 2026-06-01
description: "CDI case — nonsevere CDI developing on day 5 of levofloxacin for pneumonia; stop vs continue the inciting agent; duration extension if antibiotics continue"
disease_state: "CDI"
difficulty: medium
author: "Spencer"
status: approved
case_number: "CDI-05"
challenge_types: [CDI-on-antibiotics, stop-vs-continue-inciting-agent, de-escalation, secondary-prophylaxis, duration-extension]
tags:
  - sanity-test
  - case
  - cdi
source: generated
---

# CDI Case 5: CDI on Active Antibiotics

**Difficulty:** medium
**Author:** Spencer

## Prompt

PH is a 63-year-old male with a past medical history significant for COPD, type 2 diabetes mellitus, and hypertension who was admitted 5 days ago for pneumonia and initiated on levofloxacin 750 mg IV daily for a planned 7-day course. He was improving — SpO₂ returned to baseline on 2L NC, fever resolved on day 3, and he transitioned to a regular diet on day 4. This morning he reports 5–6 loose stools and crampy lower abdominal pain. He is afebrile with T 37.4°C. The team sends CDI testing and the results are returned below. He takes albuterol MDI, tiotropium, metformin, lisinopril, and atorvastatin at home. He has no known drug allergies.

**Ht:** 5'9"   **Wt:** 86 kg   **BMI:** 28.4   **Baseline SCr:** 0.9 mg/dL   **Allergies:** NKDA

## Stool Studies

- *C. difficile* PCR (NAAT): **Positive**
- GDH (Glutamate Dehydrogenase) Antigen: **Positive**
- *C. difficile* Toxin A/B EIA: **Positive**

## Labs

### CBC

| Test | Result | Reference Range |
|------|--------|----------------|
| WBC | 12.2 k/µL | 4.5 – 11.0 k/µL |
| Neutrophils (abs.) | 8.4 k/µL | 1.8 – 7.7 k/µL |
| Bands | 5% | < 10% |
| Lymphocytes (abs.) | 2.2 k/µL | 1.0 – 4.8 k/µL |
| Monocytes (abs.) | 0.9 k/µL | 0.2 – 1.0 k/µL |
| RBC | 4.4 M/µL | 4.5 – 5.9 M/µL |
| Hemoglobin | 13.2 g/dL | 13.5 – 17.5 g/dL |
| Hematocrit | 39.8% | 41 – 53% |
| MCV | 90 fL | 80 – 100 fL |
| MCH | 30.0 pg | 27 – 33 pg |
| MCHC | 33.2 g/dL | 32 – 36 g/dL |
| RDW | 13.9% | 11.5 – 14.5% |
| Platelets | 268 k/µL | 150 – 400 k/µL |
| MPV | 9.6 fL | 7.5 – 10.5 fL |

### CMP

| Test | Result | Reference Range |
|------|--------|----------------|
| **Electrolytes** | | |
| Sodium | 137 mEq/L | 136 – 145 mEq/L |
| Potassium | 3.7 mEq/L | 3.5 – 5.1 mEq/L |
| Chloride | 101 mEq/L | 98 – 106 mEq/L |
| CO₂ (bicarb) | 24 mEq/L | 22 – 29 mEq/L |
| BUN | 18 mg/dL | 7 – 20 mg/dL |
| Creatinine | 1.0 mg/dL | 0.7 – 1.3 mg/dL |
| eGFR | >60 mL/min/1.73m² | > 60 |
| Glucose | 148 mg/dL | 70 – 100 mg/dL |
| **Liver function** | | |
| Total protein | 6.8 g/dL | 6.3 – 8.2 g/dL |
| Albumin | 3.5 g/dL | 3.5 – 5.0 g/dL |
| Total bilirubin | 0.7 mg/dL | 0.2 – 1.2 mg/dL |
| AST | 28 U/L | 10 – 40 U/L |
| ALT | 24 U/L | 7 – 56 U/L |
| Alkaline phosphatase | 84 U/L | 44 – 147 U/L |
| **Minerals** | | |
| Calcium (total) | 9.1 mg/dL | 8.5 – 10.5 mg/dL |

### Sepsis Markers

| Test | Result | Reference Range |
|------|--------|----------------|
| Lactate | 1.2 mmol/L | < 2.0 mmol/L |
| Procalcitonin | 0.22 ng/mL | < 0.25 ng/mL |
| CRP | 44 mg/L | < 10 mg/L |

## Expected Output

- **Presentation:** Nonsevere CDI on active fluoroquinolone therapy
- **Antibiotic Initiation** *(if applicable):*
  - Vancomycin 125 mg PO Q6H × 10 days
  - Fidaxomicin 200 mg PO BID × 10 days is an alternative but **requires Infectious Disease approval at SJN prior to use**
  - **Discontinue levofloxacin** — pneumonia is clinically resolved (afebrile since day 3, SpO₂ at baseline, tolerating diet); completing 5 days is reasonable given documented clinical improvement. Stopping the inciting fluoroquinolone is the highest-yield intervention.
  - If the clinical team determines that continued antibiotic therapy is required, de-escalate to a lower CDI-risk agent whenever possible
  - If antibiotics cannot be discontinued or de-escalated, extend CDI treatment duration beyond 10 days — continue vancomycin until 5–7 days after the systemic antibiotic course is completed
  - Place in enteric isolation; soap-and-water hand hygiene
  - **Anti-peristaltic agents are contraindicated**
- **Treatment Optimization** *(if applicable):*
  - Test-of-cure is NOT recommended

## Related

- [[brain/Case Style Guide]]
- [[reference/Navigator/Cases/guidelines/local/SJN-CDI-Guidelines]]
- [[reference/Navigator/Cases/guidelines/national/2021-IDSA-SHEA-CDI-Focused-Update]]
