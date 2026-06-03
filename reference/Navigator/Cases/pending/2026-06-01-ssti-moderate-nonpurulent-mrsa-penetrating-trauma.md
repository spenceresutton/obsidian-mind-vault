---
date: 2026-06-01
description: "SSTI case — nonpurulent soft tissue infection following penetrating nail injury; penetrating trauma is an MRSA risk factor requiring empiric anti-MRSA coverage"
disease_state: "SSTI"
difficulty: medium
author: Claude
status: pending
case_number: "SSTI-03"
challenge_types: [MRSA-risk-penetrating-trauma, nonpurulent-SSTI, empiric-MRSA-coverage]
tags:
  - sanity-test
  - case
  - ssti
source: generated
---

# SSTI Case 3: Nonpurulent SSTI Following Penetrating Trauma

**Difficulty:** medium
**Author:** Claude

## Prompt

SS is a 42-year-old male with no significant past medical history who presents to the emergency department with 3 days of progressive redness, warmth, and swelling around a puncture wound on the dorsum of the right foot. He stepped on a nail at a construction site 6 days ago; the wound bled briefly and appeared to close on its own. He did not seek care at the time. Over the following 3 days, increasing redness and swelling spread outward from the puncture site. He denies purulent drainage. He has no prior MRSA infections and no hospitalizations in the past year.

On arrival, vitals are: T 38.4°C, HR 98, BP 122/76, RR 16, SpO2 98% on room air. The dorsal right foot shows a small puncture wound at the base of the second metatarsal with surrounding erythema extending approximately 5 cm in all directions. The skin is warm, tender, and edematous. No purulence, no drainage, no fluctuance. No crepitus. Borders marked at nursing triage.

**Ht:** 5'10"   **Wt:** 82 kg   **BMI:** 26.4   **Baseline SCr:** 0.8 mg/dL   **Allergies:** NKDA

## Imaging

### X-Ray Right Foot — AP, Lateral, Oblique

1. Soft tissue swelling overlying the dorsal right foot at the level of the second metatarsal base.
2. No radiopaque foreign body identified.
3. Bony structures intact. No cortical destruction, no periosteal reaction, no lucency within the metatarsal or phalangeal bones.
4. No subcutaneous emphysema.
5. Impression: Soft tissue edema at the dorsal right foot consistent with described soft tissue infection. No foreign body or osseous involvement identified. Clinical follow-up for signs of osteomyelitis is recommended if symptoms persist or worsen.

## Labs

### CBC

| Test | Result | Reference Range |
|------|--------|----------------|
| WBC | 12.6 k/µL | 4.5 – 11.0 k/µL |
| Neutrophils (abs.) | 9.8 k/µL | 1.8 – 7.7 k/µL |
| Bands | 7% | < 10% |
| Lymphocytes (abs.) | 1.8 k/µL | 1.0 – 4.8 k/µL |
| Monocytes (abs.) | 0.6 k/µL | 0.2 – 1.0 k/µL |
| RBC | 5.0 M/µL | 4.5 – 5.9 M/µL |
| Hemoglobin | 14.8 g/dL | 13.5 – 17.5 g/dL |
| Hematocrit | 44.6% | 41 – 53% |
| MCV | 89 fL | 80 – 100 fL |
| MCH | 29.6 pg | 27 – 33 pg |
| MCHC | 33.2 g/dL | 32 – 36 g/dL |
| RDW | 13.0% | 11.5 – 14.5% |
| Platelets | 288 k/µL | 150 – 400 k/µL |
| MPV | 9.4 fL | 7.5 – 10.5 fL |

### CMP

| Test | Result | Reference Range |
|------|--------|----------------|
| **Electrolytes** | | |
| Sodium | 138 mEq/L | 136 – 145 mEq/L |
| Potassium | 4.1 mEq/L | 3.5 – 5.1 mEq/L |
| Chloride | 102 mEq/L | 98 – 106 mEq/L |
| CO₂ (bicarb) | 25 mEq/L | 22 – 29 mEq/L |
| BUN | 12 mg/dL | 7 – 20 mg/dL |
| Creatinine | 0.8 mg/dL | 0.7 – 1.3 mg/dL |
| eGFR | > 60 mL/min/1.73m² | > 60 |
| Glucose | 96 mg/dL | 70 – 100 mg/dL |
| **Liver function** | | |
| Total protein | 7.2 g/dL | 6.3 – 8.2 g/dL |
| Albumin | 4.0 g/dL | 3.5 – 5.0 g/dL |
| Total bilirubin | 0.6 mg/dL | 0.2 – 1.2 mg/dL |
| AST | 22 U/L | 10 – 40 U/L |
| ALT | 24 U/L | 7 – 56 U/L |
| Alkaline phosphatase | 68 U/L | 44 – 147 U/L |
| **Minerals** | | |
| Calcium (total) | 9.2 mg/dL | 8.5 – 10.5 mg/dL |

### Sepsis Markers

| Test | Result | Reference Range |
|------|--------|----------------|
| Lactate | 1.5 mmol/L | < 2.0 mmol/L |
| Procalcitonin | 0.44 ng/mL | < 0.25 ng/mL |
| CRP | 68 mg/L | < 10 mg/L |

## Expected Output

- **Presentation:** Nonpurulent SSTI with systemic signs and MRSA risk factor (penetrating trauma) — empiric anti-MRSA coverage indicated
- **Antibiotic Initiation** *(if applicable):* Vancomycin IV. Penetrating trauma is an established MRSA risk factor; empiric anti-MRSA coverage is warranted even in the absence of purulence.
- **Treatment Optimization** *(if applicable):* If wound cultures confirm MSSA (not MRSA), step down to cefazolin IV or cephalexin PO and discontinue vancomycin. When IV-to-PO criteria are met, complete a total 5–10 day course orally. If pain or erythema persist disproportionate to exam findings, reassess for deep space infection or evolving osteomyelitis and consider MRI foot.

**INCORRECT:**
- Cefazolin alone — no MRSA coverage; penetrating trauma is an established MRSA risk factor regardless of purulence

## Related

- [[brain/Case Style Guide]]
- [[reference/Navigator/Cases/guidelines/README]]
