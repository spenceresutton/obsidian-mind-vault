---
description: "Pull cases from the St. Joseph Sanity Test Google Doc and import them into the vault as structured Obsidian notes in reference/Navigator/Cases/approved/."
---

Import Navigator sanity test cases from the Google Doc into the vault.

**Google Doc file ID:** `1x0S5mV4_IvrhFONpMJVz5UJahj6darYBLfLHUEIH2C4`

**Arguments (optional):** Disease state(s) to import (e.g., `UTI`, `CAP`). If none provided, import all disease states found.

$ARGUMENTS

## Steps

1. **Pull the doc** via the Google Drive MCP (`mcp__claude_ai_Google_Drive__read_file_content`). The file is large — spawn a subagent to extract cases rather than loading the full content into main context.

2. **Identify all cases** in the document. Cases are organized by disease state section headers (e.g., `# UTI Cases`, `# Pneumonia Cases`). Each case has:
   - A numbered title (e.g., `UTI Case 1: AmpC Producing...`)
   - Difficulty rating
   - Author (if present)
   - Prompt (clinical scenario)
   - Optional: Culture Results, Imaging, Labs (CBC, CMP, Sepsis Markers as tables)
   - Expected Output (Presentation, Antibiotic Initiation, Treatment Optimization)

3. **Map to disease state.** Infer `disease_state` from the section header:
   - UTI / urinary → `UTI`
   - Pneumonia / CAP / HAP → `CAP`
   - Otherwise use the section header text

4. **Assign case numbers** sequentially per disease state: `UTI-01`, `UTI-02`, `CAP-01`, etc. Check existing `approved/` files first to avoid collisions.

5. **For each case**, create a file at:
   `reference/Navigator/Cases/approved/YYYY-MM-DD-{disease-state-lowercase}-{slug}.md`
   where `YYYY-MM-DD` is today's date and `slug` is a 3–5 word kebab-case title derived from the case title.

6. **Frontmatter** for each file:
   ```yaml
   ---
   date: YYYY-MM-DD
   description: "{disease_state} case — {one-line summary of the clinical challenge}"
   disease_state: "{UTI|CAP|...}"
   difficulty: "{easy|medium|hard}"
   author: "{author if present, else unknown}"
   status: approved
   case_number: "{UTI-01|CAP-01|...}"
   challenge_types: [{inferred challenge types}]
   tags:
     - sanity-test
     - case
     - {disease-state-lowercase}
   source: google-doc
   ---
   ```

   Infer `challenge_types` from the case title and content. Common types:
   `AmpC`, `ESBL`, `KPC`, `ASB`, `bacteremia`, `septic-shock`, `renal-dosing`, `IV-to-PO`, `de-escalation`, `prostatitis`, `pyelonephritis`, `single-dose-aminoglycoside`, `beta-lactam-allergy`, `pregnancy`, `drug-interaction`

7. **Content structure** — preserve all case content verbatim, organized under these headings:
   - `## Prompt`
   - `## Culture Results` (if present)
   - `## Imaging` (if present)
   - `## Labs` with `### CBC`, `### CMP`, `### Sepsis Markers` subsections (if present)
   - `## Expected Output`
   - `## Related` — always include `[[brain/Case Style Guide]]`

8. **After all files are created:**
   - Report a table: case number | disease state | difficulty | challenge types | file path
   - Note any cases that were skipped or could not be parsed
   - Remind Spencer to run `/om-case-analyze` next to build the style guide
