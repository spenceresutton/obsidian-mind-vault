---
date: 2026-05-26
description: "Clinical guidelines and protocols referenced in Navigator sanity test case creation — added on demand"
tags:
  - reference
  - guidelines
  - index
---

# Guidelines & Protocols

Reference material for Navigator sanity test case creation. Guidelines are added on demand — no complete list required upfront.

## Subfolders

| Folder | Contents |
|--------|---------|
| `local/` | St. Joseph Hospital protocols and formulary policies |
| `national/` | IDSA, ASHP, and other national society guidelines |
| `concepts/` | Cross-functional theory: gram-negative resistance, ESBL, AmpC induction, dual beta-lactam coverage, PK/PD principles, etc. |

## Adding a Guideline

Point to any source and run the appropriate ingest step:
- **Google Drive** — use Drive MCP to read and convert
- **Web page** — use `defuddle parse <url> --md` to extract clean markdown
- **Manual paste** — paste content directly, apply frontmatter

Frontmatter schema:

```yaml
---
date: YYYY-MM-DD
description: "one-line summary"
guideline_type: local | national | concept
disease_states: []   # UTI, CAP, SSTI — empty for cross-functional concepts
source_url: ""
tags: [guideline]
---
```

## Ingested Guidelines

### Local (St. Joseph Hospital, Nashua NH)

| Note | Disease | Status |
|------|---------|--------|
| [[reference/Navigator/Cases/guidelines/local/SJN-Inpatient-UTI-Guidelines]] | UTI | Complete |
| [[reference/Navigator/Cases/guidelines/local/SJN-Inpatient-Pneumonia-Guidelines]] | CAP/HAP | Complete |

### National

| Note | Disease | Status |
|------|---------|--------|
| [[reference/Navigator/Cases/guidelines/national/2010-IDSA-Uncomplicated-UTI-Guidelines]] | UTI (uncomplicated) | Complete |
| [[reference/Navigator/Cases/guidelines/national/2010-IDSA-CAUTI-Guidelines]] | UTI (CAUTI) | Complete |
| [[reference/Navigator/Cases/guidelines/national/2019-IDSA-ASB-Guidelines]] | UTI (ASB) | Complete |
| [[reference/Navigator/Cases/guidelines/national/2025-IDSA-Complicated-UTI-Guidelines]] | UTI (complicated) | Partial — CQ4 (imaging) pending |
| [[reference/Navigator/Cases/guidelines/national/2026-CID-Bacterial-Prostatitis-Review]] | Prostatitis | Complete |
| [[reference/Navigator/Cases/guidelines/national/2019-IDSA-ATS-CAP-Guidelines]] | CAP | Complete |
| [[reference/Navigator/Cases/guidelines/national/2016-IDSA-ATS-HAP-VAP-Guidelines]] | HAP/VAP | Complete |
| [[reference/Navigator/Cases/guidelines/national/2019-NEJM-Aspiration-Pneumonia]] | Aspiration | Complete |

## Related

- [[reference/Navigator/Cases/README]] — case library index
- [[brain/Case Style Guide]] — how guidelines inform case generation
