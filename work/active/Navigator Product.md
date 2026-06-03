---
date: 2026-05-18
description: "IRX Navigator product development — tiger team meetings, platform features, bug fixes, testing framework, and clinical guideline integration status"
tags:
  - work-note
  - active
status: active
quarter: Q2-2026
---

# Navigator Product

Internal tracking for IRX Navigator product development, tiger team meetings, platform progress, and clinical validation work. Separate from sales pipeline (see [[Navigator Hospital Pipeline]]).

---

## Platform Status (as of 2026-05-19)

- **Active design partner:** St. Joseph Hospital (weekly Tue 1pm ET meetings)
- **Speed optimization:** Primary bottleneck — Paolo reassigned from Apollo to Navigator
- **Testing framework:** LLM-as-judge system being implemented (Opus for judging, Sonnet for production)
- **Literature:** Primary ASP literature added; citation accuracy issues under review
- **New features:** Chat history, Rooms system (read/write access per patient), session persistence

---

## Update — 2026-05-18 (Tiger Team — St. Joseph Sync)

Weekly sync with Nick Cotoia, Tiffany Lee, Vanessa. Nick returned from travel; limited testing done but SSO resolved.

**Action Items:**
- [ ] Nick: Provide guideline approval after P&T committee meeting 5/21
- [ ] Team: Continue speed optimization and bug fixes
- [ ] Spencer: Available for clinical questions via text/email

**Key Points:**
- Speed is primary concern from St. Joseph feedback
- Loading states improved (show reasoning steps in progress); overall optimization still in development
- Queuing feature planned: allow leaving and returning to chat responses
- Bug fixes: cefepime recommendation error resolved; duration range specificity improved
- SSTI guidelines ready pending Nick's approval; C. diff pending P&T committee
- P&T committee meeting 5/21: fidaxomicin restriction debate; linezolid/ceftaroline restrictions likely unchanged
- Formulary integration: default recommendations will be on-formulary; off-formulary options available via chat

---

## Update — 2026-05-19 (Bi-weekly Navigator Tiger Team)

Full tiger team with Radha, Luke Lashley, Vanessa, Tiffany, Gustavo Maurina, Sirj Goswami, Lavanya Elangovan.

**Action Items:**
- [ ] Paolo: Complete automated testing framework setup this week
- [ ] Luke: Update literature integration status; implement LLM-as-judge system
- [ ] Spencer: Add soft tissue and C-diff test cases as available; validate LLM scoring
- [ ] Tiffany: Validate LLM-as-judge responses alongside Spencer
- [ ] Team: Test free chat with new literature; evaluate module vs chat workflow clarity
- [ ] Vanessa: Circulate new UI design by end of week

**Key Points:**
- Paolo reassigned from Apollo to Navigator (completed Studio drug modules OKR early) — focus on testing framework
- Automated testing: Spencer's UTI + pneumonia test cases ready; C-diff pending St. Joseph restriction discussions
- LLM-as-judge: each case run 4–5 times for consistency; numerical scores + text descriptions; traces in Langsmith
- Luke's agent refactoring in progress — testing framework prevents performance regression
- Rooms system: one primary user (write access) per patient; additional users read-only with real-time streaming
- Chat history: multiple users can access same patient; new chat spawned when primary user switches
- Citation accuracy concerns: agent citing papers from review docs without full context; need clinical team review of guideline hierarchies
- Outdated guideline conflicts (UTI duration recommendations) identified — needs resolution

---

## Update — 2026-05-26 (Case Management System Build)

Built the Navigator Sanity Test Case Management System end-to-end during this session.

**Completed:**
- Imported all 16 Spencer-authored sanity test cases from St. Joseph Google Doc into `reference/Navigator/Cases/approved/` (UTI-01–08, CAP-03–10)
- Moved Radha-authored CAP-01 and CAP-02 to `reference/Navigator/Cases/external/` — reserved for nomenclature, excluded from calibration
- Created `brain/Case Style Guide.md` via `/om-case-analyze`: 17 challenge archetypes, 10 anti-patterns, prompt narrative arc, lab calibration rules, red herring taxonomy
- Built 5 slash commands: `/om-case-ingest`, `/om-case-analyze`, `/om-case-generate`, `/om-case-review`, `/om-case-export`
- Created Bases view (`Case Library.base`) with All Cases / Approved / Pending Review filter views
- Fixed structural inconsistencies: UTI-01 UA placement, UTI-07 Treatment Optimization placeholder, CAP-08/09/10 numbering collision

**Pending (next session):**
- [ ] Spencer: Provide UTI and CAP guideline sources (Google Drive links or web URLs)
- [ ] Ingest guidelines to `reference/Navigator/Cases/guidelines/` (local/ or national/ subfolder)
- [ ] Re-run `/om-case-analyze` with guidelines in scope — refine challenge archetype taxonomy against actual guideline thresholds
- [ ] Begin case generation phase once style guide is grounded in guidelines

---

## Update — 2026-05-26 (Guideline Ingestion Phase)

Ingested all national and local clinical guidelines underpinning the UTI and CAP sanity test cases.

**Completed:**
- 2019 IDSA/ATS CAP Guidelines (Metlay et al.) — all 16 questions fully documented; MRSA/Pseudo risk framework, severity stratification, aspiration guidance, duration
- 2016 IDSA/ATS HAP/VAP Guidelines (Kalil et al.) — HCAP abolished, 7-day duration, MDR risk factors, de-escalation, pathogen-specific therapy
- 2019 NEJM Aspiration Pneumonia Review (Mandell & Niederman) — anaerobe shift, treatment algorithm by acquisition site, chemical pneumonitis distinction
- SJN Local CAP Protocol — flowchart extracted from PDF visual rendering; corrected regimens for all four CAP severity/risk branches; key divergence from national: SJN empirically covers MRSA + Pseudo for non-severe CAP with 90-day IV abx risk (national guideline: cultures only)
- 2010 IDSA/ESCMID Uncomplicated UTI Guidelines (Gupta et al.)
- 2025 IDSA Complicated UTI Guidelines
- SJN Local UTI Protocol (P&T Approved 12/2025) — full coverage of ASB, uncomplicated cystitis, complicated UTI, CAUTI; all empiric and culture-defined options with doses, durations, restriction notes

**Key Insight Confirmed (Spencer):** Cases calibrate to SJN local protocol where it diverges from national guidelines. National-vs-local divergences are intentional case design features — identifying them is the correct analytical approach for case generation. The non-severe CAP + 90-day IV abx case (CAP-08) is the canonical example.

**Pending:**
- [ ] Ingest Kulkarni et al. 2026 CID prostatitis review (at `/Users/spencersutton/Downloads/State of the Art Review Diagnosis and Management of.pdf`) — relevant for UTI-08
- [ ] Spencer: Provide IDSA 2019 ASB guideline (Nicolle et al.) PDF if needed
- [ ] Run guideline-contextualized `/om-case-analyze` — refine challenge archetype taxonomy against actual guideline thresholds
- [ ] Begin `/om-case-generate` for new UTI edge cases once style guide is refined

---

## Platform Features (Current)

| Feature | Status |
|---|---|
| Patient flagging / prioritization | Live |
| Two-way chat with clinical reasoning | Live |
| Inline citations + source links | Live |
| Glass box reasoning steps | Live |
| One-click EHR ordering | In development (Epic integration) |
| Chat history / multi-user rooms | Live (Gustavo) |
| LLM-as-judge testing framework | In development (Luke/Paolo) |
| Voice transcription | Live but NOT PHI-compliant yet |
| Speed optimization | In progress (Paolo) |
| Queuing feature | Planned |
| New UI design | In progress (Vanessa) |

## Clinical Guidelines (St. Joseph)

| Guideline | Status |
|---|---|
| UTI | Integrated |
| Pneumonia | Integrated |
| SSTI | Ready — awaiting Nick approval |
| C. diff | Awaiting P&T committee decision (5/21) |

---

## Related

- [[St. Joseph Hospital (Nashua, NH)]]
- [[Navigator Hospital Pipeline]]
- [[Apollo Studio]]
