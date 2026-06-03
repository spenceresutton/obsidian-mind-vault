---
date: 2026-05-31
description: "CDI case — initial severe CDI in a 72-year-old with creatinine ≥1.5 as the sole severity marker; WBC below threshold; same oral vanco regimen as nonsevere"
disease_state: "CDI"
difficulty: easy/medium
author: "Spencer"
status: approved
case_number: "CDI-02"
challenge_types: [initial-CDI, severity-classification, creatinine-severity-marker, fidaxomicin-ID-approval]
tags:
  - sanity-test
  - case
  - cdi
source: generated
---

# CDI Case 2: Initial Severe CDI

**Difficulty:** easy/medium
**Author:** Spencer

## Prompt

ML is a 72-year-old female with a past medical history significant for hypertension, type 2 diabetes mellitus, and CKD stage 2 (baseline creatinine 1.1 mg/dL) who presents with 5 days of 5–7 loose stools per day and mild diffuse abdominal cramping. She completed a 7-day course of cefdinir 10 days ago for a skin and soft tissue infection. She denies hematochezia, nausea, or vomiting and has no prior history of CDI. On arrival, vitals are: T 38.1°C, HR 94, BP 142/86, RR 17, SpO₂ 96% on room air. She is in no acute distress. Abdomen is soft with mild diffuse tenderness and active bowel sounds; no guarding, rebound, or rigidity. She takes lisinopril, amlodipine, metformin, and metoprolol. She has no known drug allergies.

**Ht:** 5'5"   **Wt:** 72 kg   **BMI:** 26.3   **Baseline SCr:** 1.1 mg/dL   **Allergies:** NKDA

## Stool Studies

- *C. difficile* PCR (NAAT): **Positive**
- GDH (Glutamate Dehydrogenase) Antigen: **Positive**
- *C. difficile* Toxin A/B EIA: **Positive**

## Labs

### CBC

| Test | Result | Reference Range |
|------|--------|----------------|
| WBC | 13.8 k/µL | 4.5 – 11.0 k/µL |
| Neutrophils (abs.) | 9.2 k/µL | 1.8 – 7.7 k/µL |
| Bands | 6% | < 10% |
| Lymphocytes (abs.) | 2.1 k/µL | 1.0 – 4.8 k/µL |
| Monocytes (abs.) | 0.9 k/µL | 0.2 – 1.0 k/µL |
| RBC | 4.1 M/µL | 4.0 – 5.2 M/µL |
| Hemoglobin | 12.4 g/dL | 12.0 – 16.0 g/dL |
| Hematocrit | 37.6% | 36 – 47% |
| MCV | 89 fL | 80 – 100 fL |
| MCH | 30.2 pg | 27 – 33 pg |
| MCHC | 33.0 g/dL | 32 – 36 g/dL |
| RDW | 13.6% | 11.5 – 14.5% |
| Platelets | 312 k/µL | 150 – 400 k/µL |
| MPV | 9.8 fL | 7.5 – 10.5 fL |

### CMP

| Test | Result | Reference Range |
|------|--------|----------------|
| **Electrolytes** | | |
| Sodium | 136 mEq/L | 136 – 145 mEq/L |
| Potassium | 4.1 mEq/L | 3.5 – 5.1 mEq/L |
| Chloride | 100 mEq/L | 98 – 106 mEq/L |
| CO₂ (bicarb) | 22 mEq/L | 22 – 29 mEq/L |
| BUN | 28 mg/dL | 7 – 20 mg/dL |
| Creatinine | 1.6 mg/dL | 0.7 – 1.3 mg/dL |
| eGFR | 34 mL/min/1.73m² | > 60 |
| Glucose | 138 mg/dL | 70 – 100 mg/dL |
| **Liver function** | | |
| Total protein | 6.8 g/dL | 6.3 – 8.2 g/dL |
| Albumin | 3.4 g/dL | 3.5 – 5.0 g/dL |
| Total bilirubin | 0.8 mg/dL | 0.2 – 1.2 mg/dL |
| AST | 26 U/L | 10 – 40 U/L |
| ALT | 21 U/L | 7 – 56 U/L |
| Alkaline phosphatase | 81 U/L | 44 – 147 U/L |
| **Minerals** | | |
| Calcium (total) | 8.8 mg/dL | 8.5 – 10.5 mg/dL |

### Sepsis Markers

| Test | Result | Reference Range |
|------|--------|----------------|
| Lactate | 1.4 mmol/L | < 2.0 mmol/L |
| Procalcitonin | 0.34 ng/mL | < 0.25 ng/mL |
| CRP | 52 mg/L | < 10 mg/L |

## Expected Output

- **Presentation:** Initial Severe CDI
- **Antibiotic Initiation** *(if applicable):*
  - Vancomycin 125 mg PO Q6H × 10 days — severity classification does NOT change the antibiotic regimen for initial non-fulminant CDI
  - Fidaxomicin 200 mg PO BID × 10 days remains an option but **requires Infectious Disease approval at SJN prior to use**
  - Place in enteric isolation (contact precautions); soap-and-water hand hygiene
  - Assess and discontinue unnecessary systemic antibiotics
  - Monitor for signs of progression to fulminant CDI: worsening abdominal pain, development of ileus, hemodynamic instability — escalation required if these develop
  - **Do not use IV vancomycin — does not achieve adequate luminal concentrations**
  - **Do not use oral metronidazole — not appropriate when oral vancomycin or fidaxomicin is available**
  - **INCORRECT: Vancomycin 500 mg PO Q6H — this is the fulminant CDI regimen; not indicated in the absence of ileus, shock, or megacolon**
- **Treatment Optimization** *(if applicable):*
  - Severe CDI on presentation is a recurrence risk factor per SJN guidelines; if symptoms have not resolved by day 10, extending treatment duration is reasonable to consider — extension is not the default
  - Test-of-cure is NOT recommended

## Related

- [[brain/Case Style Guide]]
- [[reference/Navigator/Cases/guidelines/local/SJN-CDI-Guidelines]]
- [[reference/Navigator/Cases/guidelines/national/2021-IDSA-SHEA-CDI-Focused-Update]]
