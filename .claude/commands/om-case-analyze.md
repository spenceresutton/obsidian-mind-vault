---
description: "Analyze all approved Navigator sanity test cases to build or update brain/Case Style Guide.md — the style calibration source for case generation."
---

Analyze all approved Navigator sanity test cases and write a comprehensive style guide to `brain/Case Style Guide.md`.

## Steps

1. **Read all approved cases** from `reference/Navigator/Cases/approved/` only. Do NOT include files from `reference/Navigator/Cases/external/` — those are non-Spencer-authored cases excluded from style calibration. Use QMD first: `qmd --index obsidian-mind vsearch "sanity test case approved"`, filtering to `approved/` path only. Fall back to Glob if QMD unavailable.

2. **Read all guidelines** from `reference/Navigator/Cases/guidelines/` (all subfolders). Note which are present; the style guide should reflect available reference material.

3. **Analyze each case across these dimensions:**

   **Structure patterns**
   - Which sections appear in all cases vs. optionally
   - Lab panel conventions (what CBC/CMP/sepsis markers are always included vs. situational)
   - Table formatting conventions
   - Prompt verbosity and detail level (what patient info is always vs. sometimes included)
   - Expected Output specificity (how prescriptive — drug + dose + route + duration + guideline, or looser)

   **Difficulty calibration**
   - What distinguishes Easy from Medium from Hard in practice
   - Document concrete criteria per difficulty level with examples from the cases

   **Challenge archetype taxonomy**
   - Catalog every distinct type of challenge present across all cases
   - For each archetype: what clinical concept is being tested, example case(s), what a wrong answer looks like
   - Note cross-disease archetypes (e.g., renal dosing applies to UTI and CAP both)

   **Anti-patterns** (explicit "do not do" conventions from Expected Output notes)
   - Language to avoid (e.g., "foul smelling urine")
   - Clinical traps to flag but not fall into (ASB → no reflexive treatment)
   - Over-specification pitfalls

   **Spencer's voice markers**
   - How clinical scenarios are constructed (patient initials "SS", consistent demographic patterns)
   - Tone in Expected Output (direct, evidence-anchored, flags traps explicitly)
   - Level of clinical nuance expected in outputs

4. **Write `brain/Case Style Guide.md`** with the following structure:

   ```
   ## Structure Conventions
   ## Difficulty Calibration
   ## Challenge Archetype Taxonomy
   ## Anti-Patterns
   ## Voice & Style
   ## Cross-Disease Transfer Notes
   ```

   Use tables where helpful. Be specific — quote verbatim examples from cases where illustrative.

5. **Update `brain/Memories.md`** to add a pointer to `[[brain/Case Style Guide]]` if not already present.

6. **Report:** a summary of what was analyzed (case count by disease state) and the key findings (challenge archetypes found, anti-patterns documented, difficulty criteria defined).
