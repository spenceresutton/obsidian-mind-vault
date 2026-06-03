---
date: 2026-06-01
description: "DFI case — diabetic foot osteomyelitis with positive surgical bone margins following minor amputation; extended antibiotic course (6 weeks) required for residual infected bone with culture-directed oral step-down"
disease_state: "SSTI"
difficulty: hard
author: Claude
status: pending
case_number: "SSTI-15"
challenge_types: [DFI-osteomyelitis, positive-surgical-margins, duration-of-therapy, oral-step-down, MSSA, multi-specialty-consult]
tags:
  - sanity-test
  - case
  - ssti
  - dfi
source: generated
---

# SSTI Case 15: Diabetic Foot Osteomyelitis — Positive Bone Margins Post-Amputation

**Difficulty:** hard
**Author:** Claude

## Prompt

SS is a 65-year-old male with a past medical history significant for type 2 diabetes mellitus, peripheral neuropathy, peripheral arterial disease, and stage 3b CKD (baseline SCr 1.9 mg/dL) who underwent a left second toe amputation 8 days ago for a diabetic foot ulcer with osteomyelitis confirmed on pre-operative MRI. A bone biopsy sent at the time of surgery grew MSSA (methicillin-susceptible Staphylococcus aureus). He was on cefazolin IV post-operatively and was transitioned to cephalexin at discharge 3 days ago. He now returns to the outpatient wound care clinic for his first post-operative visit.

On examination, the amputation site shows mild erythema at the wound edges with scant serous drainage. No purulence, no dehiscence, no fluctuance. The remainder of the left foot appears stable. He denies fever, chills, or systemic symptoms. Vitals are: T 36.8°C, HR 78, BP 136/84, RR 14, SpO2 96% on room air.

Pathology report from the amputation specimen, finalized yesterday: **Osteomyelitis present at the surgical bone margins (proximal and medial) of the second metatarsal.** He has no known drug allergies.

**Ht:** 5'8"   **Wt:** 88 kg   **BMI:** 29.9   **Baseline SCr:** 1.9 mg/dL   **Allergies:** NKDA

## Imaging

### MRI Left Foot with and without Contrast (Pre-operative, 14 days prior)

1. Osteomyelitis of the second toe proximal phalanx with extension into the second metatarsal head — marrow signal abnormality and cortical destruction present.
2. Surrounding soft tissue edema and phlegmon at the second toe and dorsal forefoot.
3. No deep space abscess.
4. Plantar fascia intact.
5. Impression: Osteomyelitis of the second toe and second metatarsal head consistent with diabetic foot osteomyelitis. No discrete abscess.

### X-Ray Left Foot Post-Operative — AP, Lateral (Obtained at today's visit)

1. Post-operative changes consistent with second toe amputation; second metatarsal shaft is intact.
2. Lytic changes with irregular cortical margins at the residual second metatarsal head and neck — appearance consistent with residual osteomyelitis in the setting of positive pathologic margins.
3. No periosteal reaction or new cortical destruction at the remaining metatarsals or phalanges.
4. Soft tissue swelling at the amputation site without subcutaneous gas.
5. Impression: Residual lytic changes at the second metatarsal consistent with osteomyelitis at the surgical margin. Correlation with pathology (positive margins) and clinical assessment recommended to guide antibiotic duration.

## Culture Results

Pre-operative bone biopsy — left second toe / second metatarsal head (obtained in OR):

| Organism | Staphylococcus aureus — methicillin-susceptible (MSSA) |
|---|---|

| Antibiotic | Result |
|---|---|
| Oxacillin | S |
| Nafcillin | S |
| Cefazolin | S |
| Cephalexin | S |
| TMP-SMX | S |
| Clindamycin | S |
| Ciprofloxacin | S |
| Rifampin | S |
| Vancomycin | S |

## Labs

| Test | Result | Reference Range |
|------|--------|----------------|
| WBC | 9.2 k/µL | 4.5 – 11.0 k/µL |
| Neutrophils (abs.) | 6.4 k/µL | 1.8 – 7.7 k/µL |
| Hemoglobin | 11.2 g/dL | 13.5 – 17.5 g/dL |
| Platelets | 248 k/µL | 150 – 400 k/µL |
| Creatinine | 2.1 mg/dL | 0.7 – 1.3 mg/dL |
| eGFR | 34 mL/min/1.73m² | > 60 |
| Glucose | 146 mg/dL | 70 – 100 mg/dL |
| HbA1c | 8.4% | < 5.7% |
| CRP | 28 mg/L | < 10 mg/L |
| ESR | 64 mm/hr | < 20 mm/hr |

## Expected Output

- **Presentation:** Diabetic foot osteomyelitis with positive surgical bone margins following second toe amputation — residual infected bone confirmed on pathology; extended antibiotic course is required
- **Antibiotic Initiation** *(if applicable):* Patient is currently on cephalexin PO (appropriate oral step-down for MSSA osteomyelitis). Continue cephalexin 1g PO QID (or dicloxacillin 500 mg PO QID) for MSSA coverage. Oral agents with high bioavailability and bone penetration are appropriate for ambulatory management of chronic osteomyelitis once systemic signs have resolved.
- **Treatment Optimization** *(if applicable):* **Total antibiotic duration: 6 weeks from the date of the last surgery (amputation date).** Positive bone margins establish that residual infected bone remains; the 6-week course counts from the most recent surgical procedure, not from presentation. **Vascular consult recommended** — peripheral arterial disease with positive bone margins carries a higher risk of treatment failure and progression; vascular status should guide re-resection planning. **Podiatry consult** for ongoing wound care and offloading. **Surgical consult** — positive margins should prompt a discussion about re-resection of residual infected bone vs. prolonged antibiotics as definitive management. **ID consult recommended** for complex diabetic foot osteomyelitis management. ESR and CRP should be followed as markers of treatment response.

**INCORRECT:**
- Short-course antibiotics (less than 6 weeks) — positive bone margins indicate residual osteomyelitis; standard short-course therapy is reserved for patients with negative margins after resection
- Vancomycin IV — organism is MSSA; vancomycin is inferior to beta-lactams for MSSA osteomyelitis; IV therapy is not required if the patient is clinically stable on an appropriate oral agent
- Rifampin monotherapy or rifampin addition without clear indication — rifampin-containing combination regimens are primarily for implant-associated bone/joint infections; not standard for DFI osteomyelitis without a retained foreign body *(Spencer: flag for validation — some ID practitioners add rifampin to MSSA osteomyelitis regimens empirically; confirm SJN practice)*
- Omitting vascular consult — PAD with positive osteomyelitis margins in a diabetic patient is a high-risk combination for treatment failure; vascular assessment is required

## Related

- [[brain/Case Style Guide]]
- [[reference/Navigator/Cases/guidelines/README]]
