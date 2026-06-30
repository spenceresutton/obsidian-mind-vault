---
date: 2026-06-30
description: "Automated daily capture from Granola, Gmail, and Slack — raw inbox for /om-intake routing"
tags:
  - meeting-notes
  - capture
source: daily-capture-agent
---

# Daily Capture — 2026-06-30

## Granola Meetings

### Spencer + Radha IRX Nav — Jun 29, 12:00 PM EDT
**Attendees:** Spencer Sutton, [[Radha Patel]]

**St. Joseph's / BSMH Integration:**
- Integration stalled: IT scoped Phase 1 at 97 hours via Nordic, ~$8K actual cost
- Serge, Harrison Elliott, and Lavanya pulled in to challenge the estimate
- InsightRX considering paying the $8K directly to unblock; framed as only realistic path to an integrated site before midyear
- Josh Crawford (BSMH) oversees Bond Sucor — loop into monthly calls once Phase 2/3 begins; long-game network-level deployment story

**Research Plan (St. Joseph's):**
- Two-project structure (Spencer + Tiffany + Vanessa): Year 1 clinical validation (residents run patients vs. historic practice), Year 2 prospective outcomes
- Focus areas still being finalized: SSTI, CAP, UTI
- Timeline expected to bleed into a second year

**Apollo Competitive & Pricing:**
- Competitors reviewed: Atropos Health (Silver/Gold/Platinum, no public pricing), Health Catalyst (~$300–700K ARR declining with shift to AI-native "Ignite"), Merative/Micromedex
- Proposed 3-tier model: Apollo Studio Select / Premier / Enterprise — hybrid consumption, not pure SaaS or outcomes-based
- MUE ROI: ~100 patients per 15 pharmacist hours; 500-patient MUE ~$5,700 in HR cost → target 10:1 ROI → ~$10–15/bed for suite of 6 MUEs
- Key build requirements before launch: token visibility dashboard, sales scoping training, CS usage alerts

**OSF (MTX / Nova):**
- Serge open to research agreement; ~2,000 beds, ~$20K at $10/bed placeholder
- MTX seen as more commercially promising than anticoag; cleaner ROI story
- North Side (adults) + OSF (peds) together complete the MTX validation picture

**Anticoagulation:**
- Consensus: standalone anticoag LLM has no clear value prop without integration
- Sales Hive leads consistently disappointed; pivot to Apollo Studio not landing
- Radha to raise at tomorrow's GTM: propose removing anticoag from active list until integration is viable

**Action Items (Spencer):**
- Share Apollo pricing deck with full GTM team (incorporate Serge's feedback first)
- Escalate St. Joseph's integration cost to Serge for go/no-go on InsightRX funding the $8K
- Loop Josh Crawford into St. Joseph's progress once Phase 2/3 begins

**Waiting On:**
- Radha: raise anticoag positioning at GTM meeting, follow up with Diana on OU Health scoping (confirm implementation vs. Apollo scope)

---

### IRX Navigator Tiger Team: InsightRX — Jun 29, 1:30 PM EDT
**Attendees:** Spencer Sutton, [[Nick Cotoia]] (ncotoia@covh.org, Carroll Hospital / COVH), Vanessa (vanessa@insight-rx.com)

**Navigator Performance & Bugs:**
- Back-end throttling flagged; speed varies with query complexity
- Bug: idarucizumab alpha recommended as apixaban reversal agent — drug has been removed from the market
  - Root cause: apixaban mention in pasted API note triggered anticoag recommendations outside ID scope
  - Ncotoia to send test patient details (Ruth Winn UTI case excluded) for InsightRX to fix
- Ncotoia positive on the "pending actions" summary (urgent/soon/pending prioritization)
- Updated UI demo expected next week

**LLM Scope / Rules of Engagement:**
- Navigator should focus on anti-infectives and ID management only
- In-scope: bleeding risk in drug interaction context; out-of-scope: dictating reversal therapy, anticoag titration, surgical/imaging, source control (currently too verbose)
- Spencer to write formal rules of engagement doc

**Residency Research Project (2-year):**
- Year 1 (retrospective): random audit of 20–25 charts across 4–5 disease states, compare Navigator vs. guidelines and current practice; InsightRX handles data analytics
- Year 2 (outcomes): leverages integration data (LOS, readmission, intervention acceptance); aligns with DNV annual disease state reviews
- Publication pathway:
  - Year 1: AJHP, APHA, pharma tech (~impact factor 5)
  - Year 2: OFID (IDSA-affiliated) or similar ID journals
  - ASHP Midyear poster December (methods + 2 disease state preliminary results)
  - IDWeek Boston Summer 2027 (abstracts publish in JID)
  - MAD-ID (Delaware, SIDP-affiliated) also a fit

**Resident Orientation (mid-July):**
- Spencer to prep 15-min AMS/ID intro deck for incoming resident
- Spencer to draft resident-facing Navigator overview + 2-page research project scope document
- DOT phrase co-development proposed to streamline chart review

**Nordic SOW:**
- InsightRX considers Nordic's SOW significantly overpriced: 40 hours PM alone flagged as excessive
- InsightRX estimates true max ~60 hours total
- Plan: draft counter-proposal challenging hour allocations by group
- Ncotoia will escalate to COVH VP directly

**Action Items (Spencer):**
- Write LLM rules of engagement for Navigator scope control (anti-infectives/ID only)
- Draft resident-facing Navigator overview + 2-page research project scope doc (before mid-July)
- Prepare AMS/ID intro deck for resident orientation (15-min overview)
- Draft Nordic SOW counter-proposal with hour-by-hour rationale

**Waiting On:**
- Ncotoia: send test patient details for idarucizumab alpha case; continue Phase 2 test patients

---

### Apollo Standalone Pricing Conversation — Jun 29, 5:30 PM EDT
**Attendees:** Spencer Sutton, [[Sirj Goswami]]

**Competitive Landscape:**
- Very little public pricing data across the market — sparse competitive pricing is an advantage
- Atropos Health: 3 tiers (Silver/Gold/Platinum), account-based, claims data only, poor adoption; "Ace" = their EDA agent
- Health Catalyst: most transparent; ARR ~$300–700K (declining ~50% with Ignite shift); moving to consumption-based; abandoned analytics-as-a-service pilots (~0% margin)
- Pattern: forward-looking AI/agent marketing outpaces actual deployment

**MUE Pharmacist Time Valuation:**
- Scoping: 3–5 hrs; Data collection: 20–40 hrs; Analytics: 10–15 hrs; Synthesis/reporting: ~10 hrs
- 500-patient MUE (e.g., calcitonin): ~75 pharmacist hours, ~$5,000 HR cost; with analytics multiplier ~$6,000
- Apollo charges ~$2/patient reviewed vs. $10 cost → 5:1 ROI
- 6 MUEs/year at mid-size institution: ~$6,000/year; 1,000-bed system: ~$12,000/year baseline

**Pricing Model:**
- Structure: platform base fee (~$10–12/bed/year) + application-based fees (unlimited usage within agreed therapeutic areas)
- Standalone tier: flat-file ingestion, customer-managed refresh
- Enterprise tier: full EHR integration, RBAC, auto-refresh, white-glove service
- Integration fees (e.g., Nordic ~$8K) may be partially absorbed to accelerate deals
- OSF confirmed $10/bed makes sense; research phase free then converts
- Outcomes-based and consumption-based models deprioritized for now (too operationally complex)

**Platform Positioning:**
- Frame as "all things treatment optimization" — not a simple analytics tool
- Communicate infrastructure complexity early to anchor price: data lake, agents, HIPAA/HiTrust, audit trail, RBAC
- Application suite: MUE, antibiogram development, anticoagulation analytics, resistant organism predictive modeling, others TBD
- Two-pager deliverable: platform vision, stack diagram, 3–5 use case examples

**St. Joseph's Back-Channel:**
- Ncotoia aligned: considers Nordic quote unreasonable; will escalate to COVH hospital VP
- Sirj reached out to early Nordic founder (left ~2020–2021) for back-channel leverage
- Sirj willing to cover ~$8K integration fee if it accelerates the deal

**Action Items (Spencer):**
- Draft Apollo two-pager: platform vision, stack, 3–5 use case examples (include infrastructure value prop and soft application hypotheses)
- Build bottoms-up pricing inputs doc: pharmacist time, IT/infrastructure, HiTrust, integration, white-glove, displaced analytics subscriptions
- Schedule Apollo pricing review with Sirj next week (review two-pager + pricing doc, then bring to broader group)
- Set up St. Joseph's strategy meeting with Elliot, Harris, Ranveer, Sheldon (add Sirj + Lavanya as optional)

---

## Gmail

### Navigator

- **MedStar — Kellie Bedford** (Kellie.J.Bedford@medstar.net) · Jun 29 7:52 PM
  Thread: "InsightRX-Medstar: Introduction to IRX Navigator" (CC: laura@insight-rx.com)
  Kellie asked: "I wanted to evaluate the IRX Navigator as a possible future state enhancement with our Epic project (September 2027). Do you think that we should hold off on discussion for now?"
  > [!warning] UNANSWERED — prospect reply, needs reply
  > Previously added Colby Miller and Andrew Rubio (pharmacy) for demo scheduling. Spencer sent demo calendar link Jun 23. Epic go-live Sept 2027 — decision point: does timeline justify continuing now or deferring?

- **Lifebridge / Jonathan Ford** (forwarded by Dana Zalmanek) · Jun 29 4:51 PM
  Subject: "Fwd: IRX Navigator next generation CDS tool!"
  Jonathan Ford (Clinical Pharmacy Supervisor, Carroll Hospital / Lifebridge Health): Passed on Navigator pilot — no bandwidth. However: Nova aminoglycoside module go-live confirmed ("finally ready to flip the switch").
  Spencer replied: "ty"
  > [!info] DEAL UPDATE (Navigator lost) / Nova aminoglycoside activation in progress

### Apollo

- **Samuel Wornall / Baptist Memorial (BMHSC)** (Samuel.Wornall@bmhsc.org) · Jun 29 2:02 PM
  Subject: "Apollo Studio" (CC: stephanie@insight-rx.com)
  Sam trialed Apollo Studio; negative feedback — AI not doing what he wanted, timeout issues frustrating. Spencer replied: acknowledged timeout as a known security measure limiting utility; positioned Studio's value as finding unexpected patterns rather than answering known questions.
  > [!info] FYI — negative beta feedback; Spencer engaged and reframing

- **Kelsey Kohman / BSW Health** (Kelsey.Kohman@bswhealth.org) · Jun 29 6:21 PM
  Subject: "InsightRX MUE" (thread initiated by tiffany@insight-rx.com for heparin MUE discussion)
  Kelsey: Director says the cost changes things — pulling out. Appreciates the info.
  > [!warning] DEAL UPDATE — Apollo MUE deal lost at BSW Health (cost objection from director)

### New Lead / Inbound

- **Sreenidhi Chandrashekar** (forwarded by John Pilla · jpilla@insight-rx.com) · Jun 29 8:26 PM
  HubSpot notification: Sreenidhi Chandrashekar (nephrology@stmarthas.in) downloaded "Modules | BMT Product Guide" from Vasavi Hospital, India (+91 94488 85671). Healthcare Organization segment.
  > [!info] NEW CONTACT — international lead (India), likely Nova/BMT; routed to John Pilla

- **LinkedIn** · Jun 30 9:36 AM
  Notification: "You have 1 new message" — someone reached out to Spencer. Identity unknown from notification.
  > [!todo] Check LinkedIn DM

---

## Slack

No mentions or DM activity found via search for the last 24 hours. Slack may have been accessed from a new browser/device on Jun 29 (security notification received — IP 185.220.69.146, Firefox, USA). Confirm if that access was Spencer.

---

## Action Items Surfaced

### Navigator
- [ ] Reply to Kellie Bedford (MedStar) re: Epic 2027 timeline — should they defer? Needs a thoughtful answer on design partnership value now vs. waiting (UNANSWERED >24h approaching) — see [[Navigator Hospital Pipeline]]
- [ ] Write LLM rules of engagement for Navigator scope control (anti-infectives/ID only; out: anticoag reversal, surgical, imaging)
- [ ] Draft resident-facing Navigator overview + 2-page research project scope doc (due before mid-July orientation at COVH)
- [ ] Prepare AMS/ID 15-min intro deck for COVH incoming resident (mid-July)
- [ ] Draft Nordic SOW counter-proposal with hour-by-hour challenge (for Ncotoia to escalate to COVH VP)

### Apollo
- [ ] Draft Apollo standalone two-pager: platform vision, stack diagram, 3–5 use case examples — see [[Apollo MUE Data Engine]]
- [ ] Build bottoms-up Apollo pricing inputs doc (pharmacist time, IT, HiTrust, integration, white-glove, displaced subscriptions)
- [ ] Schedule Apollo pricing review with Sirj next week (review two-pager + pricing doc before bringing to GTM team)
- [ ] Share Apollo pricing deck with full GTM team (incorporate Serge's feedback first; GTM meeting is the venue) — see [[Apollo Studio]]

### St. Joseph's / BSMH
- [ ] Escalate $8K Nordic integration cost to Serge — go/no-go on InsightRX funding it (framed as best shot at integrated site before midyear)
- [ ] Set up SJH strategy meeting: Elliot, Harris, Ranveer, Sheldon (Sirj + Lavanya optional) — align on counter-quote to Nordic

### GTM / Misc
- [ ] Raise anticoag product positioning at GTM meeting (Radha's item — follow up to confirm it happened)
- [ ] Loop Josh Crawford (BSMH) into St. Joseph's progress once Phase 2/3 begins
- [ ] Check LinkedIn DM (received Jun 30 AM)
- [ ] Review Sreenidhi Chandrashekar HubSpot lead with John Pilla (India / Vasavi Hospital / BMT)
- [ ] Confirm Slack sign-in from new device (IP 185.220.69.146 Jun 29) was Spencer

### Waiting On
- [ ] Ncotoia: send test patient details for idarucizumab alpha bug; continue Phase 2 test patients
- [ ] Ncotoia: escalate Nordic SOW to COVH hospital VP
- [ ] Radha: follow up with Diana on OU Health meeting scope (implementation vs. Apollo)
- [ ] InsightRX eng: fix idarucizumab alpha off-market agent recommendation in Navigator
- [ ] Sirj: back-channel with early Nordic founder re: St. Joseph's integration
