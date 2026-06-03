---
date: 2026-05-26
description: "CAP case — aspiration pneumonia with cavitary lung abscess and positive MRSA PCR; anaerobic coverage appropriate (abscess present); MRSA causes pulmonary abscesses and necrotizing pneumonia"
disease_state: "CAP"
difficulty: hard
author: Spencer
status: approved
case_number: "CAP-11"
challenge_types:
  - aspiration-pneumonia
  - lung-abscess
  - MRSA
  - anaerobic-coverage
  - IV-to-PO
  - de-escalation
tags:
  - sanity-test
  - case
  - cap
source: generated
---

# CAP Case 11: Aspiration Pneumonia with Cavitary Abscess and Positive MRSA PCR

**Difficulty:** hard
**Author:** Spencer

## Prompt

SS is a 68-year-old male with a past medical history significant for Parkinson's disease, type 2 diabetes mellitus, and hypertension who is brought to the emergency department by family with a 4-day history of productive cough, fever, and progressive dyspnea. Family reports a witnessed aspiration event 5 days ago during a meal. He has significant dysphagia at baseline secondary to his Parkinson's disease and has had multiple prior aspiration events. His current medications include carbidopa-levodopa 25-100mg TID, metformin 1000mg BID, lisinopril 10mg daily, and amlodipine 5mg daily.

On arrival, vitals are: T 38.9°C, HR 108, BP 142/88, RR 24, SpO2 91% on 4L NC.

Ht: 5'10"   Wt: 78 kg   BMI: 25.1   Baseline SCr: 1.1 mg/dL   Allergies: NKDA

## Imaging

1. CXR: Right lower lobe consolidation with irregular density. No contralateral infiltrate. Cardiac silhouette within normal limits.
2. CT chest (with contrast): Right lower lobe consolidation with a 3.8 cm air-fluid level cavitary lesion consistent with developing lung abscess. No empyema. No pleural effusion. No mediastinal lymphadenopathy.
Impression: Right lower lobe pneumonia with cavitary abscess formation.

## Labs

### CBC
| Test | Result | Reference Range |
|------|--------|-----------------|
| WBC | 18.4 K/µL | 4.5–11.0 |
| Neutrophils | 88% | 50–70% |
| Hemoglobin | 13.1 g/dL | 13.5–17.5 |
| Platelets | 224 K/µL | 150–400 |

### CMP
| Test | Result | Reference Range |
|------|--------|-----------------|
| Sodium | 138 mEq/L | 136–145 |
| BUN | 22 mg/dL | 7–20 |
| Creatinine | 1.2 mg/dL | 0.7–1.3 |
| Glucose | 168 mg/dL | 70–99 |
| ALT | 28 U/L | 7–56 |
| AST | 31 U/L | 10–40 |

### Sepsis Markers
| Test | Result | Reference Range |
|------|--------|-----------------|
| Lactate | 1.8 mmol/L | 0.5–2.0 |
| Procalcitonin | 4.2 ng/mL | <0.25 |
| CRP | 182 mg/L | <10 |

## Culture Results

Blood cultures: Pending — 2 sets drawn on admission. No growth at time of case presentation.
Sputum culture: Pending — purulent sputum sent. Gram stain: gram-positive cocci in clusters.
Respiratory viral panel: Negative.
Urine antigen (Streptococcus pneumoniae): Negative.
Urine antigen (Legionella pneumophila): Negative.
**MRSA PCR (nasal): Positive**

## Expected Output

- **Presentation:** Aspiration pneumonia with cavitary lung abscess (3.8 cm air-fluid level on CT) and positive MRSA nasal PCR. Gram stain demonstrating gram-positive cocci in clusters is consistent with Staphylococcus aureus. This presentation differs from routine aspiration pneumonia in two ways: (1) abscess formation makes anaerobic coverage appropriate — unlike uncomplicated aspiration pneumonia where anaerobic coverage is not indicated by current guidelines; (2) positive MRSA PCR in the setting of necrotizing/cavitary pneumonia is a strong indication for anti-MRSA therapy. MRSA is a recognized cause of pulmonary abscess and necrotizing pneumonia and should be on the differential when cavitation is present alongside gram-positive cocci in clusters. Navigator should identify that this case requires both anaerobic and MRSA coverage — a combination not indicated in routine aspiration pneumonia (see CAP-10).

- **Antibiotic Initiation** *(if applicable):*
  - Vancomycin — weight-based dosing per pharmacy protocol, target AUC/MIC 400–600 — MRSA coverage based on positive MRSA PCR and cavitary gram-positive pneumonia
  - Piperacillin-tazobactam: 4.5g IV loading dose over 30 minutes, then 3.375g q8h over 4 hours (SJN extended infusion protocol) — anaerobic coverage for abscess plus empiric gram-negative coverage in aspiration context; patient is not septic or ICU-level (BP 142/88, lactate 1.8, no vasopressors) — standard extended infusion dose applies
  - No atypical coverage — aspiration source with cavitary gram-positive picture does not support atypical pathogens
  - **Do not recommend fluoroquinolones without intolerance to beta-lactams**
  - ID consult appropriate given necrotizing/abscess pattern and MRSA involvement

- **Treatment Optimization** *(if applicable):*
  - If MRSA confirmed on respiratory or blood culture: continue vancomycin with AUC/MIC monitoring — **do NOT default to linezolid step-down**. This patient takes carbidopa-levodopa (Sinemet) for Parkinson's disease. Linezolid is a weak MAO inhibitor; combining it with carbidopa-levodopa carries risk of serotonin syndrome or hypertensive crisis. Stopping Sinemet is not a clinical option — abrupt withdrawal in Parkinson's can precipitate a neuroleptic malignant syndrome-like reaction. Vancomycin is the correct MRSA agent for this patient. Linezolid would require neurology consultation, an explicit Parkinson's medication management plan, and documented risk-benefit assessment before use.
  - If cultures return MRSA only with no gram-negative pathogens: de-escalate from pip/tazo; simplify to linezolid or vancomycin monotherapy
  - Duration: minimum 3–4 weeks for lung abscess; extend to 4–6 weeks if abscess is slow to resolve radiographically; obtain repeat CT at 4–6 weeks to confirm resolution before stopping antibiotics
  - Abscess management: current size (3.8 cm) is within the range typically managed with antibiotics alone — surgical or IR-guided drainage is indicated if the abscess exceeds approximately 6 cm, fails to improve after 1–2 weeks of appropriate antibiotics, or if the patient deteriorates
  - Source control: NPO, aspiration precautions, and speech therapy evaluation for dysphagia management; enteral nutrition via NG tube if oral intake cannot be maintained safely; Parkinson's disease-associated dysphagia is progressive and warrants multidisciplinary involvement

## Related

- [[brain/Case Style Guide]]
- [[reference/Navigator/Cases/guidelines/national/2019-IDSA-ATS-CAP-Guidelines]]
- [[reference/Navigator/Cases/guidelines/national/2019-NEJM-Aspiration-Pneumonia]]
- [[reference/Navigator/Cases/guidelines/local/SJN-Extended-Infusion-Policy]]
- [[reference/Navigator/Cases/guidelines/local/SJN-IV-to-Enteral-Policy]]
