---
date: 2026-05-26
description: "CAP case — non-severe CAP with prior Pseudomonas aeruginosa sputum colonization and pending MRSA PCR"
disease_state: "CAP"
difficulty: hard
author: "Spencer"
status: approved
case_number: "CAP-09"
challenge_types: [non-severe-CAP, Pseudomonas-colonization, MRSA-PCR-pending, de-escalation, duration]
tags:
  - sanity-test
  - case
  - cap
source: google-doc
---

# CAP Case 9: Non-severe CAP with known Pseudomonas colonization

**Difficulty:** hard
**Author:** Spencer

## Prompt

SS is a 48-year-old male with a past medical history significant for hypertension, type 2 diabetes mellitus, asthma, and COPD who presents to the emergency department with worsening shortness of breath. He reports being in his usual state of health until approximately about 3-4 days ago. The patient developed increasing dyspnea, productive cough with yellow-green sputum, pleuritic chest pain, and subjective fevers up to 100.1°F at home. On arrival to the ED, vitals are: T 99.8°F (37.7°C), HR 84, BP 138/82, RR 24, SpO2 88% on room air. He appears in moderate respiratory distress and is placed on 2L nasal cannula with improvement to SpO2 94%. Lung exam reveals decreased breath sounds and dullness to percussion at the right base, with focal crackles. He has no known sick contacts, no recent travel, and no immunosuppressive conditions. Initially concern was for COPD exacerbation without high concern for pneumonia. Antibiotics were initially held, however the team now plans to initiate. He takes lisinopril, amlodipine, metformin, and an albuterol inhaler PRN. He has no documented drug allergies. A bedside chest X-ray is obtained. Labs are drawn.

**Ht:** 5'10"   **Wt:** 86 kg   **BMI:** 27.6   **Baseline SCr:** ~0.9 mg/dL   **Allergies:** NKDA

## Imaging

**Chest X-Ray — portable AP, bedside**

1. Right lower lobe opacity with air bronchograms — appearance most consistent with lobar consolidation, though portable technique limits full characterization. Pneumonia cannot be excluded and is the primary consideration given clinical context.
2. COPD/emphysema — hyperinflation with flattened hemidiaphragms and peripheral vascular attenuation bilaterally, consistent with known obstructive lung disease.
3. No large pleural effusion or pneumothorax identified on this projection. Costophrenic angles partially obscured by technique.
4. Cardiac silhouette within normal limits. No pulmonary vascular redistribution.
5. Impression: Right lower lobe consolidative opacity consistent with pneumonia in the appropriate clinical context. Repeat PA/lateral radiograph recommended when patient is able to cooperate for full characterization.

## Culture Results

- Blood cultures: 2 sets collected on presentation — no growth to date.
- Sputum culture (current): Pending.
- Sputum culture (previous admit, DKA 9 months prior): *Pseudomonas aeruginosa*
- Respiratory viral panel: Sent — results pending.
- Urine antigen: Streptococcus pneumoniae and Legionella pneumophila urinary antigens sent — results pending.
- MRSA PCR: Pending.

## Labs

### CBC

| Test | Result | Reference Range |
|------|--------|----------------|
| WBC | 11.0 k/µL | 4.5 – 11.0 k/µL |
| Neutrophils (abs.) | 8.4 k/µL | 1.8 – 7.7 k/µL |
| Bands | 8% | < 10% |
| Lymphocytes (abs.) | 1.2 k/µL | 1.0 – 4.8 k/µL |
| Monocytes (abs.) | 0.6 k/µL | 0.2 – 1.0 k/µL |
| RBC | 4.8 M/µL | 4.5 – 5.9 M/µL |
| Hemoglobin | 14.2 g/dL | 13.5 – 17.5 g/dL |
| Hematocrit | 42.6% | 41 – 53% |
| MCV | 89 fL | 80 – 100 fL |
| MCH | 29.6 pg | 27 – 33 pg |
| MCHC | 33.4 g/dL | 32 – 36 g/dL |
| RDW | 13.1% | 11.5 – 14.5% |
| Platelets | 284 k/µL | 150 – 400 k/µL |
| MPV | 9.6 fL | 7.5 – 10.5 fL |

### CMP

| Test | Result | Reference Range |
|------|--------|----------------|
| Sodium | 138 mEq/L | 136 – 145 mEq/L |
| Potassium | 4.2 mEq/L | 3.5 – 5.1 mEq/L |
| Chloride | 101 mEq/L | 98 – 106 mEq/L |
| CO₂ (bicarb) | 24 mEq/L | 22 – 29 mEq/L |
| BUN | 14 mg/dL | 7 – 20 mg/dL |
| Creatinine | 0.9 mg/dL | 0.7 – 1.3 mg/dL |
| eGFR | > 60 mL/min/1.73m² | > 60 |
| Glucose | 172 mg/dL | 70 – 100 mg/dL |
| Total protein | 7.0 g/dL | 6.3 – 8.2 g/dL |
| Albumin | 3.9 g/dL | 3.5 – 5.0 g/dL |
| Total bilirubin | 0.6 mg/dL | 0.2 – 1.2 mg/dL |
| AST | 24 U/L | 10 – 40 U/L |
| ALT | 28 U/L | 7 – 56 U/L |
| Alkaline phosphatase | 68 U/L | 44 – 147 U/L |
| Calcium (total) | 9.1 mg/dL | 8.5 – 10.5 mg/dL |

### Sepsis Markers

| Test | Result | Reference Range |
|------|--------|----------------|
| Lactate | 1.6 mmol/L | < 2.0 mmol/L |
| Procalcitonin | 0.64 ng/mL | < 0.25 ng/mL |
| CRP | 74 mg/L | < 10 mg/L |

## Expected Output

- **Presentation:** Non-severe community-acquired pneumonia with history of Pseudomonas colonization
- **Antibiotic Initiation** *(if applicable):* Cefepime 2g q8h + azithromycin 500 mg x3 days
  - Comment that atypical coverage discontinuation may be warranted
  - Comment that MRSA risk factors are not present currently, but MRSA PCR is important for follow-up
  - Comment that treatment duration is 7 days if confirmed Pseudomonas, but can be de-escalated based on culture; duration is 5 days if not Pseudomonas
  - Alternatives: Piperacillin-Tazobactam 4.5g q8h instead of cefepime; Doxycycline 100 mg BID instead of azithromycin
  - **Do not recommend fluoroquinolones without intolerance to beta-lactams**
- **Treatment Optimization** *(if applicable):*
  - If not Pseudomonas, de-escalate to target pathogen
  - Treatment duration goes from 7 to 5 days if ultimately not Pseudomonas

## Related

- [[brain/Case Style Guide]]
