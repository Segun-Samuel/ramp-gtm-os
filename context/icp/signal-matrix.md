# Ramp signal matrix

Status: work in progress, v1, 2026-11-14. To be validated with sales before any build. Built with the signal-matrix skill from [icp.md](icp.md) (v2.1), [personas.md](personas.md) and `context/docs/research/` (all sources checked 2026-11-14). Method: `knowledge-base/playbooks/signal-matrix-framework.md` and `workflow-anatomy.md`.

How to read:
- Source codes: `com` company.md, `cus` customers.md, `cmp` competitors.md, `mkt` market.md, `sig` signals.md, `voi` voice.md, then the section. `fw` = signal-matrix-framework.md, `wa` = workflow-anatomy.md (method docs, not Ramp research).
- INFERRED = not supported by the research. Tool names that come only from the method docs are marked `fw` or `wa`, not research.
- Quotes are verbatim from the research files. Customer quotes come from Ramp-published case studies, so they are vendor-selected.
- Segment scope: US Mid-Market, 100 to 999 employees, privately held, for-profit (icp.md section 1).

---

## Matrix 1: Segments x personas

### Segment definitions

| | S1 Software and technology | S2 Construction and engineering | S3 Healthcare (practices, multi-location providers, healthcare services) |
|---|---|---|---|
| Target definition | US HQ, 100 to 999 employees, software, SaaS or AI company, privately held | US HQ, 100 to 999 employees, general contractors, specialty subcontractors, developers, field services | US HQ, 100 to 999 employees, multi-location practice groups and healthcare services companies |
| Ramp evidence | "more than half of the companies in the Forbes AI 50 run on Ramp"; mid-size cases: Perplexity, Foursquare, Brandt, ElevenLabs [cus 1.3, cus 2] | "Trusted by 5,500+ general contractors, specialty subcontractors, and developers"; mid-size cases: Construction One, SAM Construction Group [cus 1.4, cus 2] | "2,500+ healthcare practices trust Ramp"; mid-size cases: SAMGI, Candid, Align ENTA, Rarebreed [cus 1.4, cus 2] |
| Ramp's segment pitch | Mid-market page: "Your whole finance stack in one place. Faster close. Same team." [cus 5.1] | "Catch job overruns before they start" / "Connect cards, expenses, AP, and budgets around every job. Code costs, spot budget risk, and complete retainage and compliance checks before payment." [cus 5.2] | "Healthcare financial management for every location, every provider." / "Every card swipe, vendor invoice, and reimbursement lands in your accounting system. Coded, categorized, and ready to close. No re-keying. No bank portals." [cus 5.2] |
| Typical ERP | NetSuite, Sage Intacct, QuickBooks Online (Brandt on Sage Intacct) [sig 7.3] | Sage 100 Contractor, Sage 300 CRE, Sage Intacct Construction, Viewpoint Vista and Spectrum, CMiC, Acumatica, NetSuite, QBO [cus 5.2] | QuickBooks (Align ENTA started on "five instances of QuickBooks") [sig 2.9]. Others: Not found |
| Lead product (hypothesis, INFERRED) | Corporate cards and expenses | Cards and expenses with job-cost coding | Cards and bill pay across locations |
| Upsell (hypothesis, INFERRED) | Procurement and vendor management | Accounts payable with PO matching | Procurement; multi-entity accounting |
| Company examples | Requires Clay research with filters: US, 100 to 999 employees, industry software / SaaS / AI, private. Lookalike seeds (existing Ramp customers, suppress from outreach): Perplexity, Foursquare, Brandt Information Services, ElevenLabs | Requires Clay research with filters: US, 100 to 999 employees, construction / specialty trade contractors, private. Lookalike seeds (suppress): Construction One, SAM Construction Group, Bratjen Construction | Requires Clay research with filters: US, 100 to 999 employees, healthcare providers / practice management, private, multiple locations. Lookalike seeds (suppress): SAMGI, Candid, Align ENTA, Rarebreed Veterinary Partners |
| Priority | **High** | **High** | **Medium** |
| Why | Densest data (funding, hiring, headcount all public); strongest case-study base | Ramp built a dedicated product and page; clear field-spend pain; weaker funding data | Clear multi-location pain; fewer mid-size cases; location and M&A data is harder to get |

No target company names are listed: the research holds only existing Ramp customers, and target lists need Clay research.

### Phase 2 scores (INFERRED ratings, basis given)

| Segment | Signal density | Product fit | Penetrability | Basis |
|---|---|---|---|---|
| S1 Software | High | High | High | VC-backed companies show in Crunchbase and SEC Form D; heavy hiring data (sig 9, fw "US Market") |
| S2 Construction | Medium | High | Medium | Dedicated Ramp for Construction (Jul 2026) and 5,500+ customers; funding signal weak outside VC markets (fw) |
| S3 Healthcare | Medium | Medium | Medium | 2,500+ practices but no Ramp "for Healthcare" launch found; PE roll-ups visible in cases (Rarebreed PE sponsor, Align ENTA acquisitions) [cus 3.28, sig 2.9] |

### Angle per cell

| Segment | Champion: Controller | Economic buyer: CFO or VP Finance | Influencer: AP and accounting ops |
|---|---|---|---|
| **S1 Software** | High card volume coded without manual work. Perplexity ran about 7,000 to 9,000 card transactions a month; its Controller: "Gone are the days of scrambling to chase receipts, manually coding really large data sets." [cus 3.2] | Control software and vendor spend without adding finance staff. Foursquare: "We've eliminated rogue spend and cut our vendor stack by a third." Brandt: "With Ramp, we haven't had to add accounting headcount to keep up with growth." [cus 3.10, cus 3.34] | Requests and approvals people actually use. Foursquare had "employees navigating 20-page guides just to submit a request"; after: "The average person can figure Ramp out without training. That's what drives 100% adoption." [sig 1.6, voi 1] |
| **S2 Construction** | Get field receipts and job codes without chasing. Construction One: "Our AP person would go into 75 different Google docs, make one giant report, turn it into an Excel spreadsheet, and import it into our software," Ramp claims "70%+ of receipts matched within 24 hours". [sig 2.5, cus 5.2] | Spend tied to every job before it overruns, and cards for crews instead of owners' cards. Viking Well Service: "We were using AmEx cards under the name of one of the partners, and we needed to move away from that". Infinity: "We had a name for the money we couldn't trace: 'X purchases.'" [cus 7, cus 3.15] | Pay subs and suppliers only against a PO and compliance check. Infinity: "A construction invoice isn't a bill. It's a contract with a due date." SAM Construction's page: "no PO, no payment". [cus 3.15, sig 6.2] |
| **S3 Healthcare** | One close across locations and entities. Align ENTA: "There was no solution before Ramp," ... "Each division had its own accounting." [sig 2.9] | Grow by acquisition without growing the finance team, on card limits that scale. Align ENTA: "we could grow the business without having to add headcount, increasing owner value with each acquisition." Rarebreed: "We had a $30,000 monthly limit for a $40M revenue business," [sig 2.9, cus 7] | Vendor invoices from every location coded with no re-keying, and invoices screened. Ramp healthcare page: "No re-keying. No bank portals." and "60 fraud signals screened per invoice". [cus 5.2] |

Considered and not in v1 (from icp.md): SMB, Enterprise and Strategic bands; nonprofits (candidate for a second segment); public sector (separate motion); Canada and UK.

---

## Matrix 2: Signals

### The four tests (from `wa`, "Choosing a Mother Intent")

Each signal is scored 1 to 5 on each test; total out of 20.
- **Reason:** clear buying reason. 5 = a customer quote names it as the reason (grade A in icp.md); 3 = Ramp's own content (B); 1 to 2 = third party or INFERRED (C).
- **Volume:** enough accounts firing per month in the segment. **No volume data exists in the research; every Volume score is INFERRED** until a Clay count is pulled.
- **Data:** a named tool can detect it programmatically.
- **Story:** easy to reference naturally in the first line of outreach.

### Signal table

| # | Signal (what fires) | Mother intent (`wa`) | Where the data comes from | Tool that detects it | Type | Reason | Volume | Data | Story | Total |
|---|---|---|---|---|---|---|---|---|---|---|
| U1 | Finance-ops roles posted: Controller, Assistant Controller, Accounting Manager, AP Specialist or Manager, Staff Accountant, Procurement Manager. Stronger when 2+ finance roles post within 30 days | Hiring specific roles | Public job postings (company careers pages, LinkedIn, job boards) | Clay "Find Jobs at Company" (`wa`); Clay job-post signals such as "Find Active Job Openings" [sig 9] | Universal | 3 | 4 | 5 | 5 | **17** |
| U2 | New finance leader: CFO, VP Finance, Head of Finance, Controller, VP Controller or Director of Accounting started in the last 90 days | New leadership | LinkedIn profile start dates | Clay "Find People" filtered by title and start date (`wa`); LinkedIn Sales Navigator; UserGems [sig 9] | Universal | 3 | 3 | 4 | 5 | **15** |
| U3 | Headcount up 20% or more in 6 months | Hypergrowth (headcount) | Company headcount from LinkedIn-based providers | Clay "Company Headcount" enrichment, Apollo (`wa`) | Universal | 5 | 3 | 4 | 3 | **15** |
| U4 | Hiring in a new country or new US states (first postings outside current locations, last 60 days) | Hypergrowth (hiring velocity), location variant | Job postings by location | Clay "Find company jobs growth by location signal" [sig 9] | Universal | 5 | 2 | 4 | 4 | **15** |
| U5 | Funding round (Series A to D) in the last 90 days, or a new SEC Form D | Companies fundraising | Crunchbase; SEC EDGAR Form D (filed "within 15 days after the first sale") [sig 9] | Clay Crunchbase enrichment (`last_funding_at`, `last_funding_type`) [sig 9]; EDGAR via n8n scrape (`wa`) | Universal, S1 only | 2 | 3 | 5 | 3 | **13** |
| U6 | Company announces an acquisition (new entity coming onto its books) | Niche-specific play (not in the `wa` catalog) | Press releases and trade news; Crunchbase acquisitions (INFERRED source) | News monitoring via Clay or n8n (INFERRED tool, not verified) | Universal, best for S2 and S3 | 3 | 2 | 2 | 5 | **12** |
| N1 | S3: location count rising for a practice group (new clinics opening) | Niche-specific play | Google Maps listings | Google Places API via Clay HTTP (`fw` physical-world signal; not verified for this use) | Niche, S3 | 2 | 2 | 3 | 4 | **11** |
| U7 | Job posting names an incumbent tool: Expensify, SAP Concur, Bill.com, Divvy, Brex, Navan, Coupa | Competitor customers | Job description text | Clay job-post data with keyword match (`wa`: "job posts mentioning competitor tools") | Universal, **compound only** | 2 | 2 | 3 | 4 | **11** |

### Basis for each score

| # | Reason | Volume (all INFERRED) | Data | Story |
|---|---|---|---|---|
| U1 | Vendor blog only (Salesgear: "Two or more roles on the same team within about 30 days" signals a plan) [sig 4.2]. Brandt frames hiring as the alternative to Ramp: "add people, or redesign the process." [sig 2.1] | `fw` calls hiring the highest-volume universal signal | Job posts are public; named Clay actions | "You're hiring an AP specialist" leads straight to the Brandt story |
| U2 | Narration only: "As soon as Assistant Controller Tim Borse joined MAGNA-TILES, he knew the company needed a better corporate card system." The 90-day window is unproven; "70% of budget in 100 days" is untraceable [sig 2.5, sig 5] | Every company changes finance leaders at some point; rate Not found | LinkedIn start dates via Clay or Sales Navigator | "Since you joined as Controller" is natural |
| U3 | Customer quote: "We were growing too fast and needed a solution that could match that scale," (TaskHuman) [sig 2.1] | Threshold from `fw` and `wa` (20 to 25%); share of mid-market firms hitting it: Not found | Headcount enrichment is standard | Generic: "you've grown fast" |
| U4 | Customer quote: "Our previous vendor wasn't able to service our entire employee base," (Notion) [cus 3.1]. Ramp supports cards in 30+ countries [com 2] | Few mid-market companies open new countries in any month | Named Clay signal [sig 9] | "Your first hires in London" is specific |
| U5 | No customer quote ties funding to buying; narration only (TaskHuman) [sig 2.2] | VC-backed only; `fw`: "Only for VC-backed markets" | Crunchbase fields named in research [sig 9] | Congratulations-style opener, used by everyone |
| U6 | Ramp blog: "Every acquisition adds entities, GL structures, approval chains, and local compliance requirements." [sig 1.1]. Align ENTA's quote describes the result | Low in mid-market | No tool named in research | "Congrats on acquiring X; one more entity to close" |
| N1 | INFERRED. Rarebreed grew from "7 locations when it joined Ramp in 2020" to 120+ [cus 3.28] | Unknown | Google Places named only in `fw` | "Your third clinic this year" is specific |
| U7 | Ramp itself says Brex users "don't need to make a move yet" [sig 1.2] | Only a share of postings name tools | Job text is public; BuiltWith cannot see back-office tools (`fw`, sig 9) | "Moving off Expensify" is concrete |

### Iron Law check (could a Clay operator build it now?)

| # | Key filters | Status |
|---|---|---|
| U1 | Titles above; US; posted in the last 30 days; ICP filter: 100 to 999 employees, S1 to S3 industries; exclude staffing and recruiting firms | VERIFIED (tool named in research and `wa`) |
| U2 | Titles above; current company start date in the last 90 days; ICP filter applied after | VERIFIED |
| U3 | Headcount delta of 20% or more over 6 months (monthly snapshots); ICP filter | VERIFIED (threshold from `fw`, INFERRED for Ramp) |
| U4 | Postings in a country or state with no prior postings, last 60 days; ICP filter | VERIFIED (PARTIAL): needs a baseline of past locations |
| U5 | `last_funding_type` Series A to D; `last_funding_at` in the last 90 days; S1 only | VERIFIED |
| U6 | Acquisition announced in the last 90 days where the acquirer passes the ICP filter | NOT VERIFIED: no tool in research. Verify before building |
| N1 | Google Places count for the brand, month-over-month increase; S3 only | NOT VERIFIED: needs a test |
| U7 | Job description contains any incumbent name; pair with U1 or U2 | VERIFIED (COMPOUND): secondary enrichment, never a mother intent |

### Killed

| Signal | Why |
|---|---|
| Close too long, audit coming, cards expiring, contract ending, shared-card fraud | Strongest reasons in the research (grade A), but not detectable from outside. Use as discovery questions (icp.md section 3b) |
| Regulation (1099 threshold, Nacha fraud monitoring, UK fraud offence) | Applies to a whole category at once; no per-company timing [mkt] |
| SAP ECC end of support | Enterprise only; SAP is not a Ramp accounting integration [sig 7.3] |
| AI token spend | Evidence is from existing Ramp customers; expansion signal, not new logo [sig 10] |
| Brex customers after the Capital One close | Ramp itself says no urgent need; who uses Brex cannot be detected [sig 1.2, sig 9] |
| Lookalikes of Ramp customers | No timing; used as list seeds instead (Matrix 1) |

### Universal vs niche

6 of 8 live signals are universal: one Clay build each, with keyword and industry swaps per segment (U1 to U4, U6, U7). U5 is universal in build but useful only for S1. N1 is the only niche build (S3).

### Signal x segment

| Signal | S1 Software | S2 Construction | S3 Healthcare |
|---|---|---|---|
| U1 Finance-ops hiring | Yes; add "Revenue Accountant" (INFERRED keyword) | Yes; add "Project Accountant" (INFERRED keyword) | Yes; add "Practice Finance" titles (INFERRED keyword) |
| U2 New finance leader | Yes | Yes | Yes |
| U3 Headcount growth | Yes | Yes | Yes |
| U4 New locations hiring | Yes (countries) | Yes (states) | Yes (states) |
| U5 Funding | Yes | No | No |
| U6 Acquisition | Low | Yes | Yes |
| N1 Location count | No | No | Yes |
| U7 Incumbent tool in job post | Compound | Compound | Compound |

---

## Build first: top five

1. **U1 Finance-ops hiring (17/20).** Highest score and the most volume. One build serves all three segments. The story writes itself from Brandt's choice to "add people, or redesign the process". Weakest on reason (vendor-blog evidence), so test it first and measure.
2. **U2 New finance leader (15/20).** Finds the champion directly (the Controller persona). The data is reliable and the opener is natural. Do not lean on the 90-day stat; test the window.
3. **U3 Headcount growth (15/20).** The only list signal with a customer quote naming it as the reason (TaskHuman). Pair with U1 for more context.
4. **U4 Hiring in new countries or states (15/20).** A customer-quoted reason (Notion), and Ramp's global card and reimbursement features fit. Lower volume, so run it as a smaller, high-relevance campaign, mainly in S1.
5. **U5 Funding, S1 only (13/20).** Cheapest, cleanest data, and Ramp already sells through VC channels ("Dedicated team to expedite underwriting for your portfolio") [sig 3]. Weak reason on its own, so stack it with U1 or U3.

U7 is not on the list on purpose: use it as a secondary enrichment on U1 and U2 to route the message ("moving off Expensify"). U6 and N1 wait until their data source is verified.

---

## Matrix 3: Workflow tracker

| W # | Status | Workflow name | Mother intent | Segments | Persona | Channel |
|---|---|---|---|---|---|---|
| W1 | Planned | Finance-ops hiring | Hiring specific roles | S1, S2, S3 | Controller, CFO | |
| W2 | Planned | New finance leader | New leadership | S1, S2, S3 | Controller, CFO | |
| W3 | Planned | Headcount growth | Hypergrowth (headcount) | S1, S2, S3 | CFO | |
| W4 | Planned | New country or state hiring | Hypergrowth (hiring velocity) | S1 first | CFO, Controller | |
| W5 | Planned | Funding round | Companies fundraising | S1 | CFO | |
| W6 | Planned (verify source) | Acquisition announced | Niche-specific play | S2, S3 | CFO | |
| W7 | Planned (verify source) | Practice location growth | Niche-specific play | S3 | CFO | |

Other tracker columns (campaigns, launch date, leads, results) are filled as campaigns launch.

---

## Open before building

- Pull a Clay count per signal per segment to replace the INFERRED Volume scores. This costs credits, so the cost will be estimated first.
- Backtest U1 to U5 on reference customers: did the signal fire before they bought?
- Verify the data sources for U6 and N1.
- Confirm Matrix 1 axes and the top five with sales.
