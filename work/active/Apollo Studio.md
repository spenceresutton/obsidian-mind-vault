---
date: 2026-05-01
description: "Apollo Studio go-to-market strategy, product development, and prospect demos — MUE analytics, EDA integration, standalone positioning"
tags:
  - work-note
  - active
status: active
quarter: Q2-2026
---

# Apollo Studio

Active project tracking Apollo Studio go-to-market, product development, and key demos. Apollo Studio is the AI-powered analytics layer — chat-to-plot, MUE automation, flat file ingestion — positioned as both a standalone service and an upgrade within existing Apollo Gold.

See also: [[Navigator Hospital Pipeline]], [[Q2 2026 OKRs]]

---

## Product Definition

Three components under the Apollo umbrella:
1. **Apollo (Nova/MIPD)** — standard precision dosing analytics
2. **Apollo Studio** — chat-to-plot functionality and data environment access; natural language interface for custom queries; "glass box" methodology display
3. **White Glove Analytics** — flat file ingestion, data mapping, bespoke investigation service

Two deployment modes:
- **MIPD-focused** (within Apollo Gold): contained, productized
- **Standalone** (flat file ingestion): requires white-glove service; bespoke engagement

---

## Go-to-Market Positioning

- Anchor to concrete endpoints: CMS measures, cost savings, mandatory reporting (NHSN, Joint Commission)
- Target: pharmacy informatics teams and operations leaders
- Competitive advantage vs Health Catalyst / Atropos: AI-powered analytics at lower cost; true HL7 integration vs claims-data-only competitors
- Avoid "workflow efficiency" as primary selling point — focus on cost savings and patient safety
- Key use cases: calcitonin appropriateness, high-cost medication MUEs, antibiogram automation, opioid stewardship

---

## Update — 2026-05-01 (Apollo Standalone Strategy)

Strategy session with Radha Patel, Sirj Goswami, John Pilla. BDR tool development tabled in favor of broader outreach. Apollo standalone framework defined.

**Action Items:**
- [ ] Spencer: Schedule follow-up with Sirj to resolve nomenclature and positioning questions
- [ ] Team: Review updated value proposition document
- [ ] Update Apollo slide deck and provider-facing demo materials
- [ ] Develop functional buyer experience plan
- [ ] Create sales motion document including pipeline development and post-close workflow

**Key Points:**
- Unresolved: Apollo Studio vs Apollo Standalone nomenclature; whether Navigator includes Apollo components by default
- Pricing model TBD: SaaS subscription vs project-based professional services
- Professional services component challenges SaaS recurring revenue model
- BDR tool: Spencer tabling advanced development, focusing on Salesforce workflows

---

## Update — 2026-04-28 (Provider GTM — Apollo Positioning)

Apollo analytics-as-service pitch resonates across stakeholders. EDA agent going live in 2 weeks at time of meeting.

**Key Points:**
- Health Catalyst comparable: $500K–1M ARR, up to $4–8M for largest; two-tier deploy vs deploy+white-glove (4x price difference)
- Main competition: Epic Slicer Dicer (frustrated users, limited cross-data analysis)
- Apollo service model: data mapping + context mapping + clinical team generates plots + self-service access ongoing
- Ohio Health lead: pharmacy informaticist needs help beyond vancomycin; large metrics list; most feasible without full integration

---

## Update — 2026-05-05 (Apollo Analytics Demo — Jeffrey Starkey / Deaconess)

First opportunity from Apollo campaign (35+ hospitals contacted). Jeffrey Starkey at Deaconess currently uses Apollo Silver for QAPI metrics.

**Action Items:**
- [ ] Spencer: Send follow-up email including broader org outreach approach and data analysis pilot program offer
- [ ] Spencer: Send AI education circuit materials and slide deck for preceptor development
- [ ] Explore resident involvement in AI analytics projects

**Key Points:**
- Deaconess grown from 2 to 7 hospitals without expanding stewardship resources — Jeffrey staffing ~50% clinical time vs intended 20–30%
- Interested in Apollo Studio concept but cited staffing crisis; not ready for Gold but engaged on flat file ingestion
- Apollo Studio: 90 seconds to 3 minutes for complex queries; pinnable assets for recurring reports
- Stage 2–3 AKI rate stratification by age groups and facility demonstrated

---

## Update — 2026-05-07 (UTMB Analytics Demo)

Apollo analytics demo with UTMB team. Strong interest in expanded analytics beyond ID drugs.

**Action Items:**
- [ ] Radha: Send Apollo analytics one-pager to UTMB
- [ ] UTMB: Evaluate interest in expanded analytics beyond ID drugs
- [ ] Future discussion on custom analytics needs as Scott settles into new role

**Key Points:**
- UTMB currently uses Epic Slicer Dicer (tedious, manual) and PowerBI (limited scope)
- Scott (quality representative) showed strong interest — asked detailed analytics questions beyond MIPD
- Flat file ingestion discussion: Scott wanted immediate access, clarified need for Sirj team coordination
- Natural language queries via Studio demonstrated; calcitonin appropriateness and custom MUE use cases shown
- Navigator integration targeting February 2027

---

## Update — 2026-05-12 (Provider GTM — Apollo Studio Strategy)

Deep dive on Apollo Studio positioning, calcitonin use case, and white-glove service process.

**Action Items:**
- [ ] Create synthetic calcitonin dataset for realistic demos
- [ ] Build hosted demo environment (not Claude-based)
- [ ] MAD-ID: Explore high-cost medication use cases, gather market feedback
- [ ] Post-MAD ID: Align Apollo Studio rollout with existing customer outreach
- [ ] Schedule workshop on demo environment development
- [ ] Create customer feedback tracking document

**Key Points:**
- Calcitonin MUE use case: $500/dose, 1 in 3 doses unnecessary; automates 40–160 hour manual review process
- White-glove process: discovery → data pipeline setup → Studio configuration → CS handoff
- Target "vancomycin equivalent" beachhead market for Studio — focus on 6-month roadmap capabilities
- CS-sales alignment needed: CS unaware of Apollo expansion campaigns; pipeline report in Salesforce proposed

---

## Update — 2026-05-19 (Apollo EDA Integration — Bryan Kleinberg)

Technical feasibility discussion with Bryan (engineering) and Paulo for EDA integration.

**Action Items:**
- [ ] Spencer: Create synthetic dataset using Claude, work backwards from desired MUE presentation
- [ ] Bryan: Join upcoming Sirj meetings (Wed/Fri) to clarify technical requirements and resource allocation
- [ ] Build proof-of-concept for 2 MUEs: (1) Calcitonin, (2) Quality-focused MUE
- [ ] Spencer: Share Apollo Studio folder documents and Claude artifact with Bryan
- [ ] Decision pending: standalone web app vs Apollo-integrated solution

**Key Points:**
- Bryan confirmed feasibility: 6-month timeline for full data ingestion and custom visualization
- Current roadmap aligns with Spencer's proof-of-concept needs
- UI adjustments required: sidebar filters → treatment tags
- Client feedback: positive but requesting actual demos, not conceptual presentations

---

## Update — 2026-05-19 (Provider GTM — MAD-ID Debrief)

MAD-ID conference debrief. Apollo Studio resonated strongly at conference.

**Action Items:**
- [ ] Spencer: Upload MAD-ID lead list to Salesforce for campaign launch
- [ ] Team: Develop customer survey on MUE problem statements (with Customer Success)
- [ ] Spencer: Continue Apollo upgrade campaign (2 opportunities from 30+ outreach)
- [ ] John/Sirj: Schedule Orca Bio meeting for busulfan conditioning support
- [ ] Marketing: Plan AI implementation webinar/roadshow for state pharmacy conferences
- [ ] Team: Finalize Apollo Studio beachhead market strategy

**Key Points:**
- VCU Health medical lab director: mentioned stratifiable antibiograms 3–4 times — promising non-pharmacy channel lead
- MUE discussions strong: anticoag, calcitonin use cases lit up ID specialists
- 40–100 hours human resource burden for current antibiogram creation — efficiency positioning
- Personalized antibiogram: 20–30% difference between standard and blood culture antibiograms
- Some customers using ChatGPT for Excel analysis — opportunity for validated, reproducible alternative
- Dose Me losing market share significantly (PE buyout, clinical staff departures)

---

## Update — 2026-05-20 (Apollo Gold Upgrade Quote — Baptist)

Pricing discussion for Baptist Apollo Gold upgrade with Laura and Dana.

**Action Items:**
- [ ] Spencer: Send Apollo Gold upgrade quote to Baptist
- [ ] Spencer: Send BMC renewal documents to Dana for Salesforce setup (BMT 57mo + ID Core 36mo)
- [ ] Spencer: Follow up on Covenant message from Jeff Lau
- [ ] Spencer: Continue pursuing Beaufort development partner signature (167 beds)

**Key Points:**
- Baptist: ID Core + Apollo Silver at $30/bed/year; proposed Gold at $30/bed total ($20 upgrade + $10 Silver credit)
- 553 beds = $16,590 annual for Gold; net upgrade cost $11,340 after Silver credit
- Start high, negotiate down — Gold list price $27,650 shown first

---

## Related

- [[Navigator Hospital Pipeline]]
- [[Q2 2026 OKRs]]
