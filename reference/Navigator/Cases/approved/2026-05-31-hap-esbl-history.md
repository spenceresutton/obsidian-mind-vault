---
date: 2026-05-31
description: "HAP case — hospital-acquired pneumonia with prior ESBL-producing Klebsiella pneumoniae from sputum 8 months ago; prior MDRO history triggers meropenem; MRSA PCR negative removes vancomycin; ESBL oral step-down to FQ or TMP/SMX if susceptible and monomicrobial"
disease_state: "HAP"
difficulty: medium
author: Spencer Sutton
status: approved
case_number: "HAP-14"
challenge_types:
  - esbl-history
  - carbapenem-escalation
  - mdro-risk
  - hap-vap-empiric
tags:
  - sanity-test
  - case
  - hap
source: generated
---

# PNA Case 14: HAP with ESBL History

**Difficulty:** medium
**Author:** Spencer Sutton

## Prompt

SS is a 66-year-old female with a past medical history significant for type 2 diabetes mellitus, hypertension, and mild cognitive impairment who was admitted eight days ago for an elective right total knee arthroplasty. Eight months ago, during a hospitalization for aspiration pneumonia, sputum cultures grew *Klebsiella pneumoniae* producing an extended-spectrum beta-lactamase (ESBL). She was treated with meropenem at that time and has had no further antibiotic courses since discharge. No MRSA or Pseudomonas respiratory isolation is on record.

On hospital day 8, she develops new fever, productive cough with purulent sputum, and worsening dyspnea requiring supplemental oxygen. A chest X-ray is obtained and compared to the post-operative day 1 film. Blood cultures and sputum culture are sent. MRSA nasal PCR is obtained. Her allergy history is reviewed prior to antibiotic selection.

She appears acutely ill with moderate respiratory distress. Lung exam reveals decreased breath sounds at the right lower lobe with coarse crackles and dullness to percussion at the right base. She is alert and oriented to person, place, and time but appears fatigued.

She takes lisinopril 10 mg daily, atorvastatin 40 mg nightly, metformin 1000 mg BID (held per perioperative protocol), and aspirin 81 mg daily. She has no documented drug allergies.

Vitals (hospital day 8): T 39.0°C, HR 108, BP 110/72, RR 24, SpO2 93% on 4L NC.

Ht: 5'4"   Wt: 72 kg   BMI: 27.5   Baseline SCr: 0.9 mg/dL   Allergies: NKDA

## Imaging

### Chest X-Ray — PA and Lateral

1. New right lower lobe consolidation, not present on post-operative day 1 film.
2. No cavitary lesion or pleural effusion identified.
3. Cardiac silhouette within normal limits. No pulmonary vascular congestion.
4. Impression: New right lower lobe consolidation consistent with hospital-acquired pneumonia in the appropriate clinical context. Clinical correlation recommended.

## Culture Results

Blood cultures: 2 sets collected — no growth at time of case presentation.
Sputum culture: Pending — purulent sputum sent. Gram stain: gram-negative rods, heavy growth.
Respiratory viral panel: Negative.
MRSA PCR (nasal swab): Negative.

## Labs

### Complete Blood Count with Differential

| Test | Result | Reference Range |
|------|--------|-----------------|
| WBC | 16.2 k/µL | 4.5 – 11.0 k/µL |
| Neutrophils (abs.) | 13.9 k/µL | 1.8 – 7.7 k/µL |
| Neutrophils (%) | 86% | 50 – 70% |
| Bands | 10% | < 10% |
| Lymphocytes (abs.) | 1.3 k/µL | 1.0 – 4.8 k/µL |
| Monocytes (abs.) | 0.7 k/µL | 0.2 – 1.0 k/µL |
| RBC | 3.8 M/µL | 4.2 – 5.4 M/µL |
| Hemoglobin | 11.4 g/dL | 12.0 – 16.0 g/dL |
| Hematocrit | 34.2% | 37 – 47% |
| MCV | 90 fL | 80 – 100 fL |
| MCH | 30.0 pg | 27 – 33 pg |
| MCHC | 33.3 g/dL | 32 – 36 g/dL |
| RDW | 14.4% | 11.5 – 14.5% |
| Platelets | 264 k/µL | 150 – 400 k/µL |
| MPV | 9.9 fL | 7.5 – 10.5 fL |

### Comprehensive Metabolic Panel

| Test | Result | Reference Range |
|------|--------|-----------------|
| **Electrolytes** | | |
| Sodium | 136 mEq/L | 136 – 145 mEq/L |
| Potassium | 4.2 mEq/L | 3.5 – 5.1 mEq/L |
| Chloride | 101 mEq/L | 98 – 106 mEq/L |
| CO₂ (bicarb) | 22 mEq/L | 22 – 29 mEq/L |
| BUN | 18 mg/dL | 7 – 20 mg/dL |
| Creatinine | 1.0 mg/dL | 0.5 – 1.1 mg/dL |
| eGFR | 72 mL/min/1.73m² | > 60 |
| Glucose | 198 mg/dL | 70 – 100 mg/dL |
| **Liver function** | | |
| Total protein | 6.1 g/dL | 6.3 – 8.2 g/dL |
| Albumin | 2.9 g/dL | 3.5 – 5.0 g/dL |
| Total bilirubin | 0.8 mg/dL | 0.2 – 1.2 mg/dL |
| AST | 24 U/L | 10 – 40 U/L |
| ALT | 19 U/L | 7 – 56 U/L |
| Alkaline phosphatase | 78 U/L | 44 – 147 U/L |
| **Minerals** | | |
| Calcium (total) | 8.6 mg/dL | 8.5 – 10.5 mg/dL |

### Sepsis Markers

| Test | Result | Reference Range |
|------|--------|-----------------|
| Lactate | 1.8 mmol/L | < 2.0 mmol/L |
| Procalcitonin | 6.8 ng/mL | < 0.25 ng/mL |
| CRP | 201 mg/L | < 10 mg/L |

*Resulted: hospital day 8*

## Expected Output

- **Presentation:** Hospital-acquired pneumonia with ESBL history.

- **Antibiotic Initiation** *(if applicable):*
  - Meropenem 1g q8h
  - Comment that MRSA coverage is not indicated given negative MRSA nasal PCR
  - Comment that recent ESBL history warrants empiric coverage with a carbapenem
  - Treatment duration is 7 days

- **Treatment Optimization** *(if applicable):*
  - If culture returns ESBL-producing organism: continue meropenem for 7 days
  - If ESBL is susceptible to a fluoroquinolone or TMP/SMX and the infection is monomicrobial: reasonable to convert to oral therapy when afebrile, hemodynamically stable, and without leukocytosis
  - If culture returns a non-ESBL organism: de-escalate to an appropriate agent based on susceptibility results

## Related

- [[brain/Case Style Guide]]
- [[reference/Navigator/Cases/guidelines/national/2016-IDSA-ATS-HAP-VAP-Guidelines]]
- [[reference/Navigator/Cases/guidelines/local/SJN-Inpatient-Pneumonia-Guidelines]]
- [[reference/Navigator/Cases/guidelines/local/SJN-Renal-Dose-Adjustment-Policy]]
