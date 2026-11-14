# Ramp outbound GTM system

Status: design v1, 2026-11-14. Work in progress: nothing is built, no lists pulled, no copy written. Built from `context/icp/` (icp.md v2.1, personas.md, signal-matrix.md, icp-challenge.md), the repo's playbooks and skills, and the Tools section of CLAUDE.md.

How to read:
- Steps run in order. Each step has: what happens, the tool, the decisions (each answer and where it leads), and the hand-off to the next step.
- Codes: `icp` icp.md, `per` personas.md, `sm` signal-matrix.md, `wa` workflow-anatomy.md, `bc` build-clay skill. Signal IDs (U1 to U5) are from signal-matrix.md.
- INFERRED = a design choice or threshold not set by the research or the playbooks. Revise it after the first four weeks of data.
- PROPOSED = a tool or setting not yet in the CLAUDE.md Tools list. Needs the owner's OK.

Scope: US Mid-Market (100 to 999 employees, privately held, for-profit) in three segments: S1 software and technology, S2 construction and engineering, S3 healthcare. Signals: the top five from signal-matrix.md (U1 finance-ops hiring, U2 new finance leader, U3 headcount growth, U4 hiring in new countries or states, U5 funding for S1 only).

---

## The flow

```
 1 Context OS ──► 2 Buying signals ──► 3 Find companies ──► 4 Enrich ──► 5 ICP fit check
      ▲                                                                       │
      │                                                                       ▼
12 Weekly feedback ◄── 11 CRM ◄── 10 Replies ◄── 9 Sequence ◄── 8 Emails ◄── 7 People ◄── 6 Route by segment
```

Cheap, deterministic gates (dedupe, suppression, firmographic filters) run before anything that costs credits or model spend. [bc]

## Tools

| Tool | Role in this system | Status |
|---|---|---|
| Claude Code + this repo | Context OS; runs the skills; operates Clay through Rex | In use |
| Clay (via `tools/rex`) | Signals, company and people tables, enrichment, fit check, email waterfall | In CLAUDE.md |
| HubSpot | CRM: system of record for companies, contacts, suppression, deals | In CLAUDE.md |
| n8n | Scheduling and glue (Clay to sequencer to HubSpot, reply webhooks) | In CLAUDE.md, trial starts Week 4, not earlier |
| Email sequencer | Sends the email steps; tags replies | **PROPOSED: Instantly.** Its MCP is connected to this workspace and the campaign-qa skill supports it. Not yet chosen |
| LinkedIn tool | Connection requests and messages | **Not chosen.** Until then, LinkedIn steps are HubSpot tasks for a rep |
| Inbox placement test | Checks inbox vs spam before launch | inbox-placement-test skill (built for EmailBison and MailReach) |
| Notion, Miro | Publishing (step 14) and drawing this system (step 13) | Later |

---

## Step 1: Context OS

**What happens.** Every workflow starts from the repo, not from memory. The run reads the target definition, signals, angles and facts, and every later step writes back to it (step 12).

**Tool.** Claude Code with the repo files and skills: `/campaign-strategy`, then `/build-workflow-spec`, `/campaign-copy`, `/clay-build-plan`, `/design-clay-table-json`, `/import-clay-table`, `/campaign-qa`.

**Inputs.** icp.md (filters, exclusions, suppression), personas.md (titles, pains, objections), signal-matrix.md (segments, angles, signals), `context/messaging/facts.md` (the only allowed source of claims in copy).

| Decision | Yes → | No → |
|---|---|---|
| Does this signal have a workflow spec with status STRUCTURE-APPROVED in `output/campaigns/<slug>/`? | Go to step 2 | Run `/build-workflow-spec` first. Nothing gets built without it |
| Does `context/messaging/facts.md` exist and cover the claims the copy needs? | Copy can be written in step 9 | `/campaign-copy` stops and builds facts.md from the template with the owner. Today it does not exist (messaging is step 10, not done) |
| Has a Context OS file changed since the last run (new exclusion, new objection, new angle)? | Re-read it; re-check open campaigns against it | Run as specified |

**Hand-off.** One approved workflow per signal, named `{Workflow} - {Segment} - v{n}` [wa], with its segment filters, persona titles and angle.

---

## Step 2: Buying signals

**What happens.** Each signal runs on its own schedule and produces a list of companies where the signal fired. Signal first, ICP filter after: the signal is the trigger, not a decoration on a static list. [sm, framework guardrail]

**Tool.** Clay sources and enrichments run through Rex. Before Week 4, Claude Code runs them by hand on the schedule. From Week 4, n8n triggers them.

| Signal | What fires | Clay action | Run frequency [wa] |
|---|---|---|---|
| U1 Finance-ops hiring | Controller, Assistant Controller, Accounting Manager, AP Specialist or Manager, Staff Accountant, Procurement Manager posted in the last 30 days | "Find Jobs at Company" / job-post signals | Weekly |
| U2 New finance leader | CFO, VP Finance, Head of Finance, Controller, VP Controller, Director of Accounting started in the last 90 days | "Find People" filtered by title and start date | Monthly |
| U3 Headcount growth | Headcount up 20% or more over 6 months | Company headcount enrichment, monthly snapshot | Monthly snapshot (`wa` says quarterly for hypergrowth; the delta needs monthly data points, INFERRED) |
| U4 New country or state | First job posts in a new country or US state, last 60 days | "Find company jobs growth by location signal" | Weekly |
| U5 Funding (S1 only) | Series A to D in the last 90 days, or a new SEC Form D | Crunchbase enrichment; EDGAR scrape via n8n | Bi-weekly |

| Decision | Answer → where it goes |
|---|---|
| Did the signal fire inside its window? | Yes → step 3. No → not added |
| U1: one finance role, or two or more within 30 days? | Two or more → tag `U1-team`. One → tag `U1-single`, sent after `U1-team` rows (Salesgear: a single role is often a backfill, sig 4.2). Both are Tier 2 unless another signal lifts them [icp 5] |
| U2: is the new leader in a champion or economic-buyer title? | Yes → carry the person as the first contact for step 7. No (other title) → drop |
| Has this company been contacted in the last 90 days? | Yes, and the signal is new → re-entry allowed, the new signal is logged [wa dedupe rule]. Yes, same signal → skip. No → step 3. The 90-day suppression length is INFERRED |

**Hand-off.** Signal rows with company name, domain or LinkedIn URL, signal ID, signal date and evidence URL (the job post, the profile, the funding record).

---

## Step 3: Find companies

**What happens.** Signal rows become one row per company in the Companies table for the segment, with a clean identity and every signal it carries. Suppression runs here, before any paid enrichment.

**Tool.** Clay Companies table (`Companies | US Mid-Market | <date>`, one workbook per segment) built with Rex [bc]. Suppression is a free lookup against a HubSpot export and a suppression list.

| Decision | Answer → where it goes |
|---|---|
| Can a company domain be resolved? | Yes → continue. No → one lookup or Claygent fallback; still no → drop as "no identity" (logged, not retried) |
| Is the domain already in the table? | Yes → merge: add the new signal to the existing row (one row per company). No → new row |
| Existing Ramp customer, partner-sourced account, open opportunity or recent loss in HubSpot? [icp 6, Suppress] | Yes → suppressed, stops here. No → step 4 |
| Public sector, nonprofit, or non-US HQ? [icp 6] | Yes → excluded. No → step 4 |

**Hand-off.** Deduplicated, unsuppressed companies with domain and LinkedIn URL typed as `url`, and a signal list per row. [bc]

---

## Step 4: Enrichment

**What happens.** Collect only the evidence the fit check and the copy need: firmographics first (cheap), then 2 to 4 secondary enrichments that route the message [wa].

**Tool.** Clay. Firmographics from Clay company enrichment. Location and employee count with a Claygent Run 1 and a Run 2 fallback when Run 1 is missing, failed or low-confidence [bc]. Every AI column has a native JSON Schema [bc]. AI at scale runs outside Clay unless the owner approves a USD estimate (starter-kit override #1).

| Field | Why | Source |
|---|---|---|
| HQ country, employee count, industry, ownership (private or public, for-profit) | Hard filters in step 5 | Clay company enrichment; Claygent fallback |
| Incumbent tools named in job posts (Expensify, SAP Concur, Bill.com, Divvy, Brex, Navan, Coupa) | U7 compound enrichment: routes the message, never a trigger on its own [sm] | Job description text from U1 or U4 |
| ERP named in job posts (NetSuite, Sage Intacct, QuickBooks, construction ERPs, SAP, Oracle, Workday) | Qualify filter and angle [icp 1] | Job description text |
| Locations or entity count | Positive fit marker; S3 angle [icp 1] | Website evidence (Claygent) |
| Funding status (S1) | Routing for U5 and stacking [sm] | Crunchbase |

| Decision | Answer → where it goes |
|---|---|
| Is the employee count still missing after Run 2? | Yes → drop (the band can't be checked). No → continue |
| Is the industry classification clear? | Clear → use it. Ambiguous → the AI classifier returns `REVIEW` (enum `S1 | S2 | S3 | OUT | REVIEW`) → manual review queue |
| Is this a new column or a new batch? | Yes → prove it on one row that should qualify and one that should fail, then show the cost in USD and Clay credits and wait for the owner's OK [bc, import-clay-table]. No (proven column, approved batch) → run |

**Hand-off.** Each company row with firmographics, a segment label and secondary evidence.

---

## Step 5: ICP fit check

**What happens.** Deterministic gates first, then one AI qualification that only reads the evidence already collected (no browsing). Then a readiness tier.

**Tool.** Clay formulas for the gates (free); `Company Fit Qualification / Use AI / <Model>` returning `PASS | FAIL | REVIEW` with reasons [bc].

| Gate (in order) | Pass → | Fail → |
|---|---|---|
| HQ is US | next gate | Exclude |
| 100 to 999 employees | next gate | Exclude (log as a candidate for the SMB or Enterprise motion) |
| Privately held, for-profit | next gate | Exclude |
| Industry is S1, S2 or S3 | next gate | Exclude |
| Not a SAP, Oracle Fusion or Workday shop (if the ERP is known) | next gate | Exclude: Enterprise-tier fit [icp 1] |
| ERP known and in the supported list? | Positive marker | Unknown does not disqualify (ERP detection is not solved) [icp 1] |
| AI qualification | PASS → tier. REVIEW → manual queue, decided within the week. FAIL → exclude with reason | |

Not checked here: the $25,000 cash floor. It can't be seen from outside; Ramp's own underwriting checks it at sign-up [icp 6].

| Tier [icp 5] | Rule | Leads to |
|---|---|---|
| Tier 1 | PASS plus U2 (new leader), U3 (headcount growth) or U4 (new country or state) | Step 6, email plus LinkedIn plus rep task |
| Tier 2 | PASS plus U1 or U5 only (`U1-team` sent before `U1-single`) | Step 6, email plus LinkedIn |
| Tier 3 | PASS, no live signal (signal expired) | Held; re-checked when a new signal fires. No outreach |

**Hand-off.** Qualified companies with segment, tier, signals and the reason for the verdict.

---

## Step 6: Route by segment

**What happens.** Each qualified company goes to one campaign: the signal sets the workflow, the segment sets the angle, the tier sets the channel mix.

**Tool.** Clay formula (deterministic routing; no model). Campaign names follow `{Workflow} - {Segment} - v{n}` [wa], for example `Finance-ops hiring - Construction - v1`.

| Decision | Answer → where it goes |
|---|---|
| Which segment? | S1 → software angle (card volume, vendor and software spend, adoption). S2 → construction angle (job-cost coding, crew cards, PO before payment). S3 → healthcare angle (one close across locations, growth by acquisition, invoice screening) [sm Matrix 1] |
| Which signal fired? (several → highest score in sm wins: U1 > U2 > U3 = U4 > U5) | Sets the workflow and the opening line. The other signals become secondary lines [wa signal stacking] |
| Which persona first? (INFERRED) | U2 → the new leader. U1 → the Controller (the role being hired usually reports to them), CFO second. U3, U4, U5 → the CFO or VP Finance, Controller second |
| Incumbent tool known (U7)? | Yes → "moving off {tool}" route. No → fallback route with no tool reference [wa] |
| Tier? | Tier 1 → email plus LinkedIn plus rep task. Tier 2 → email plus LinkedIn |

AP and accounting ops (the influencer) are not cold-contacted in v1: in the research they rarely start the search (INFERRED, personas.md section 3). Their pains appear in the copy as proof.

**Hand-off.** Company rows with campaign name, angle, persona order and channel mix.

---

## Step 7: Find people

**What happens.** Find current people in the persona titles at each routed company, merge two discovery paths into one People table, check they still work there, and qualify them.

**Tool.** Clay: a Find People staging table plus a people-search Claygent on the company row, both routed by `Send table data` into one shared People table [bc].

| Persona | Title families to search [per] |
|---|---|
| Champion | Controller, VP Controller, Corporate Controller, Assistant Controller, VP of Accounting, Director of Accounting, Chief Accounting Officer |
| Economic buyer | CFO, VP Finance, SVP Finance, Head of Finance |

| Decision | Answer → where it goes |
|---|---|
| Same person found by both paths? | Yes → merge on personal LinkedIn URL (or full name plus domain), keep the better-verified values [bc]. No → keep |
| `Still Employed?` (AI action, enum `YES | NO | REVIEW`) [bc] | YES → contact qualification. NO → drop. REVIEW → manual check |
| Contact qualification passes? | Yes → step 8. No → drop with reason |
| No champion found? | Use the economic buyer only |
| No champion and no economic buyer? | Company parked as "no contact"; logged for the weekly review |
| Contacts per company | At most one per persona, so two (INFERRED cap) |

**Hand-off.** Qualified, currently employed contacts, with the company verdict pulled in by one `Company Table Data` lookup [bc].

---

## Step 8: Find and verify emails

**What happens.** Find a work email and verify it before anything is sent.

**Tool.** One native Clay waterfall: Prospeo → LeadMagic → Icypeas → Findymail → Wiza → FullEnrich (own-key providers first, 4 steps by default), LeadMagic validation per step, then a second verifier on the results. Conservative: no catch-all. Run as a button, only after the owner approves the credit estimate. [bc override 3e]

| Decision | Answer → where it goes |
|---|---|
| Email found? | Yes → verify. No → LinkedIn-only route |
| Both verifiers say valid? | Yes → email plus LinkedIn sequence. No → LinkedIn-only route |
| Catch-all or risky? | Never emailed → LinkedIn-only route |
| Personal email (gmail and similar)? | Never used |
| Already in HubSpot as unsubscribed or bounced? | Suppressed (checked again here because emails are new keys) |

Before the first send from any new mailbox: run the inbox-placement-test skill. Inbox → launch is allowed. Spam or promotions → fix the domain or copy and test again.

**Hand-off.** Contacts with a verified work email (or flagged LinkedIn-only), ready for the sequencer.

---

## Step 9: The sequence (email and LinkedIn)

**What happens.** Copy is written from the approved workflow spec and verified facts only, QA'd against the spec, approved by the owner, then loaded and sent.

**Tool.** `/campaign-copy` (copy from the spec and facts.md, banned lists in `copy-bans.yaml`, no em dashes), `/campaign-qa` (checks the loaded campaign against the spec), the email sequencer (PROPOSED: Instantly), and LinkedIn by rep task until a tool is chosen.

Default shape (INFERRED; the workflow spec sets the final cadence):

| Step | Channel | Content |
|---|---|---|
| 1 | Email | Signal line + segment angle + one proof point from facts.md |
| 2 | LinkedIn | Connection request, no pitch |
| 3 | Email | Second angle: a persona pain in the customer's words [per] |
| 4 | LinkedIn | Message (only if connected) |
| 5 | Email | Short last note |

| Decision | Answer → where it goes |
|---|---|
| Copy passes `/campaign-copy` QA and `/campaign-qa`? | Yes → owner review. No → fix and re-run QA |
| Owner approves launch? (CLAUDE.md: ask before sending) | Yes → load and start. No → hold |
| Email bounced? | Stop email steps, continue LinkedIn only, mark the email bad in HubSpot |
| LinkedIn connection accepted? | Yes → send step 4. No → skip step 4 |
| Reply on any channel? | Stop all remaining steps on both channels → step 10 |
| Sequence finished with no reply? | Contact rests 90 days (INFERRED); re-entry only on a new signal [wa] |

**Hand-off.** Replies, bounces and step events from the sequencer and the LinkedIn tasks.

---

## Step 10: Reply handling

**What happens.** Every reply is classified within one business day (INFERRED SLA) and gets one next action.

**Tool.** Sequencer reply tags. Before Week 4: classified by hand (or by Claude Code with a fixed label set). From Week 4: n8n takes the reply webhook, classifies with an enum, and writes to HubSpot.

| Reply type | Next action |
|---|---|
| Interested or asks for a meeting | Book a meeting; create a HubSpot deal; notify the owner |
| Referral ("talk to X") | Add X as a contact with the original context; new short sequence that names who referred them |
| Objection | Answer from the persona's objection table [per]; log the objection type for step 12 |
| Not now, with a date | HubSpot task for that date; contact stays out of sequences until then |
| Not interested | Close; suppress for 180 days (INFERRED) |
| Wrong person | Ask for the right person; mark the contact; re-run step 7 for the company |
| Unsubscribe | Global suppression in the sequencer and HubSpot, same day |
| Out of office | Pause; resume after the return date |
| Bounce | Mark invalid; LinkedIn-only route |

**Hand-off.** Classified replies and their actions, all logged in HubSpot.

---

## Step 11: The CRM

**What happens.** HubSpot is the single record of who was contacted, why, and what happened. It is also the suppression source for step 3.

**Tool.** HubSpot. Sync before Week 4: CSV or manual import. From Week 4: n8n.

| What syncs | When |
|---|---|
| Company: domain, segment, tier, signals with dates, ERP and incumbent if known | When the company enters a sequence |
| Contact: persona, title, verified email, LinkedIn URL, campaign name, signal that triggered them | When the contact enters a sequence |
| Activity: sends, replies, reply type | On each event |
| Deal | On a booked meeting; deal source = campaign + signal |

| Decision | Answer → where it goes |
|---|---|
| Company already in HubSpot with an owner? | Yes → owner gets a task, no sequence (also caught in step 3). No → create |
| Contact already exists? | Yes → update properties, never a duplicate (match on email, then LinkedIn URL). No → create |
| Meeting booked? | Yes → deal created with campaign and signal attribution. No → activity only |

**Hand-off.** One table per week of sends, replies, meetings and deals by signal, segment, persona and campaign.

---

## Step 12: Weekly feedback loop

**What happens.** Every week the results go back into the Context OS so the next run is better. This review is part of the work log and the next ISO week's priorities file.

**Tool.** Claude Code reads HubSpot and sequencer results and updates the repo files; Matrix 3 in signal-matrix.md is the tracker.

| Read | Write back to |
|---|---|
| Sends, bounce, reply and positive-reply rates by signal, segment and persona | Matrix 3 tracker; the Volume score in Matrix 2 (measured counts replace INFERRED) |
| Reply reasons and objections | personas.md objection tables |
| Loss reasons ("not now", competitor named) | icp.md section 7 |
| Pains named in replies and calls | icp.md section 3b, with grade A when quoted |
| Meetings and deals: did the signal fire before they engaged? | Signal grades in icp.md section 3a and signal-matrix.md (this is the backtest) |
| Clay and Rex problems | `tools/rex/LEARNINGS.md` |
| What worked and what didn't | `knowledge-base/learnings/` |
| Next week's runs and fixes | `weekly-priorities/<next ISO week>.md` and the work log |

| Decision (starting thresholds, all INFERRED) | Answer → where it goes |
|---|---|
| Bounce rate above 2% on any mailbox? | Pause that mailbox; check the waterfall and verification settings |
| Signal has 200 or more contacts and no positive replies? | Iterate the copy angle first (one change per version, `v{n+1}`) [wa] |
| Two iterations, still no positive replies? | Kill or rework the signal; record why in signal-matrix.md |
| Positive replies concentrated in one segment or persona? | Shift volume there; note it in the next week's priorities |
| A Context OS file changed this week? | Step 1 re-reads it before the next run |

---

## Pillar check

| Pillar | Where the design delivers it | Gaps and risks |
|---|---|---|
| **Clean data** | One row per company (domain dedupe); one People table with source lineage; typed `url` and `email` columns; `Still Employed?` before any copy; two-verifier email check with no catch-all; suppression before paid enrichment; HubSpot as the single record [bc] | HubSpot and Clay sync is manual until n8n (Week 4), so suppression can lag. Duplicate risk across the three segment workbooks needs a shared suppression check |
| **Always-on signals** | Each of the five signals has a schedule matched to its speed (weekly, bi-weekly, monthly) [wa]; re-entry on a new signal | Until n8n is live, "always-on" means a manual weekly run by Claude Code. Volume per signal is unmeasured (sm Matrix 2) |
| **Composable workflows** | Universal signals are one Clay build each, reused across segments with keyword swaps [sm]; one Companies plus People pattern [bc]; routing by formula; the skill chain from spec to copy to QA; standard campaign naming [wa] | LinkedIn tool and sequencer not chosen, so the send layer is not yet composable. Copy is blocked until facts.md exists |
| **Tight feedback loops** | Weekly review writes back to icp.md, personas.md, signal-matrix.md, learnings and the next week's priorities; deals carry signal attribution | Reply classification is manual until n8n. Thresholds are guesses until four weeks of data exist. The deal-to-signal backtest needs HubSpot properties set at send time from day one |

---

## Open decisions

1. Email sequencer: Instantly (PROPOSED) or another. It needs adding to the Tools list in CLAUDE.md.
2. LinkedIn tool, or keep rep tasks for v1.
3. Sending domains and mailboxes: who sets them up, and when warmup starts.
4. HubSpot sync before Week 4: CSV import cadence, or wait for n8n.
5. `context/messaging/facts.md`: needed before any copy (step 10 of the build brief).
6. The INFERRED thresholds: 90-day contact rest, 180-day suppression after "not interested", 2% bounce, 200 contacts before iterating, two-contacts-per-company cap.
