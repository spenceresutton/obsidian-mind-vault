---
date: 2026-07-01
description: "Automated daily capture from Granola, Gmail, and Slack — raw inbox for /om-intake routing"
tags:
  - meeting-notes
  - capture
source: daily-capture-agent
---

# Daily Capture — 2026-07-01

> [!info] Related
> [[North Star]] · [[Brag Doc]] · [[Work Index|work/Index]]

## Granola Meetings

### Provider GTM Meeting — Jun 30, 1:00 PM EDT
**Attendees:** Spencer, John Pilla (PharmD), Laura Harter, Sirj Goswami, Nikhil, Radha Patel, Dana Zalmanek, Joseph Ioia

**Navigator Pipeline:**
- Elliot Infirmary, Beaufort, Nebraska — targeting close by August; exec summaries with integration specifics sent last week; Spencer followed up with Scott at Nebraska yesterday (was on vacation)
- Sanford pilot signed; auto-converts to contract Jan 1 unless they opt out — John confident
- Gotham contract signed
- Bay Health (NJ) approved funding
- Ohio State — still awaiting budget approval
- Mount Sinai, NYU Langone — progressing slowly but positively; Northwell reviewing agreement (3 large NY systems in play)

**Saint Joseph's / Nordic dispute:**
- Nordic scoped integration at 96 hours; InsightRX estimated 20–50 hours; 40-hr PM allocation seen as a money grab
- Strategy: build counter-scope, argue number down, then escalate to St. Joseph's VP
- Finance committee not until September; goal is to get build done before Nordic access lost in Feb 2027 (Sunquest Beaker conversion)
- Longer-term: Nordic is deeply integrated with Bon Secours Mercy Health — potential channel partner

**Apollo Studio:**
- Spencer reviewing competitor landscape for standalone pricing (limited data, mostly on the frontier)
- Two-pager in progress: applications, positioning, pricing; review with Sirj next week
- Apollo Messaging/Webinar Strawman rescheduled to Jul 1 (tomorrow)

**Radha updates:**
- Advent Health: pharmacy governance approved Nova + Navigator budget; call with Becca needed for integration roadmap + Gantt chart
- WellStar trial wrapped; Radha following up with Tiffany; budget decision expected July
- Radha closed 3rd BMT deal of year (Orlando Health, peds + adult)
- Northside (Atlanta): still in contracting, evaluating ID and BMT

**Joseph / Conference leads:**
- Mad ID leads called 3–4x with limited booking success
- Phoebe Putney: Joseph escalated a Sales Hive booking to system Director of Pharmacy — smart play
- ASHP strategy: dedicate someone to booking on-site follow-ups; Sirj suggested using Granola at booth

**Wins announced:**
- BMC signed: Nova for ID — Spencer's first closed sale
- Sanford pilot on track; Gotham signed; Advent Health budget approved

**Action items from this meeting:**
- [ ] Finalize Apollo two-pager and review with Sirj (target: next week)
- [ ] Build counter-scope for Nordic; attend working meeting Jul 8
- [ ] Post BMC close to #great-news channel (done per Slack — ✓)

---

### CRRT Model — Jun 30, 2:30 PM EDT
**Attendees:** Spencer, Stephanie Hughes

Deep-dive on Nova CRRT model (driven by Maimonides demo questions posted to #customer-success).

**Key points:**
- Model released ~2025; designed for patients who receive CRRT at any point during therapy
- Lives in hemodialysis section; defaults to "model-based clearance" on open
- Covariates: weight, height, serum creatinine, age; CRRT vs IHD label is NOT a covariate
- Sessions entered manually (start/stop times); "indefinite" option available for continuous CRRT
- Model stays active for entire patient stay once applied — does not revert when CRRT ends
- Alternative models: Oda et al. (requires effluent flow rate + urinary output), Goti et al. (not configured/advertised), manual entry (user-calculated clearance)
- IHD patients underrepresented in model development; manual entry may be best fit for IHD

**Action items:**
- [ ] Reach out to Stephanie with any follow-up questions

---

### Closing out a Sale — Jun 30, 4:30 PM EDT
**Attendees:** Spencer, Laura Harter

Post-BMC-close operational walkthrough.

**DocuSign:**
- Spencer set up work DocuSign trial account (confirmed via email)
- Ranvir countersigns faster than Surge; get work credentials from Ranvir if needed
- BMC amendment sent to Surge via Slack; Surge viewed but didn't sign page 5 — Laura resent

**Salesforce close requirements:**
- Signed contract attached, AP info filled in (email + PO required Y/N), products populated
- Spencer pre-filled Ebony Herd as AP contact (from BMT record) — needs confirmation
- Closing fires two automated notifications: Customer Success (kickoff) and AR (billing)
- BMC term start: October 1; invoice sends that date

**Implementation:**
- BMC can begin implementation before Oct 1 but cannot go live clinically until Oct 1 (fiscal year boundary)
- Recommended contract language (from Laura's MGH amendment): "Implementation activities may begin on or after the date of full execution. Clinical use may begin on or after [start date]."
- Tiffany auto-assigned as CS lead; likely to swap with Stephanie (who manages BMT for BMC)
- Kickoff call is AE's responsibility to schedule — no automated email for expansions

**Renewal ownership:**
- Open question: who owns renewals/QBRs when Spencer expanded an existing account?
- Laura + Dana currently paid on renewals; overlap needs resolution with Surge

**Laura sent Spencer (per email):**
- Epic Implementation Deck
- Epic Implementation Assets (technical — do NOT send to customer)
- Epic Kickoff Email Template

**Action items:**
- [ ] Confirm AP details for BMC with Babash — is Ebony Herd still correct? Is PO required? (Page 5 blank)
- [ ] Confirm BMC's preferred implementation start date; add note in Salesforce
- [ ] Get BMT renewal contract signed by BMC (they requested extension)
- [ ] Schedule BMC kickoff call (send scheduling email in early September if Oct 1 start)
- [ ] Discuss renewal ownership with Surge — clarify Spencer's role and comp structure

---

## Gmail

### Navigator

- **BMC contract SIGNED** — `Kimberly.Ackerbauer@bmc.org` (CC: Alison Blackman), Jun 30 12:24 PM — "We finally got sign off from the big boss." Attached signed InsightRx.pdf. 🚨 DEAL UPDATE — needs Salesforce close, AP confirmation, kickoff scheduling.

- **Navigator feedback from St. Joseph's** — `ncotoia@covh.org` (Nicholas J. Cotoia Jr., PharmD, BCPS, BCCCP — Clinical Pharmacy Coordinator, PGY-1 RPD, St. Joseph Hospital, Nashua NH), Jun 30 12:09 PM — Active pilot sanity testing results:
  - UTI TEST_MW: PASS
  - UTI TEST_RW: FAIL — heavy Apixaban reversal recommendations for UGIB (Andexanet alfa)
  - PNA TEST_SA: FAIL — job timeout x2 on new patient creation, HCAP terminology outdated, vancomycin dosing despite MRSA nares negative, missed renal dose adjustment (CrCl 35, cefepime should be q12h not q8h), cost display missing "$" symbol
  - CC'd Tiffany and Vanessa — they're looped in

- **Navigator Clinical Ticket Review (recurring)** — Vanessa Burns invited Spencer + Luke Lashley, Wednesdays 4–4:30pm EDT

- **Navigator Ticket / Feedback catch-up (one-time)** — Vanessa Burns invited Spencer + Luke Lashley, Mon Jul 6 12:30–1pm EDT

- **Counter-scope meeting for St. Joseph's/Nordic** — All attendees accepted Jul 8, 5–6pm EDT: Ranvir Mangat, Haaris Padela, Lavanya Elangovan, Elliott Duvall

- **OSF Healthcare — High-Dose Methotrexate partnership** — Spencer's email to Sarah Engberg + Craig Magarity bounced OOO; Craig back 7/2, Sarah back 6/29 (may now be reachable). Thread subject: "IRX:OSF Partnership on High-Dose Methotrexate."

### Apollo

- **Apollo Messaging/Webinar Strawman** — Updated calendar invite for Jul 1 12–1pm EDT (today); attendees: Spencer, John Pilla, Nikhil. Review Apollo messaging and run gap analysis on marketing materials.

- **Novant Health — Apollo Studio follow-up** — Laura (CC: Spencer, Stephanie) sent Apollo Studio demo email to Robert Crawford, LJ McKamey, Greg Rebo at Novant Health, Jun 30 12:37pm. Included an AI Studio query example (AKI rate post 48h by location). No reply yet.

### Nova / Expansion

- **Montrose Health upgrade** — Leah Walter (lewalter@montrosehealth.com), Director of Pharmacy, replied Jun 30: "I'll review with my team and get back to you." Spencer sent price quote Jun 24 (with approved discount). Thread alive; no decision yet. WAITING ON.

### Sales / Admin

- **Salesforce task from Laura** — "Set up product review call for Renewal" — Account: **Centre Henri Becquerel** — Priority: HIGH — Due: 6/30/2026. ACTION ITEM.

- **Finance acknowledgment** — Mara Jimenez-Garcia (finance@insight-rx.com) acknowledged "New Customer:" notification — "We'll look into this and circle back." Likely BMC billing trigger.

- **DocuSign trial** — 14-day free trial activated for spencer.sutton@insight-rx.com. Account activation email received.

- **LinkedIn** — Notification to connect with Lashun Bonaparte (no context on who this is).

---

## Slack

- **#great_news_everyone** — Spencer posted: "Announcing my first sale! Just received a signed contract from Boston Medical Center. They have closed on ID Core as a system!" (Jun 30, 1:29pm). Reactions: 18x tada, 9x trixie, 3x champagne, 2x dancer. Congrats from Steph Hughes ("BMC is a hard one, how exciting!"), Lavanya, Sirj, Haaris. FYI / WIN.

- **#customer-success** — Spencer posted Maimonides demo questions (Jun 30, 11:34am): (1) Can dose assist options be limited? (2) Can historic PK priors default on patient return? (3) CRRT model mechanics overview. Reply count: 4. Laura added: "Spencer and I are reaching out to Geisinger about BMT — initially interested, they've gone dark." ACTION ITEM — route Maimonides questions to product/clinical; DEAL UPDATE — Geisinger going dark.

- **DM with Mahmood** — Spencer sent detailed root cause write-up for ECONNRESET on Claude Code over work OpenVPN (Jun 30 12:53pm). Root cause: OpenVPN pushes IPv6 default routes → macOS routes Anthropic traffic over VPN tunnels → resets on reconnect. Fix: LaunchDaemon reject routes for IPv6 global unicast/ULA. Asked Mahmood if VPN profile can stop pushing IPv6 defaults to remove client-side workaround. Mahmood had said "Claude's traffic doesn't go through the VPN" (incorrect for IPv6). WAITING ON Mahmood's response.

---

## Action Items Surfaced

### Navigator
- [ ] Confirm AP details for BMC with Babash — Ebony Herd correct? PO required? Page 5 of contract blank.
- [ ] Confirm BMC preferred implementation start date; note in Salesforce
- [ ] Get BMC BMT renewal contract signed (extension requested)
- [ ] Schedule BMC kickoff call — send in early September if Oct 1 start
- [ ] Discuss renewal ownership with Surge (Spencer's role, comp structure)
- [ ] Attend counter-scope working meeting for St. Joseph's/Nordic — Wed Jul 8 5–6pm EDT
- [ ] Route Maimonides demo questions to product/clinical team (dose assist limits, PK priors default, CRRT)
- [ ] St. Joseph's Navigator feedback (Cotoia) already CC'd Tiffany/Vanessa — confirm they're triaging
- [ ] Follow up with OSF Healthcare (Sarah Engberg) re: High-Dose Methotrexate partnership — she was OOO through 6/29, Craig Magarity back 7/2

### Apollo
- [ ] Apollo Messaging/Webinar Strawman review — TODAY Jul 1, 12–1pm EDT (with John Pilla, Nikhil)
- [ ] Finalize Apollo two-pager (competitor pricing, positioning, applications) — review with Sirj next week
- [ ] Set up product review call for renewal — **Centre Henri Becquerel** (HIGH priority Salesforce task from Laura)

### Nova / Expansion
- [ ] Montrose Health (Leah Walter) — WAITING ON team review of upgrade quote; follow up if no response by end of week

### Partnerships / Pipeline
- [ ] Set up integration roadmap call with Becca at Advent Health (Nova + Navigator phased plan, Gantt chart)
- [ ] Brainstorm ASHP booth strategy for on-site meeting booking (Sirj suggested Granola at booth)

### Admin / Infrastructure
- [ ] Confirm work DocuSign setup — get credentials from Ranvir or proceed with trial account
- [ ] Reply to Mahmood re: VPN profile IPv6 default routes — can they push a split-tunnel fix for IPv6?
