---
date: 2026-05-26
description: "Recurring patterns and conventions discovered across work — architecture, naming, tooling, and implementation patterns"
tags:
  - brain
---

# Patterns

Recurring patterns discovered across work. Update when something repeats three or more times.

---

## Navigator Sales Patterns

**IT security is the slowest gate** — Every [[Navigator Hospital Pipeline|Navigator]] deal stalls at IT security review. Start the IT conversation early, before clinical buy-in is complete. Get the AI committee process and informatics contact identified at the first follow-up meeting.

**Price range unlocks leadership approval** — Prospects rarely escalate internally until they have a number. Surface the range early; it converts curiosity into a real budget conversation.

**EHR compatibility shapes urgency** — Hospitals on Epic + Cerner with existing InsightRX integrations move faster. Pending EHR migrations (e.g., [[WMC Health]] Epic migration late 2027) create urgency or pause depending on timing.

**Speed is the top clinical complaint** — Clinicians consistently cite alert fatigue and slow decision support as pain points. Lead demos with speed and specificity; show time-to-recommendation in real workflows. See [[Navigator Product]].

**C. diff and AMS gaps are the most common immediate pain points** — When a prospect has an active problem (C. diff cluster, AUC below target, vancomycin protocol gaps), close in on it fast. Specificity beats general value prop every time.

---

## Apollo Patterns

**POC-first, then broad rollout** — [[Apollo Studio]] closes when there's a concrete use case on the table. Anchor the POC to a specific question the buyer already wants answered.

**"We'll do the analytics for you" beats self-serve** — Buyers respond to the service-model framing. Don't lead with platform; lead with the output they'll get.

---

## Navigator Case Development Patterns

**Academic journal URLs fail — use PDFs directly** — WebFetch returns wrong content for academic journal URLs (Oxford, PMC, PubMed) due to CDN routing. Pattern: Spencer provides PDFs from Desktop/Downloads; extract via `pdftotext <path> -` in Bash. For embedded image tables or flowcharts (common in hospital protocols), also run `pdftoppm -r 150 <path> /tmp/prefix` then read the rendered images with the Read tool.

**SJN guidelines have flowcharts, not text tables** — The SJN CAP protocol (and likely other hospital protocols) embed treatment algorithms as images inside the Word/PDF document, not as extractable table cells. python-docx will return empty tables. Always render to images and visually parse for local hospital protocols.

**Load national + local guidelines in generation; local governs divergences** — When generating cases for a specific institution, the local protocol takes precedence where it conflicts with national guidelines. Build this two-layer check into any case review or generation prompt. See [[brain/Key Decisions]] for the canonical non-severe CAP example.

---

## Patterns to Watch

- Whether antibiogram use cases (static vs. real-time) convert into standalone [[Apollo Studio]] opportunities
- Whether physician risk-tolerance framing (qualitative vs. probabilistic) affects [[Navigator Product]] adoption speed
- Whether state-level antibiogram partnerships (NY, NH, MA) generate inbound referrals
