---
date: 2026-05-26
description: "CAP case — inpatient non-severe community-acquired pneumonia in a healthy adult with no allergies or risk factors"
disease_state: "CAP"
difficulty: easy
author: "Radha"
status: external
case_number: "CAP-01"
challenge_types: [non-severe-CAP, IV-to-PO, duration, de-escalation]
tags:
  - case
  - cap
  - external
source: google-doc
note: "Radha-authored case. Excluded from style calibration. Case number reserved for nomenclature continuity."
---

# CAP Case 1: Inpatient Non-Severe CAP — Healthy Adult, No Allergies, No Comorbidities

**Difficulty:** easy
**Author:** Radha

## Prompt

M.R. is a 66-year-old woman who presents to the general medicine floor with a 3-day history of a productive cough with yellow-green sputum, pleuritic chest pain on the right side, fever to 38.9°C, and fatigue. She denies any recent hospitalization, travel, sick contacts, or antibiotic use in the past year. She is a non-smoker, drinks alcohol occasionally, and has hypothyroidism and is on Synthroid. The ED physician decided to admit based on hypoxia on room air that required supplemental oxygen.

**Allergies:** NKDA

**Weight/Height:** 68 kg, 5'6" (BMI 24)

**Vitals:** Temp 38.9°C | HR 94 | BP 118/74 | RR 22 | SpO2 97% on 2L NC

**Exam:** Dullness to percussion and bronchial breath sounds over right lower lobe. No use of accessory muscles. Alert and oriented x3.

**Labs:** WBC 13.8 (86% neutrophils, no bands), Na 138, K 4.0, Cl 103, CO2 24, BUN 13, SCr 0.5, Glu 91. CrCl ~54 mL/min. Procalcitonin 0.68 ng/mL.

**CXR:** Right lower lobe consolidation consistent with pneumonia. No effusion.

Blood cultures x2 drawn pre-antibiotic. No sputum culture ordered at triage. No prior MRSA or Pseudomonas history. No IV antibiotics in the past 90 days.

## Expected Output

- **Presentation:** Community-acquired pneumonia (CAP), non-severe.
  - Risk factors: None (healthy, no recent healthcare exposure, no prior antibiotic or healthcare contact)
  - Severity: CURB-65 = 2 (RR 22, age <65; no confusion, BUN normal, BP normal); PSI Class II — not severe CAP
  - Clinical flags: Productive cough, fever, lobar infiltrate on CXR. SpO2 92% on RA improving to 96% on 2L. No tachypnea >30, no hypoxia, no altered mental status
  - If applicable, consider Respiratory PCR to rule out viral etiology and de-escalation or discontinuation of antibiotics. Trend Vitals/CBC/PCT — if PCR is positive for virus and clinically stable could consider dropping antibiotics
- **Antibiotic Initiation** *(if applicable):*
  - Preferred: Ceftriaxone 1–2 g IV q24h PLUS Azithromycin 500 mg IV/PO daily (per 2019 IDSA/ATS CAP Guideline, Question 9 — inpatient non-severe, no MRSA/PsA risk factors)
  - Alternative: Levofloxacin 750 mg IV/PO daily (acceptable but not preferred over combination for non-severe inpatient CAP)
  - Duration: Minimum 5 days. Must meet all clinical stability criteria before stopping
  - INCORRECT choices: Piperacillin-tazobactam (excessive spectrum, no MRSA/PsA risk factors); Vancomycin or anti-MRSA coverage (not indicated)
- **Treatment Optimization** *(if applicable):*
  - Stop azithromycin after 3 days if patient is clinically stable (afebrile x24h, HR <100, RR <24, SBP >90 mmHg, SpO2 >90% on RA or chronic baseline O2)
  - De-escalate: if sputum or blood cultures return with a susceptible organism or are negative with improvement, complete 5-day total course of oral antibiotics (amoxicillin-clav, cefdinir, cefpodoxime)
  - Could consider earlier at day 3 for discontinuation of all antibiotics if patient meets all clinical stability criteria
  - Duration: 3-5 days total is sufficient for non-severe inpatient CAP in a patient who achieves clinical stability
  - Follow-up chest imaging: NOT routinely recommended after clinical resolution

## Related

- [[brain/Case Style Guide]]
