---
date: 2026-06-29
description: "Automated daily capture from Granola, Gmail, and Slack — raw inbox for /om-intake routing"
tags:
  - meeting-notes
  - capture
source: daily-capture-agent
---

# Daily Capture — 2026-06-29

## Granola Meetings

### Spencer + Radha IRX Nav — 12:00 PM EDT
**Attendees:** Spencer Sutton, [[Radha Patel]] (InsightRX)

**St. Joseph's / BSMH integration:**
- Integration stalled — Nordic (EHR vendor) quoted 97 hours for Phase 1; Serge, Harrison Elliott, Lavanya pulled in to refute
- Actual cost estimate: ~$8K. Considering InsightRX paying directly to unblock before midyear
- [[Josh Crawford]] (BSMH) oversees Bond Sucor as well; Apollo Studio discussions already underway there — loop him into monthly calls once Phase 2/3 starts for network-level positioning

**Apollo Studio pricing model (proposed):**
- Hybrid consumption-based model (not pure SaaS, not outcomes-based)
- Three tiers: Apollo Studio Select / Premier / Enterprise
- MUE ROI rationale: ~$1/patient review, ~$10–15/bed for 6 MUEs; target 10:1 ROI
- Key build requirements before launch: token visibility dashboard, sales trained to scope on-site, CS able to flag usage spikes
- Competitors reviewed: Atropos Health, Health Catalyst (best comparator), Merative

**MTX commercialization:**
- OSF: ~2,000 beds, primarily peds; $10/bed = ~$20K; preventing one glucarpidase course nets $40–150K vs. $20–60K cost
- North Side: primarily adult, expected close closer to 2027
- MTX seen as more commercially promising than anticoagulation — cleaner ROI

**Anticoag product positioning:**
- Consensus: standalone anticoag LLM has very limited standalone value without real-time integration
- Radha considering raising at tomorrow's GTM: remove anticoag from active product list until integration viable
- Sales Hive anticoag leads consistently disappointed; pivot to Apollo Studio on those calls not landing

**Spencer's action items from this meeting:**
- Share Apollo pricing deck with full GTM team tomorrow — incorporate Serge's feedback first
- Escalate St. Joseph's $8K integration cost to Serge for go/no-go decision — frame as only shot at integrated site before midyear

**Waiting on:**
- Radha to raise anticoag positioning at GTM meeting tomorrow
- Radha to follow up with Diana on OU Health scoping meeting (confirm if implementation or Apollo scoping)

---

### IRX Navigator Tiger Team: InsightRX — 1:30 PM EDT
**Attendees:** Spencer Sutton, [[Nick Cotoia]] (ncotoia@covh.org), [[Vanessa Burns]] (vanessa@insight-rx.com)

**Navigator performance:**
- Production slowdowns flagged — 7–10 min for medium-difficulty queries; back-end throttling suspected (Spencer also raised in #irx-navigator Slack)
- Gustavo Maurina checked server: nothing wrong on server side, likely agent side
- Updated UI demo expected next week

**Clinical output bug — idarucizumab alpha:**
- Navigator recommended idarucizumab alpha as apixaban reversal agent — but that agent has been removed from the market
- Root cause: apixaban mention in pasted API note triggered anticoag recommendations outside ID scope
- Ncotoia to send Ruth Winn (UTI test patient) details so InsightRX can remove the off-market agent from recommendation list
- Rules of engagement being written to constrain LLM scope: Navigator = anti-infectives/ID only; mentioning bleeding risk in drug interaction is in scope; dictating reversal therapy is not

**COVH Residency Research Project (2-year structure):**
- Year 1: retrospective clinical validation — random audit 20–25 charts across 4–5 disease states, compare Navigator output vs. guidelines/current practice; COVH can run antimicrobial indication reports to pull cohorts
- Year 2: outcomes-focused validation leveraging integration data (LOS, readmission, intervention acceptance)
- Publication pathway: Year 1 → AJHP/pharma tech (impact factor ~5); Year 2 → OFID or similar; ASHP Midyear poster December; IDWeek Boston summer 2027; MAD ID Delaware (SIDP-affiliated)
- Resident orientation mid-July (resident starts Jul 6) — time critical

**Nordic SOW:**
- Nordic quoted 40 hours for project management alone — flagged as excessive (~$8K overestimate based on hourly rate)
- Plan: draft counter-proposal, ask Nordic to defend specific hour allocations
- Ncotoia will escalate directly to COVH VP rather than working through Nordic layers

**Spencer's action items from this meeting:**
- Write LLM rules of engagement for Navigator scope control (anti-infectives/ID only; define anticoag, surgical, imaging as out of scope)
- Draft resident-facing Navigator overview + 2-pager research project scope doc — before mid-July
- Prepare antimicrobial stewardship intro deck for mid-July resident orientation (15-min ID/AMS overview)
- Draft Nordic SOW counter-proposal with hour-by-hour challenge

**Waiting on:**
- Ncotoia to send Ruth Winn test patient details for idarucizumab alpha fix
- Ncotoia to continue phase 2 test patients and send feedback document (exclude Ruth Winn UTI case)

---

## Gmail

### Navigator
- **[[Dana Zalmanek]] → Spencer (fwd from Jonathan Ford, Lifebridge Health / Carroll Hospital)** — Jonathan Ford (PharmD, MBA, BCIDP, Clinical Pharmacy Supervisor) declined IRX Navigator pilot: "We will have to pass on IRX Navigator pilot since we don't have the bandwidth." Separately, Lifebridge IS ready to go live on aminoglycoside module (Nova). ⚠️ **DEAL LOSS — Navigator pilot at Lifebridge off the table for now.**

### Apollo
- **[[Samuel Wornall]] (Samuel.Wornall@bmhsc.org, Beaufort Health) → Spencer** — Replied to Apollo Studio outreach. Feedback: tried it a couple times, couldn't get AI to do what he wanted; frequent timeouts/auto-logouts made use challenging. Spencer replied acknowledging timeout issue (security measure limiting utility) and described core Apollo Studio value. ⚠️ **Lukewarm prospect — Apollo Studio not landing well on trial.**
- **Kelsey Kohman (Kelsey.Kohman@bswhealth.org, BSW Health, System Pharmacy Clinical Coordinator) → [[Tiffany Lee]] (cc: Spencer)** — After Tiffany connected them for a heparin MUE discussion, Kelsey followed up with director and replied: "at this time the cost does change things...will absolutely reach out if things change in the future." ⚠️ **DEAL LOSS — BSW Health / heparin MUE opportunity closed on cost.**

### FYI / Internal
- **Slack sign-in notification** — Slack account sign-in from new browser (Firefox, IP 185.220.69.146) flagged — likely automated session, no action needed
- **Calendar** — Vanessa Burns accepted Tiger Team meeting (no content)

---

## Slack

- **DM from sirj (sirj@insight-rx.com)** — Requested meeting 2–5 PM today; confirmed for 2:30 PM PST. Context: Apollo Standalone Pricing Conversation (per morning briefing, STM ticket). **FYI**
- **DM from John Pilla (jpilla@insight-rx.com)** — "hi i am back and yes!" → "this is done" + "let me know if you have any trouble adding" — context unclear, likely access/permissions grant completed. **FYI / WAITING ON** — confirm what was added
- **#irx-navigator** — Spencer flagged Navigator running slow (7–10 min for medium-difficulty queries). Gustavo Maurina: no server issues visible. Vanessa: no prod changes since last Tuesday. Lavanya: same build since last Tues. **DECISION** — investigation needed; no root cause found yet.
- **#analytics_feedback** — Spencer posted Sam Wornall's Apollo Studio timeout feedback (14-reply thread). **FYI** — product team looped in.
- **Morning briefing (self-DM via Claude, 9:00 AM EDT)** — Key flags:
  - STM-67 PAST DUE: Align with Vanessa on COVH residency project design (was due Jun 27; addressed in Tiger Team today)
  - STM-75 (due Jun 30): Reply to Samad Minhaj (OSF Healthcare) re: future cost structure for HD methotrexate — 3 days unanswered, coordinate with Jon/Stephanie first
  - STM-77 (due Jul 1): MedStar/Kellie Bedford replied Jun 24 adding Colby Miller + Andrew Rubio (pharmacy) for Navigator demo — 5 days unanswered
  - STM-66 PAST DUE: Scott Bergman (Nebraska Medicine) Navigator follow-up (due Jun 26)
  - STM-68 & STM-70 (due Jun 30): Scope COVH opioid stewardship module + PMP API; follow up with Nick Cotoia on specifics
  - STM-74 (due Jul 3): Respond to Nick Cotoia's offer to share COVH integration SOW to unblock IT delay
  - **48 of 50 open STM tickets are overdue** — oldest from Jun 1 (25+ days past due)

---

## Action Items Surfaced

**Spencer owns — Navigator:**
- [ ] Write LLM rules of engagement for Navigator scope (anti-infectives/ID only; anticoag reversal, surgical, imaging = out of scope)
- [ ] Draft resident-facing Navigator overview + 2-pager research project scope doc — **before mid-July (resident starts Jul 6)**
- [ ] Prepare antimicrobial stewardship intro deck for mid-July resident orientation
- [ ] Draft Nordic SOW counter-proposal with hour-by-hour challenge for Ncotoia
- [ ] Reply to MedStar/Kellie Bedford + Colby Miller + Andrew Rubio re: Navigator demo — **5 days unanswered (STM-77, due Jul 1)**
- [ ] Scott Bergman (Nebraska Medicine) Navigator follow-up — **PAST DUE since Jun 26 (STM-66)**
- [ ] Scope COVH opioid stewardship module + PMP API; follow up with Ncotoia (STM-68 & STM-70, due Jun 30)
- [ ] Respond to Ncotoia's offer to share COVH integration SOW (STM-74, due Jul 3)

**Spencer owns — Apollo / Sales:**
- [ ] Share Apollo pricing deck with GTM team tomorrow — incorporate Serge's feedback first
- [ ] Escalate St. Joseph's $8K integration cost to Serge for go/no-go — frame as best shot at integrated site before midyear
- [ ] Reply to Samad Minhaj (OSF Healthcare) re: HD methotrexate future cost structure — **3 days unanswered (STM-75, due Jun 30)** — coordinate with Jon/Stephanie first

**Waiting on others:**
- [ ] WAITING ON Ncotoia: Send Ruth Winn test patient details so InsightRX can remove idarucizumab alpha from recommendation list
- [ ] WAITING ON Ncotoia: Continue phase 2 test patients + feedback doc (exclude Ruth Winn UTI)
- [ ] WAITING ON Radha: Raise anticoag product positioning at GTM meeting tomorrow
- [ ] WAITING ON Radha: Follow up with Diana on OU Health scoping meeting type (implementation vs. Apollo scoping)
- [ ] WAITING ON John Pilla: Confirm what "this is done" refers to — clarify what access/item was added

**Deal losses to log:**
- [ ] Lifebridge Health / Jonathan Ford — Navigator pilot declined (bandwidth); Nova aminoglycoside module going live separately
- [ ] BSW Health / Kelsey Kohman — heparin MUE opportunity closed on cost
