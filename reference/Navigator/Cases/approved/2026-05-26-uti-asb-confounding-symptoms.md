---
date: 2026-05-26
description: "UTI case — asymptomatic bacteriuria with confounding symptoms from BPH and acute DKA illness"
disease_state: "UTI"
difficulty: medium
author: "Spencer"
status: approved
case_number: "UTI-02"
challenge_types: [ASB, confounding-symptoms, BPH, diabetes]
tags:
  - sanity-test
  - case
  - uti
source: google-doc
---

# UTI Case 2: Asymptomatic Bacteriuria with confounding symptoms

**Difficulty:** medium
**Author:** Spencer

## Prompt

SS is a 46-year-old male with a past medical history significant for asthma, benign prostatic hypertrophy (BPH), and type 2 diabetes mellitus (T2DM) who initially presented to the emergency department with a two-day history of polyuria, polydipsia, nausea, vomiting, and altered mental status. On arrival, serum glucose was 612 mg/dL, bicarbonate 8 mEq/L, pH 7.18, and anion gap 28. The patient was diagnosed with diabetic ketoacidosis (DKA) and admitted to the medical ICU (MICU) for IV insulin therapy and aggressive fluid resuscitation per institutional DKA protocol.

After 4 days in the MICU, the patient's anion gap closed, bicarbonate normalized, and he was transitioned to subcutaneous insulin and stepped down to the general medicine floor. On the morning of his first full day on stepdown, the patient endorsed increased difficulty with urination. He denies frank dysuria, fever, chills, or flank pain. Vitals are stable: T 37.1°C, HR 82, BP 118/74, RR 16, SpO2 97% on room air.

UA with microscopy:

| Test | Result |
|------|--------|
| Color | Yellow, cloudy |
| Specific gravity | 1.022 |
| pH | 5.8 |
| Leukocyte esterase | 3+ |
| Nitrites | Positive |
| WBC | > 100 /hpf |
| RBC | 5 – 10 /hpf |
| Bacteria | Many |
| Epithelial cells | Rare |
| Protein | Trace |
| Glucose | 1+ |
| Ketones | Trace |

## Culture Results

- Urine culture: Pending — no growth at time of case presentation. Gram stain: gram-negative rods.
- Blood cultures: 2 sets collected on admission — no growth to date.

## Labs

### CBC

| Test | Result | Reference Range |
|------|--------|----------------|
| WBC | 9.2 k/µL | 4.5 – 11.0 k/µL |
| Neutrophils (abs.) | 6.8 k/µL | 1.8 – 7.7 k/µL |
| Bands | 4% | < 10% |
| Lymphocytes (abs.) | 1.6 k/µL | 1.0 – 4.8 k/µL |
| Monocytes (abs.) | 0.5 k/µL | 0.2 – 1.0 k/µL |
| RBC | 4.6 M/µL | 4.5 – 5.9 M/µL |
| Hemoglobin | 13.8 g/dL | 13.5 – 17.5 g/dL |
| Hematocrit | 41.2% | 41 – 53% |
| MCV | 90 fL | 80 – 100 fL |
| MCH | 30.1 pg | 27 – 33 pg |
| MCHC | 33.8 g/dL | 32 – 36 g/dL |
| RDW | 13.2% | 11.5 – 14.5% |
| Platelets | 298 k/µL | 150 – 400 k/µL |
| MPV | 9.1 fL | 7.5 – 10.5 fL |

### CMP

| Test | Result | Reference Range |
|------|--------|----------------|
| Sodium | 138 mEq/L | 136 – 145 mEq/L |
| Potassium | 4.1 mEq/L | 3.5 – 5.1 mEq/L |
| Chloride | 103 mEq/L | 98 – 106 mEq/L |
| CO₂ (bicarb) | 24 mEq/L | 22 – 29 mEq/L |
| BUN | 18 mg/dL | 7 – 20 mg/dL |
| Creatinine | 1.0 mg/dL | 0.7 – 1.3 mg/dL |
| eGFR | 88 mL/min/1.73m² | > 60 |
| Glucose | 148 mg/dL | 70 – 100 mg/dL |
| Total protein | 7.1 g/dL | 6.3 – 8.2 g/dL |
| Albumin | 3.8 g/dL | 3.5 – 5.0 g/dL |
| Total bilirubin | 0.7 mg/dL | 0.2 – 1.2 mg/dL |
| AST | 28 U/L | 10 – 40 U/L |
| ALT | 34 U/L | 7 – 56 U/L |
| Alkaline phosphatase | 72 U/L | 44 – 147 U/L |
| Calcium (total) | 9.2 mg/dL | 8.5 – 10.5 mg/dL |

### Sepsis Markers

| Test | Result | Reference Range |
|------|--------|----------------|
| Lactate | 1.4 mmol/L | < 2.0 mmol/L |
| Procalcitonin | 0.18 ng/mL | < 0.25 ng/mL |
| CRP | 22 mg/L | < 10 mg/L |

## Expected Output

- **Presentation:** Asymptomatic bacteriuria
  - Recognize difficulty urinating likely associated with BPH and acute illness (DKA)
  - UA is concerning for infection, however UTI diagnosis requires symptoms
  - Patient has no systemic signs of infection
  - **Navigator should identify that the clinician must decide whether symptoms represent UTI or BPH + acute illness**
- **Antibiotic Initiation** *(if applicable):*
  - Assess whether symptoms are associated with a UTI
  - Watch off antibiotics (assuming decision is that it is not a UTI)
  - Nitrofurantoin 100 mg BID x5 days (Assuming decision is that it is a UTI)
- **Treatment Optimization** *(if applicable):* N/A

## Related

- [[brain/Case Style Guide]]
- [[reference/Navigator/Cases/guidelines/national/2019-IDSA-ASB-Guidelines]]
- [[reference/Navigator/Cases/guidelines/local/SJN-Inpatient-UTI-Guidelines]]
