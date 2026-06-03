---
date: 2026-05-26
description: "UTI case — asymptomatic bacteriuria with KPC-producing Klebsiella in an elderly LTCF patient with AMS"
disease_state: "UTI"
difficulty: hard
author: "Spencer"
status: approved
case_number: "UTI-06"
challenge_types: [ASB, elderly, KPC, altered-mental-status, pan-resistance]
tags:
  - sanity-test
  - case
  - uti
source: google-doc
---

# UTI Case 6: Asymptomatic Bacteriuria in Elderly

**Difficulty:** hard
**Author:** Spencer

## Prompt

SS is a 78-year-old male with a past medical history significant for hypertension, hyperlipidemia, and type 2 diabetes mellitus who resides in a long-term care facility. He is brought to the emergency department by facility staff after nursing aids noted he was more confused than usual over the past 24 hours. At baseline, the patient is alert and oriented to person, place, and time, and is conversational. On arrival he is oriented to person only, answering questions slowly and inconsistently. He is unable to endorse symptoms further. No recent antibiotic exposure is reported. No fever, rigors, vomiting, or witnessed fall. No focal neurologic deficits are noted on exam. He is not in acute distress.

On arrival vitals: T 37.2°C, HR 84, BP 158/88, RR 16, SpO2 97% on room air. A urinalysis is obtained as part of the AMS workup. Basic labs and a urine culture are sent. Blood cultures are not collected given the absence of systemic signs of infection.

Ht: 5'8"   Wt: 81 kg   BMI: 27.4   Allergies: NKDA

UA with microscopy (straight catheter specimen):

| Test | Result |
|------|--------|
| Color | Yellow, cloudy |
| Specific gravity | 1.026 |
| pH | 6.2 |
| Leukocyte esterase | 2+ |
| Nitrites | Positive |
| WBC | 25 – 50 /hpf |
| RBC | 3 – 5 /hpf |
| Bacteria | Moderate |
| Epithelial cells | Rare |
| Protein | Trace |
| Glucose | 3+ |
| Ketones | Negative |

## Culture Results

Urine culture: Klebsiella pneumoniae >100,000 CFU/mL — KPC-producing carbapenem-resistant organism (CRO). Susceptibilities:

| Antibiotic | Result |
|------------|--------|
| Ampicillin | R |
| Ampicillin-sulbactam | R |
| Piperacillin-tazobactam | R |
| Ceftriaxone | R |
| Cefepime | R |
| Ertapenem | R |
| Meropenem | R |
| Imipenem | R |
| Ceftazidime-avibactam | S |
| Meropenem-vaborbactam | S |
| Colistin | S |
| Gentamicin | I |
| TMP/SMX | R |
| Nitrofurantoin | R |

## Expected Output

- **Presentation:** Asymptomatic bacteriuria
  - Urine cx/colonization does not require treatment (even if resistant)
  - **Avoid being too specific in additional work-up/alternative sources of altered mental status**
  - **Consideration to send the culture for additional susceptibilities (Amikacin) is likely warranted.**
- **Antibiotic Initiation** *(if applicable):*
  - Watch off antibiotics
  - **Realistically the tool shouldn't even offer an "if you would treat". If the user challenges with "we have made the decision to treat, then provide treatment options"**
- **Treatment Optimization** *(if applicable):* N/A

## Related

- [[brain/Case Style Guide]]
- [[reference/Navigator/Cases/guidelines/national/2019-IDSA-ASB-Guidelines]]
- [[reference/Navigator/Cases/guidelines/national/2010-IDSA-CAUTI-Guidelines]]
- [[reference/Navigator/Cases/guidelines/local/SJN-Inpatient-UTI-Guidelines]]
