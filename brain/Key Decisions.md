---
date: 2026-05-26
description: "Architectural and workflow decisions worth recalling across sessions — each links to its source work note"
tags:
  - brain
---

# Key Decisions

Architectural or workflow decisions worth recalling. Link to the full [[Decision Record]] when one exists.

---

## Product & GTM

**Apollo standalone has three components** — Apollo Studio (chat-to-plot self-service analytics), White Glove Analytics (flat-file/bespoke reporting), and Ready-to-Deploy MUEs (calcitonin as flagship). The three-part framing is how we sell and how we sequence. See [[Apollo Studio]].

**Apollo Studio positioning: service model** — "We'll do the analytics for you" is the value prop, not a self-serve tool. Calcitonin MUE is the flagship demo use case. See [[Apollo Studio]].

**Pilot training protocol** — Super user training before contract is OK; broad org-wide training only after contract signed. Prevents give-away of training value with no close. See [[Navigator Product]].

**CHOC: pursue clinical outreach, not research re-engagement** — Coordinate with Jordan/Vanessa before any outreach. Research angle is closed; clinical is the path. See [[Navigator Hospital Pipeline]].

**Q2 OKR targets** — $175K expansion revenue, 100% gross retention, 3 Navigator design partnerships closed, 7 Apollo opportunities generated. See [[Q2 2026 OKRs]].

---

## Navigator Case Management

**Navigator Case Management System** — Built 2026-05-26. Five slash commands (`/om-case-ingest`, `/om-case-analyze`, `/om-case-generate`, `/om-case-review`, `/om-case-export`), 16 Spencer-authored approved cases (UTI-01–08, CAP-03–10), Bases view, and [[brain/Case Style Guide]] brain note. Infrastructure lives in `reference/Navigator/Cases/`.

**External folder for non-Spencer cases** — CAP-01 and CAP-02 (Radha-authored) live in `reference/Navigator/Cases/external/` with `status: external`. Their case numbers are reserved. `/om-case-analyze` reads `approved/` only — never `external/`. Style calibration draws exclusively from Spencer's 16 cases.

**Guideline ingestion before case generation** — Spencer directed: ingest the UTI and CAP guidelines the existing cases are based on, re-analyze cases in that context, refine [[brain/Case Style Guide]], then begin generating new cases. Skipping this step risks generating cases that diverge from actual guideline thresholds. Guidelines go to `reference/Navigator/Cases/guidelines/` (local/, national/, concepts/ subfolders).

**National-vs-local divergence is a design feature, not an error** — Cases calibrate to SJN local protocol where it diverges from national guidelines. When a case's empiric coverage appears to contradict a national guideline recommendation, check the local SJN protocol first. The non-severe CAP + 90-day IV abx case (CAP-08) is canonical: IDSA says cultures only for non-severe with this risk factor; SJN empirically adds cefepime + vancomycin. Identifying these divergences is the correct analytical approach for case generation. Spencer confirmed this explicitly on 2026-05-26.

---

## Workspace & Tooling

**obsidian-mind as primary Claude workspace** — Set `~/obsidian-mind` as default Claude Code working directory via `~/.zshrc` alias. All vault context loads at session start. Remote agents (Granola/Gmail/Slack) feed vault via nightly cron; they cannot write local files directly.

**Jira over Asana for task management** — Dual-project Jira setup: STM (tactical, day-to-day) + SPM (strategic, workstreams). Cloud ID: `1de624b6-54fd-4d2e-95c6-508a59f7eb58` on insight-rx.atlassian.net.

**stop-slop as primary writing standard** — Consolidated into `~/.claude/CLAUDE.md`. Overrides any prior protocol where they conflict. No adverbs, no em dashes, no passive voice, no filler. See [[Writing & Document Co-Authoring Protocol]].
