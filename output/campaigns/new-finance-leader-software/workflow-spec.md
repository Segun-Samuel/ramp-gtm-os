# Workflow spec: New finance leader, software

**Status:** STRUCTURE-APPROVED 2026-11-14 · copy pending

Slug: `new-finance-leader-software`. Built with `/build-workflow-spec` from `context/icp/icp.md` (v2.1), `context/icp/personas.md`, `context/icp/signal-matrix.md` (signal U2, with U1 and U7 as boosters) and `context/docs/gtm-system.md`. Approved section by section on 2026-11-14.

Notes:
- No `context/messaging/facts.md` exists yet. Every customer name, quote and Ramp claim below is research-sourced and becomes usable in copy only once its approved wording is in facts.md. Until then copy renders it as `{{placeholder}}`.
- INFERRED = not set by the research or the playbooks; revise after the first weeks of data.
- Segment history: first specced for construction, switched to software on 2026-11-14 at the owner's request (richer data, more mid-size software case studies). Construction can reuse the [ENGINE] sections with its own [ICP] section and angles.

---

## 1. Mother intent (trigger) [ENGINE]

**A US mid-market software, SaaS or AI company has a new CFO, VP Finance, Head of Finance or Controller who joined from outside in the last 90 days.**

- Catalog match: ⭐ New leadership (past 90/180 days), `knowledge-base/playbooks/workflow-anatomy.md`.
- Window: 0 to 90 days from the start date. The window is a test: every contact carries a start bucket (0 to 30, 31 to 60, 61 to 90 days) and a send bucket (section 7), and the weekly loop compares reply rates by bucket.
- New to the company only. Internal promotions are out of v1 and are logged for a later test.

## 2. Inclusion / exclusion [ICP]

**Include: company** (from icp.md section 1)
- HQ in the United States
- 100 to 999 employees
- Software, SaaS and AI companies
- Privately held, for-profit
- ERP, if known, is not SAP, Oracle Fusion or Workday (unknown ERP stays in)

**Include: trigger titles** (new to the company, start date 0 to 90 days ago)
- Economic buyer: CFO, Chief Financial Officer, VP Finance, VP of Finance, SVP Finance, Head of Finance
- Champion: Controller, Corporate Controller, VP Controller, Assistant Controller, VP of Accounting, Director of Accounting, Chief Accounting Officer

**Recipient:** the new leader only. One contact per company.

**Exclude**
- Titles containing: Interim, Fractional, Acting, Consultant, Advisor, Part-time, Outsourced
- Ramp customers, partner-sourced accounts, open opportunities and recent losses in HubSpot
- Anyone contacted in the last 90 days
- Every company on Ramp's 34-competitor versus list (`context/docs/research/competitors.md` section 3), for example Brex, Mercury, Airwallex, Rho, Navan, Zip
- Public sector, nonprofits, non-US HQ

## 3. Sources [ENGINE]

| What | Source | Tool |
|---|---|---|
| Trigger: new leader and start date | LinkedIn-based person profiles: current title and start date | Clay people search filtered by title, start date, company industry, company size and US; `start_date` and `company_domain` as extra keys (Rex) |
| New to the company | Previous position on the profile | Clay person data or LinkedIn Experiences action; previous employer domain differs from the current company |
| Company firmographics | Company profile | Clay company enrichment; Claygent Run 1 / Run 2 fallback for location and employee count |
| Still in the role | Person profile | `Still Employed?` AI action, enum `YES | NO | REVIEW` |
| Booster U1: finance-ops roles open | Company job postings, last 30 days | Clay "Find Jobs at Company" |
| Booster U7: incumbent tool named | Job description text from U1 | Keyword match |
| ERP named | Job description text from U1 | Keyword match |
| Suppression | HubSpot export and suppression list | Clay lookup (free) |
| Work email | Email finder waterfall | Clay native waterfall (Prospeo, LeadMagic, Icypeas, Findymail; Wiza and FullEnrich only if needed), LeadMagic validation per step, second verifier on results, no catch-all |

## 4. Signals table [ENGINE]

| # | Signal | Role | How it's read | Output |
|---|---|---|---|---|
| 1 | New finance leader, new to the company, started 0 to 90 days ago | trigger | Boolean: TRUE when the current title matches a trigger title (section 2) AND matches no excluded word AND the start date is within 90 days AND the previous employer domain differs from the current company domain | `New Leader` (TRUE / FALSE) |
| 2 | Leader persona | router | Regex on current title. CFO, Chief Financial Officer, VP Finance, VP of Finance, SVP Finance, Head of Finance → ECONOMIC_BUYER. Controller, Corporate Controller, VP Controller, Assistant Controller, VP of Accounting, Director of Accounting, Chief Accounting Officer → CHAMPION | `Leader Persona` (ECONOMIC_BUYER / CHAMPION) |
| 3 | Days since start | context-clause and test tag | Count: today minus start date | `Start Bucket` (clusters below). Never routes |
| 4 | Finance-ops roles open (U1 booster) | router | Count of job posts in the last 30 days with titles matching Controller, Assistant Controller, Accounting Manager, Accounts Payable, AP Specialist, Staff Accountant, Revenue Accountant (INFERRED keyword), Procurement Manager. Posts in the leader's own title family are not counted (likely the stale post for the role just filled) | `Hiring Cluster` (clusters below) and `First Role Title` |
| 5 | Incumbent tool named in those posts (U7 booster) | context-clause | Keyword match on signal 4 job descriptions: Expensify, SAP Concur, Bill.com, Divvy, Brex, Navan, Coupa, Amex. First match wins | `Incumbent Tool` (name or blank). Never routes |
| 6 | ERP named in those posts | context-clause | Keyword match on the same descriptions: NetSuite, Sage Intacct, QuickBooks, Xero, Rillet, Campfire. A match on SAP, Oracle or Workday excludes the company (section 2) | `ERP` (name or blank). Never routes |

**Count clusters**

- Start bucket (signal 3, test only): 0 to 30 days = FIRST_MONTH; 31 to 60 = SECOND_MONTH; 61 to 90 = THIRD_MONTH.
- Hiring cluster (signal 4, routes): 0 roles = NOT_HIRING; 1 role = ONE_ROLE; 2 or more = TEAM_BUILD (rebuilding the team under the new leader).

What routes: 2 personas x 3 hiring clusters = 6 cells. Incumbent tool and ERP never route, because they only exist when the company is hiring.

## 5. Routing matrix with angles [ENGINE]

Economic buyer cells (C1 to C3) are about spend and headcount. Champion cells (C4 to C6) are about the mechanics of the close.

| Cell | Deterministic read | What it tells us (inferred situation) | The angle it earns |
|---|---|---|---|
| **C1** New CFO, not hiring | New Leader TRUE; Leader Persona = ECONOMIC_BUYER; Hiring Cluster = NOT_HIRING | A new finance head is reviewing where the money goes (vendors, software subscriptions, cards) with the team already in place. | Control vendor and software spend without adding finance staff. Proof: Foursquare, "We've eliminated rogue spend and cut our vendor stack by a third." |
| **C2** New CFO, one finance role open | New Leader TRUE; ECONOMIC_BUYER; ONE_ROLE; `{{role_title}}` exists | A new finance head is adding one person to finance: more volume is landing on the team. | The hire-or-fix choice, from a software company that faced it. Proof: Brandt's VP of Accounting, "instead of hiring our way through it, we fixed the workflow so we can keep supporting the organization as we scale." Decide what the `{{role_title}}` does before they start. |
| **C3** New CFO, two or more finance roles open | New Leader TRUE; ECONOMIC_BUYER; TEAM_BUILD; `{{role_title}}` exists | A new finance head is rebuilding the finance team for the company's next stage. | Build the stack for the next stage while hiring the team. Proof: TaskHuman's Controller, "We were growing too fast and needed a solution that could match that scale." Cards, bills, procurement and the close on one system before new hires inherit the old one. |
| **C4** New Controller, not hiring | New Leader TRUE; Leader Persona = CHAMPION; Hiring Cluster = NOT_HIRING | A new Controller is learning the close as it runs today: in software, a high volume of card transactions and subscriptions. | High card volume coded without manual work. Proof: Perplexity runs about 7,000 to 9,000 card transactions a month; its Controller: "Gone are the days of scrambling to chase receipts, manually coding really large data sets." |
| **C5** New Controller, one finance role open | New Leader TRUE; CHAMPION; ONE_ROLE; `{{role_title}}` exists | A new Controller is adding capacity to accounting. | Code spend in real time, not at month-end. Proof: Brandt's Staff Accountant, "We would have to wait until the statement closed at the end of the month to download all transactions." The new hire reviews exceptions instead of downloading statements. |
| **C6** New Controller, two or more finance roles open | New Leader TRUE; CHAMPION; TEAM_BUILD; `{{role_title}}` exists | A new Controller is staffing up accounting; employees across the company will use whatever system they choose. | A system people use without training. Proof: Foursquare, "The average person can figure Ramp out without training. That's what drives 100% adoption." New hires and the rest of the company start on one tool. |

**Branch coverage**

| Cell | Start bucket | `{{role_title}}` | Incumbent tool | ERP |
|---|---|---|---|---|
| C1 | Yes | No | No | No |
| C2 | Yes | Yes | If found | If found |
| C3 | Yes | Yes | If found | If found |
| C4 | Yes | No | No | No |
| C5 | Yes | Yes | If found | If found |
| C6 | Yes | Yes | If found | If found |

C1 and C4 rely only on the leader's arrival and the software setting. In the hiring cells, incumbent tool and ERP add one line each when present and are dropped when blank.

**Niche-native check:** every angle depends on software-company traits: vendor and subscription sprawl, high card volume, company-wide adoption. C2 and C5 are the least niche; they are anchored to Brandt (a software company) and are the first to sharpen if copy reads generic.

**Proof sources** (research, to be cleared into facts.md before copy): Foursquare (`customers.md` 3.10, `voice.md` 1), Brandt (`customers.md` 3.34 and 7, `signals.md` 2.1), TaskHuman (`signals.md` 2.1), Perplexity (`customers.md` 3.2).

## 6. Variables contract [ENGINE]

| Variable | Source field | Exists in cells |
|---|---|---|
| `{{first_name}}` | People table, First Name | All |
| `{{company_name}}` | Companies table, Company Name | All |
| `{{leader_title}}` | People table, current title (trigger title) | All |
| `{{start_month}}` | Start date written as a month name | All |
| `{{start_bucket}}` | Start Bucket: FIRST_MONTH, SECOND_MONTH, THIRD_MONTH (a label for tenure wording, never a day count) | All |
| `{{role_title}}` | First Role Title (signal 4) | C2, C3, C5, C6 |
| `{{incumbent_tool}}` | Incumbent Tool (signal 5) | C2, C3, C5, C6, only when not blank |
| `{{erp}}` | ERP (signal 6) | C2, C3, C5, C6, only when not blank |
| `{{social_proof}}` | Cell proof line from `context/messaging/facts.md` (Foursquare for C1 and C6, Brandt for C2 and C5, TaskHuman for C3, Perplexity for C4) | All; placeholder until facts.md exists |
| `{{sender_name}}` | `context/messaging/facts.md`, sender block | All; placeholder until facts.md exists |

Tracking fields, never in copy: `Cell ID`, `Days Since Start`, `Start Bucket`, `Send Bucket`.

## 7. Cadence and channel [ENGINE]

**Periodicity:** always-on, run monthly (catalog velocity for leadership changes). Each leader enters once; a leader who later changes company may re-enter.

**Timing test:**
- First run: the backlog covers all three start buckets.
- From the second run: each new leader gets a `Send Bucket` from a hash of their LinkedIn URL modulo 3 (0 → send in days 0 to 30 after start; 1 → days 31 to 60; 2 → days 61 to 90). Leaders already past their bucket when they enter are sent at once and tagged late.
- The weekly loop compares reply and positive-reply rates by bucket.

**Channel:** email and LinkedIn (a new finance leader puts the company in Tier 1, `gtm-system.md` step 5).
- Email: the sequencer (Instantly proposed, not yet chosen).
- LinkedIn: HubSpot task for a rep until a LinkedIn tool is chosen.
- No verified email: LinkedIn only.

**Sequence shape** (from `gtm-system.md`; timing INFERRED):

| Step | Day | Channel | Content |
|---|---|---|---|
| 1 | 1 | Email | Arrival plus the cell's angle |
| 2 | 3 | LinkedIn | Connection request, no pitch |
| 3 | 5 | Email | Second angle: a persona pain in the customer's words |
| 4 | 8 | LinkedIn | Message, only if connected |
| 5 | 12 | Email | Short last note |

**Stop rules:** a reply on either channel stops both; a bounce stops email and LinkedIn continues; an unsubscribe is suppressed everywhere the same day.

---

## Definition of done

- [x] Mother intent: one sentence, signal-led, matched to the catalog
- [x] Inclusion: ICP box + trigger definition + recipient, tagged [ICP]
- [x] Exclusion: who's out and why
- [x] Sources: trigger + every enrichment
- [x] Signals table: every read deterministic, every role declared
- [x] Count clusters declared for every count that routes
- [x] Routing matrix with the angle column complete
- [x] Branch coverage: every cell's angle survives on the data in that cell
- [x] Variables contract: every `{{variable}}` mapped to its source field
- [x] Engine/ICP markers on every section
- [x] Cadence and channel declared

## Next

`/campaign-copy` writes the copy from this spec. It will stop at its facts gate until `context/messaging/facts.md` exists with the approved proof lines and sender details.
