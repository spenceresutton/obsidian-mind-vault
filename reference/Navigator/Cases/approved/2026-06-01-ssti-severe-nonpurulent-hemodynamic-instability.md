---
date: 2026-06-01
description: "SSTI case — rapidly spreading nonpurulent cellulitis progressing to septic shock requiring vasopressor support; ICU admission with broad empiric coverage required"
disease_state: "SSTI"
difficulty: hard
author: Spencer
status: approved
case_number: "SSTI-05"
challenge_types: [severe-SSTI, septic-shock, hemodynamic-instability, ICU-care, empiric-broad-spectrum, extended-infusion]
tags:
  - sanity-test
  - case
  - ssti
source: generated
---

# SSTI Case 5: Nonpurulent SSTI with Septic Shock

**Difficulty:** hard
**Author:** Spencer

## Prompt

SS is a 67-year-old male with a past medical history significant for coronary artery disease (s/p PCI 4 years ago), type 2 diabetes mellitus, and hypertension who presents via EMS after his spouse called 911 for acute-onset confusion and inability to bear weight on the right leg. Over the preceding 36 hours, he developed rapidly worsening redness, swelling, and pain in the right lower extremity. He had no systemic symptoms initially, but his spouse reports he became increasingly confused and lethargic over several hours before the call.

On arrival to the ED, vitals are: T 39.3°C, HR 132, BP 78/46, RR 26, SpO2 92% on room air. He is placed on 2L nasal cannula with improvement to 95%. Aggressive fluid repletion was initiated, but due to inability to maintain MAP above 65, norepinephrine was initiated. Blood cultures x2 sets are collected and the patient is transferred to the ICU.

On ICU arrival, vitals are: T 38.8°C (rectal), HR 116, BP 92/54 (MAP 67 on NE 0.08 mcg/kg/min), RR 22, SpO2 95% on 2L NC.

SS appears acutely ill and in moderate distress. He is diaphoretic and restless. The right lower extremity shows extensive erythema from the dorsal foot to the proximal thigh with advancing borders; the skin is warm, tense, and tender throughout with 3+ dependent edema to the knee. Streaking lymphangitis extends from the medial calf toward the inguinal region. No crepitus is palpable. No bullae, skin necrosis, or progressive discoloration is present. He is alert and oriented to person and place but unable to recall the date; he follows commands appropriately.

He takes aspirin, metoprolol succinate, atorvastatin, metformin, and lisinopril.

**Ht:** 5'9"   **Wt:** 91 kg   **BMI:** 29.9   **Baseline SCr:** 1.0 mg/dL   **Allergies:** NKDA

## Imaging

### X-Ray Right Lower Extremity — AP

1. Extensive soft tissue edema and swelling of the right lower extremity, most pronounced at the medial calf extending to the mid-thigh.
2. No subcutaneous emphysema or gas within soft tissue planes identified on this projection.
3. No radiopaque foreign body.
4. No periosteal reaction or cortical destruction of the tibia or fibula.
5. Impression: Diffuse soft tissue swelling consistent with described soft tissue infection. No gas-forming infection identified on plain film. CT of the right lower extremity should be obtained if clinical suspicion for necrotizing fasciitis persists despite negative plain films.

## Labs

### CBC

| Test | Result | Reference Range |
|------|--------|----------------|
| WBC | 22.4 k/µL | 4.5 – 11.0 k/µL |
| Neutrophils (abs.) | 19.8 k/µL | 1.8 – 7.7 k/µL |
| Bands | 18% | < 10% |
| Lymphocytes (abs.) | 0.8 k/µL | 1.0 – 4.8 k/µL |
| Monocytes (abs.) | 0.6 k/µL | 0.2 – 1.0 k/µL |
| RBC | 4.2 M/µL | 4.5 – 5.9 M/µL |
| Hemoglobin | 12.8 g/dL | 13.5 – 17.5 g/dL |
| Hematocrit | 38.4% | 41 – 53% |
| MCV | 91 fL | 80 – 100 fL |
| MCH | 30.5 pg | 27 – 33 pg |
| MCHC | 33.4 g/dL | 32 – 36 g/dL |
| RDW | 13.8% | 11.5 – 14.5% |
| Platelets | 144 k/µL | 150 – 400 k/µL |
| MPV | 10.2 fL | 7.5 – 10.5 fL |

### CMP

| Test | Result | Reference Range |
|------|--------|----------------|
| **Electrolytes** | | |
| Sodium | 132 mEq/L | 136 – 145 mEq/L |
| Potassium | 5.2 mEq/L | 3.5 – 5.1 mEq/L |
| Chloride | 98 mEq/L | 98 – 106 mEq/L |
| CO₂ (bicarb) | 18 mEq/L | 22 – 29 mEq/L |
| BUN | 28 mg/dL | 7 – 20 mg/dL |
| Creatinine | 1.8 mg/dL | 0.7 – 1.3 mg/dL |
| eGFR | 42 mL/min/1.73m² | > 60 |
| Glucose | 244 mg/dL | 70 – 100 mg/dL |
| **Liver function** | | |
| Total protein | 6.2 g/dL | 6.3 – 8.2 g/dL |
| Albumin | 2.8 g/dL | 3.5 – 5.0 g/dL |
| Total bilirubin | 1.0 mg/dL | 0.2 – 1.2 mg/dL |
| AST | 44 U/L | 10 – 40 U/L |
| ALT | 38 U/L | 7 – 56 U/L |
| Alkaline phosphatase | 84 U/L | 44 – 147 U/L |
| **Minerals** | | |
| Calcium (total) | 7.8 mg/dL | 8.5 – 10.5 mg/dL |

### Sepsis Markers

| Test | Result | Reference Range |
|------|--------|----------------|
| Lactate | 4.8 mmol/L | < 2.0 mmol/L |
| Procalcitonin | 14.2 ng/mL | < 0.25 ng/mL |
| CRP | 168 mg/L | < 10 mg/L |

*Resulted: ICU admission day*

## Expected Output

- **Presentation:** Nonpurulent SSTI with septic shock requiring vasopressor support
- **Antibiotic Initiation** *(if applicable):* Vancomycin IV + Piperacillin-tazobactam 4.5g IV loading dose over 30 min, then 4.5g IV q8h over 4 hours extended infusion + Clindamycin 900 mg IV q8h. Do not delay antibiotics for CT or surgical consultation.
- **Treatment Optimization** *(if applicable):*
    - If necrotizing fasciitis cannot be excluded on clinical grounds despite negative plain film, obtain CT right lower extremity and surgical consultation.
    - If cultures return with a targetable organism, narrow the spectrum accordingly.
    - Discontinue clindamycin if necrotizing fasciitis is excluded, or infection is not confirmed to be *Streptococcus pyogenes* or *Clostridium* spp.
    - Treatment should continue for at least 5 days and through clinical improvement. Reasonable to extend course to 10–14 days if slow improvement.
    - If necrotizing fasciitis is identified, 2–4 weeks of therapy may be warranted.

## Related

- [[brain/Case Style Guide]]
- [[reference/Navigator/Cases/guidelines/README]]
- [[reference/Navigator/Cases/guidelines/local/SJN-SSTI-Guidelines]]
- [[reference/Navigator/Cases/guidelines/local/SJN-Extended-Infusion-Policy]]
