---
date: 2026-06-01
description: "CDI case — PCR+/Antigen−/Toxin− indicating CDI colonization with very low organism levels; clear do not treat; enteric isolation still required"
disease_state: "CDI"
difficulty: easy
author: "Spencer"
status: approved
case_number: "CDI-09"
challenge_types: [CDI-diagnosis-algorithm, PCR-positive-antigen-negative, colonization, do-not-treat, enteric-isolation]
tags:
  - sanity-test
  - case
  - cdi
source: generated
---

# CDI Case 9: PCR+/Antigen−/Toxin− — Do Not Treat

**Difficulty:** easy
**Author:** Spencer

## Prompt

BH is a 74-year-old female with a past medical history significant for hypertension and atrial fibrillation who is on postoperative day 2 following an elective right total knee arthroplasty. Nursing reports 3 loose stools over the past 24 hours. The patient is afebrile, hemodynamically stable, tolerating a regular diet, and denies abdominal pain or cramping. She received a single preoperative dose of cefazolin for surgical prophylaxis. The team sends CDI stool testing. On assessment, vitals are: T 36.9°C, HR 72, BP 128/76, RR 14, SpO₂ 98% on room air. Abdomen is soft, non-tender, non-distended with normal bowel sounds. She takes metoprolol, apixaban, lisinopril, and atorvastatin. She has no known drug allergies.

**Ht:** 5'3"   **Wt:** 70 kg   **BMI:** 27.4   **Baseline SCr:** 0.8 mg/dL   **Allergies:** NKDA

## Stool Studies

- *C. difficile* PCR (NAAT): **Positive**
- GDH (Glutamate Dehydrogenase) Antigen: **Negative**
- *C. difficile* Toxin A/B EIA: **Negative**

## Labs

### CBC

| Test | Result | Reference Range |
|------|--------|----------------|
| WBC | 9.2 k/µL | 4.5 – 11.0 k/µL |
| Neutrophils (abs.) | 6.0 k/µL | 1.8 – 7.7 k/µL |
| Bands | 2% | < 10% |
| Lymphocytes (abs.) | 2.2 k/µL | 1.0 – 4.8 k/µL |
| Monocytes (abs.) | 0.7 k/µL | 0.2 – 1.0 k/µL |
| RBC | 3.8 M/µL | 4.0 – 5.2 M/µL |
| Hemoglobin | 11.0 g/dL | 12.0 – 16.0 g/dL |
| Hematocrit | 33.2% | 36 – 47% |
| MCV | 88 fL | 80 – 100 fL |
| MCH | 28.9 pg | 27 – 33 pg |
| MCHC | 33.1 g/dL | 32 – 36 g/dL |
| RDW | 13.1% | 11.5 – 14.5% |
| Platelets | 304 k/µL | 150 – 400 k/µL |
| MPV | 9.4 fL | 7.5 – 10.5 fL |

### CMP

| Test | Result | Reference Range |
|------|--------|----------------|
| **Electrolytes** | | |
| Sodium | 140 mEq/L | 136 – 145 mEq/L |
| Potassium | 3.8 mEq/L | 3.5 – 5.1 mEq/L |
| Chloride | 104 mEq/L | 98 – 106 mEq/L |
| CO₂ (bicarb) | 25 mEq/L | 22 – 29 mEq/L |
| BUN | 12 mg/dL | 7 – 20 mg/dL |
| Creatinine | 0.8 mg/dL | 0.7 – 1.3 mg/dL |
| eGFR | >60 mL/min/1.73m² | > 60 |
| Glucose | 108 mg/dL | 70 – 100 mg/dL |
| **Liver function** | | |
| Total protein | 6.8 g/dL | 6.3 – 8.2 g/dL |
| Albumin | 3.7 g/dL | 3.5 – 5.0 g/dL |
| Total bilirubin | 0.5 mg/dL | 0.2 – 1.2 mg/dL |
| AST | 18 U/L | 10 – 40 U/L |
| ALT | 14 U/L | 7 – 56 U/L |
| Alkaline phosphatase | 68 U/L | 44 – 147 U/L |
| **Minerals** | | |
| Calcium (total) | 9.1 mg/dL | 8.5 – 10.5 mg/dL |

### Sepsis Markers

| Test | Result | Reference Range |
|------|--------|----------------|
| Lactate | 0.8 mmol/L | < 2.0 mmol/L |
| Procalcitonin | 0.10 ng/mL | < 0.25 ng/mL |
| CRP | 14 mg/L | < 10 mg/L |

## Expected Output

- **Presentation:** PCR+/Antigen−/Toxin− — CDI colonization, do not treat
- **Antibiotic Initiation** *(if applicable):*
  - Do not treat — PCR positivity with negative antigen and negative toxin represents colonization, not active CDI. Treatment is not indicated.
  - Place in enteric isolation (contact precautions) regardless of treatment decision — soap-and-water hand hygiene
  - **INCORRECT: Initiating vancomycin or any CDI-directed antibiotic therapy based on PCR positivity alone when both antigen and toxin are negative**
- **Treatment Optimization** *(if applicable):* N/A

## Related

- [[brain/Case Style Guide]]
- [[reference/Navigator/Cases/guidelines/local/SJN-CDI-Guidelines]]
- [[reference/Navigator/Cases/guidelines/national/2021-IDSA-SHEA-CDI-Focused-Update]]
