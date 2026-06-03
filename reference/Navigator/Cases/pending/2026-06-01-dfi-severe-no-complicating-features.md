---
date: 2026-06-01
description: "DFI case — severe diabetic foot infection with systemic signs but without osteomyelitis or critical ischemia; broad empiric IV coverage and multi-specialty consultation required"
disease_state: "SSTI"
difficulty: hard
author: Claude
status: pending
case_number: "SSTI-13"
challenge_types: [DFI-severe, systemic-signs, empiric-broad-spectrum, multi-specialty-consult, vascular-consult, extended-infusion]
tags:
  - sanity-test
  - case
  - ssti
  - dfi
source: generated
---

# SSTI Case 13: Severe Diabetic Foot Infection Without Complicating Features

**Difficulty:** hard
**Author:** Claude

## Prompt

SS is a 72-year-old male with a past medical history significant for type 2 diabetes mellitus, peripheral neuropathy, peripheral arterial disease, hypertension, and chronic kidney disease (stage 3a, baseline SCr 1.6 mg/dL) who presents to the emergency department via ambulance after his home health aide found him febrile and lethargic. He has a large non-healing ulcer on the plantar surface of the right foot that has been present for approximately 3 weeks and was being managed with home wound care. His aide reports the wound has been worsening and that he has not been weight-bearing for 2 days due to pain.

On arrival, vitals are: T 38.8°C, HR 112, BP 102/62, RR 22, SpO2 95% on room air. The right foot shows a 4 × 3 cm ulcer at the plantar mid-foot with necrotic tissue at the base and purulent drainage. Erythema extends 6–8 cm beyond the wound margin to the dorsal foot and medial ankle. The foot is warm and edematous to the mid-calf. Probe-to-bone test is negative. No crepitus. No bullae. Posterior tibial and dorsalis pedis pulses are diminished bilaterally.

Blood cultures x2 sets are collected. Wound cultures are sent. He takes metformin, lisinopril, atorvastatin, aspirin, and furosemide. He has no known drug allergies.

**Ht:** 5'7"   **Wt:** 84 kg   **BMI:** 29.3   **Baseline SCr:** 1.6 mg/dL   **Allergies:** NKDA

## Imaging

### X-Ray Right Foot — AP, Lateral, Oblique

1. Extensive soft tissue swelling of the plantar and dorsal right foot and distal ankle.
2. No cortical destruction or irregularity of the metatarsal or tarsal bones.
3. No periosteal reaction identified on plain film.
4. No subcutaneous emphysema or gas within soft tissues.
5. Impression: Significant soft tissue swelling without plain film evidence of osteomyelitis. Clinical correlation and MRI of the right foot should be considered to evaluate for osteomyelitis given the extent of soft tissue infection and diabetic foot ulcer at a pressure point.

## Labs

### CBC

| Test | Result | Reference Range |
|------|--------|----------------|
| WBC | 18.6 k/µL | 4.5 – 11.0 k/µL |
| Neutrophils (abs.) | 15.4 k/µL | 1.8 – 7.7 k/µL |
| Bands | 14% | < 10% |
| Lymphocytes (abs.) | 1.2 k/µL | 1.0 – 4.8 k/µL |
| Monocytes (abs.) | 0.8 k/µL | 0.2 – 1.0 k/µL |
| RBC | 3.9 M/µL | 4.5 – 5.9 M/µL |
| Hemoglobin | 11.4 g/dL | 13.5 – 17.5 g/dL |
| Hematocrit | 34.2% | 41 – 53% |
| MCV | 87 fL | 80 – 100 fL |
| MCH | 29.2 pg | 27 – 33 pg |
| MCHC | 33.3 g/dL | 32 – 36 g/dL |
| RDW | 14.8% | 11.5 – 14.5% |
| Platelets | 164 k/µL | 150 – 400 k/µL |
| MPV | 10.6 fL | 7.5 – 10.5 fL |

### CMP

| Test | Result | Reference Range |
|------|--------|----------------|
| **Electrolytes** | | |
| Sodium | 134 mEq/L | 136 – 145 mEq/L |
| Potassium | 4.8 mEq/L | 3.5 – 5.1 mEq/L |
| Chloride | 98 mEq/L | 98 – 106 mEq/L |
| CO₂ (bicarb) | 20 mEq/L | 22 – 29 mEq/L |
| BUN | 34 mg/dL | 7 – 20 mg/dL |
| Creatinine | 2.2 mg/dL | 0.7 – 1.3 mg/dL |
| eGFR | 32 mL/min/1.73m² | > 60 |
| Glucose | 296 mg/dL | 70 – 100 mg/dL |
| **Liver function** | | |
| Total protein | 6.4 g/dL | 6.3 – 8.2 g/dL |
| Albumin | 2.9 g/dL | 3.5 – 5.0 g/dL |
| Total bilirubin | 0.8 mg/dL | 0.2 – 1.2 mg/dL |
| AST | 36 U/L | 10 – 40 U/L |
| ALT | 28 U/L | 7 – 56 U/L |
| Alkaline phosphatase | 92 U/L | 44 – 147 U/L |
| **Minerals** | | |
| Calcium (total) | 8.2 mg/dL | 8.5 – 10.5 mg/dL |

### Sepsis Markers

| Test | Result | Reference Range |
|------|--------|----------------|
| Lactate | 2.8 mmol/L | < 2.0 mmol/L |
| Procalcitonin | 3.4 ng/mL | < 0.25 ng/mL |
| CRP | 142 mg/L | < 10 mg/L |

| HbA1c | 10.8% | < 5.7% |

## Expected Output

- **Presentation:** Severe diabetic foot infection with systemic signs (SIRS criteria met) — no osteomyelitis on plain film, no critical ischemia, no crepitus; broad empiric IV coverage and multi-specialty consultation required
- **Antibiotic Initiation** *(if applicable):* Vancomycin IV (AUC-guided dosing; pharmacist to adjust — Cr 2.2, eGFR 32, acutely elevated from baseline 1.6) + Piperacillin-tazobactam 3.375g IV q8h over 4 hours extended infusion per SJN standard protocol (note: eGFR 32, which is above the SJN CrCl <20 threshold for q12h dosing; standard extended infusion dose applies). **Vascular consult recommended** (diminished pedal pulses bilaterally, known PAD, DFI). **Podiatry consult** (wound debridement, assessment, offloading). **Surgical consult** (assess need for operative debridement).
- **Treatment Optimization** *(if applicable):* MRI right foot to evaluate for osteomyelitis given plain film limitations in early osteomyelitis. Narrow antibiotics based on wound/blood culture results. Duration for severe DFI without osteomyelitis: typically 2–4 weeks based on clinical response. Reassess renal function and vancomycin levels daily given acute-on-chronic kidney injury.

**INCORRECT:**
- Narrow-spectrum cefazolin or cephalexin alone — severe DFI with systemic signs requires broad empiric coverage including MRSA and gram-negative pathogens including anaerobes
- Standard pip/tazo 30-minute infusion — SJN default is extended infusion (4h); this patient does not meet the septic shock threshold for the escalated 4.5g q8h dose but standard extended infusion (3.375g q8h over 4h) applies
- Omitting vascular consult — diminished pedal pulses in a patient with known PAD and severe DFI represents a limb-threatening situation; vascular assessment is required

## Related

- [[brain/Case Style Guide]]
- [[reference/Navigator/Cases/guidelines/README]]
- [[reference/Navigator/Cases/guidelines/local/SJN-Extended-Infusion-Policy]]
