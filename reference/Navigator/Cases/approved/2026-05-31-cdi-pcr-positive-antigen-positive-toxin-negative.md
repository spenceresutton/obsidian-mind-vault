---
date: 2026-05-31
description: "CDI case — PCR+/Antigen+/Toxin− with modest clinical suspicion and borderline stool output; SJN diagnosis algorithm; do not treat; enteric isolation regardless"
disease_state: "CDI"
difficulty: medium
author: "Spencer"
status: approved
case_number: "CDI-04"
challenge_types: [CDI-diagnosis-algorithm, PCR-positive-toxin-negative, do-not-treat, enteric-isolation, colonization-vs-infection]
tags:
  - sanity-test
  - case
  - cdi
source: generated
---

# CDI Case 4: PCR+/Antigen+/Toxin− — Treat or Not?

**Difficulty:** medium
**Author:** Spencer

## Prompt

TW is a 71-year-old female with a past medical history significant for hypertension, osteoarthritis, and hypothyroidism who is currently admitted for a hip fracture repair. She is on postoperative day 3. The surgical team is called because nursing documented 3 loose stools over the past 24 hours and the patient reports mild lower abdominal discomfort. She received a 24-hour perioperative course of cefazolin that ended 3 days ago. She is otherwise tolerating a regular diet and ambulating with physical therapy. She is afebrile and hemodynamically stable. On assessment, vitals are: T 37.2°C, HR 78, BP 126/74, RR 15, SpO₂ 97% on room air. Abdomen is soft, mildly tender in the lower quadrants, non-distended, with normal bowel sounds. She takes lisinopril, levothyroxine, and acetaminophen. She has no known drug allergies.

**Ht:** 5'4"   **Wt:** 68 kg   **BMI:** 25.8   **Baseline SCr:** 0.8 mg/dL   **Allergies:** NKDA

## Stool Studies

- *C. difficile* PCR (NAAT): **Positive**
- GDH (Glutamate Dehydrogenase) Antigen: **Positive**
- *C. difficile* Toxin A/B EIA: **Negative**

## Labs

### CBC

| Test | Result | Reference Range |
|------|--------|----------------|
| WBC | 9.6 k/µL | 4.5 – 11.0 k/µL |
| Neutrophils (abs.) | 6.2 k/µL | 1.8 – 7.7 k/µL |
| Bands | 2% | < 10% |
| Lymphocytes (abs.) | 2.4 k/µL | 1.0 – 4.8 k/µL |
| Monocytes (abs.) | 0.7 k/µL | 0.2 – 1.0 k/µL |
| RBC | 3.9 M/µL | 4.0 – 5.2 M/µL |
| Hemoglobin | 11.2 g/dL | 12.0 – 16.0 g/dL |
| Hematocrit | 33.8% | 36 – 47% |
| MCV | 88 fL | 80 – 100 fL |
| MCH | 28.7 pg | 27 – 33 pg |
| MCHC | 33.1 g/dL | 32 – 36 g/dL |
| RDW | 13.4% | 11.5 – 14.5% |
| Platelets | 286 k/µL | 150 – 400 k/µL |
| MPV | 9.4 fL | 7.5 – 10.5 fL |

### CMP

| Test | Result | Reference Range |
|------|--------|----------------|
| **Electrolytes** | | |
| Sodium | 139 mEq/L | 136 – 145 mEq/L |
| Potassium | 3.9 mEq/L | 3.5 – 5.1 mEq/L |
| Chloride | 103 mEq/L | 98 – 106 mEq/L |
| CO₂ (bicarb) | 25 mEq/L | 22 – 29 mEq/L |
| BUN | 14 mg/dL | 7 – 20 mg/dL |
| Creatinine | 0.9 mg/dL | 0.7 – 1.3 mg/dL |
| eGFR | >60 mL/min/1.73m² | > 60 |
| Glucose | 104 mg/dL | 70 – 100 mg/dL |
| **Liver function** | | |
| Total protein | 6.9 g/dL | 6.3 – 8.2 g/dL |
| Albumin | 3.6 g/dL | 3.5 – 5.0 g/dL |
| Total bilirubin | 0.5 mg/dL | 0.2 – 1.2 mg/dL |
| AST | 19 U/L | 10 – 40 U/L |
| ALT | 16 U/L | 7 – 56 U/L |
| Alkaline phosphatase | 76 U/L | 44 – 147 U/L |
| **Minerals** | | |
| Calcium (total) | 9.0 mg/dL | 8.5 – 10.5 mg/dL |

### Sepsis Markers

| Test | Result | Reference Range |
|------|--------|----------------|
| Lactate | 0.9 mmol/L | < 2.0 mmol/L |
| Procalcitonin | 0.12 ng/mL | < 0.25 ng/mL |
| CRP | 18 mg/L | < 10 mg/L |

## Expected Output

- **Presentation:** PCR+/Antigen+/Toxin− with low clinical suspicion
- **Antibiotic Initiation** *(if applicable):*
  - Correlate with the full clinical picture — treatment is most likely not warranted in this presentation given borderline stool output, absence of systemic signs, and a plausible postoperative explanation for loose stools
  - Place in enteric isolation regardless of treatment decision — contact precautions and soap-and-water hand hygiene apply to all PCR-positive patients
  - If the patient acutely worsens or all other causes have been excluded, consider: Vancomycin 125 mg PO Q6H × 10 days
  - **INCORRECT: Initiating treatment based on PCR and antigen positivity alone without toxin confirmation and without high clinical suspicion**
- **Treatment Optimization** *(if applicable):* N/A

## Related

- [[brain/Case Style Guide]]
- [[reference/Navigator/Cases/guidelines/local/SJN-CDI-Guidelines]]
- [[reference/Navigator/Cases/guidelines/national/2021-IDSA-SHEA-CDI-Focused-Update]]
