---
date: 2026-05-26
description: "Navigator sanity test case library — approved and pending cases organized by disease state with style-guided generation workflow"
tags:
  - reference
  - index
  - sanity-test
---

# Navigator Sanity Test Cases

Clinical test cases that verify Navigator produces correct outputs before each release. Cases are written or generated then reviewed by the clinical team.

## Commands

| Command | Purpose |
|---------|---------|
| `/om-case-ingest` | Pull cases from the Google Doc and import to `approved/` |
| `/om-case-analyze` | Analyze all approved cases to build or update [[brain/Case Style Guide]] |
| `/om-case-generate` | Generate new cases using style calibration from approved cases |
| `/om-case-review` | Review pending cases — approve or revise before they go live |
| `/om-case-export` | Export approved cases formatted for the Google Doc |

## Folder Structure

```
Cases/
├── approved/     # Vetted cases — style calibration source
├── pending/      # AI-generated cases awaiting review
└── guidelines/
    ├── local/    # St. Joseph protocols (added on demand)
    ├── national/ # IDSA guidelines (added on demand)
    └── concepts/ # Cross-functional theory: gram-negative resistance, ESBL, AmpC, dual beta-lactam
```

## Google Doc Source

File ID: `1x0S5mV4_IvrhFONpMJVz5UJahj6darYBLfLHUEIH2C4`

## Related

- [[brain/Case Style Guide]] — style analysis and challenge archetypes
- [[work/active/Navigator Product]] — broader Navigator product context
- [[reference/Navigator/Cases/guidelines/README]] — guidelines and protocols index
