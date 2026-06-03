---
description: "Generate a new Navigator sanity test case using style calibration from approved cases and available guidelines. Saves to pending/ for review."
---

Generate a new Navigator sanity test case.

**Arguments:** `{disease_state} {difficulty} {challenge_type(s)} [guideline hint]`

Examples:
- `UTI hard ESBL renal-dosing`
- `CAP medium beta-lactam-allergy`
- `UTI easy uncomplicated-cystitis`

$ARGUMENTS

## Steps

1. **Parse arguments.** Extract:
   - `disease_state` — required (e.g., UTI, CAP, SSTI)
   - `difficulty` — required (easy, medium, hard)
   - `challenge_types` — one or more challenge archetypes
   - `guideline_hint` — optional reference to a specific guideline or concept

   If arguments are missing or ambiguous, ask before proceeding.

2. **Load style calibration:**
   - Read `brain/Case Style Guide.md` in full
   - Read the 3–5 most recent `approved/` cases matching the requested `disease_state` (by frontmatter `disease_state` field). If fewer than 3 exist for that disease state, supplement with cases from other disease states.
   - Use these as voice and structure references, not content sources.

3. **Load relevant guidelines** from `reference/Navigator/Cases/guidelines/`:
   - Search `local/` and `national/` for files whose `disease_states` frontmatter matches the requested disease state
   - Search `concepts/` for files relevant to the requested challenge types
   - Read any matching files and use them to inform clinical accuracy

4. **Determine case number.** Scan `approved/` and `pending/` for the highest existing case number for this disease state (e.g., `UTI-08`). Assign the next number.

5. **Generate the case.** Write a complete clinical vignette that:
   - Opens with patient initials "SS" per Spencer's convention, then age, sex, PMH, presentation
   - Includes enough detail in the Prompt that no follow-up questions are needed
   - Contains Culture Results, Imaging, and Labs tables as appropriate for the challenge (not every section is required for every case)
   - Has an Expected Output that specifies drug + dose + route + duration + guideline citation where applicable
   - Flags wrong-answer traps explicitly if the challenge type warrants it
   - Matches the difficulty level per the calibration criteria in `brain/Case Style Guide.md`

6. **Save to `reference/Navigator/Cases/pending/`** with filename:
   `YYYY-MM-DD-{disease-state-lowercase}-{slug}.md`

   Frontmatter:
   ```yaml
   ---
   date: {today}
   description: "{disease_state} case — {one-line summary}"
   disease_state: "{disease_state}"
   difficulty: "{difficulty}"
   author: Claude
   status: pending
   case_number: "{DISEASE-NN}"
   challenge_types: [{challenge_types}]
   tags:
     - sanity-test
     - case
     - {disease-state-lowercase}
   source: generated
   ---
   ```

7. **Present the case** in full to Spencer. Note:
   - Which approved cases were used for calibration
   - Which guidelines were referenced
   - Any clinical decisions made that Spencer should validate (organism selection, dosing rationale, guideline citation)

8. **Do not auto-approve.** Wait for Spencer to run `/om-case-review` or explicitly say "approve this case."
