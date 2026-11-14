# Ramp ICP

Status: v2.1, 2026-11-14. Revised after the sceptical Head of Sales challenge ([icp-challenge.md](icp-challenge.md)). Primary segment locked: US Mid-Market (section 1). Built only from `context/docs/research/` (all sources checked 2026-11-14). Still needed before scale: account count, and fire rate and cost per signal (section 8).

How to read:
- Every row cites a research file and section: `com` = company.md, `cus` = customers.md, `cmp` = competitors.md, `mkt` = market.md, `sig` = signals.md, `voi` = voice.md. The URL and check date sit next to the fact in that file.
- Quotes are verbatim from the research file. Customer metrics and switcher counts are Ramp's own claims.
- **Bias:** nearly all trigger evidence comes from Ramp-published wins, so it is vendor-selected. No base rate exists: we never see how many companies with the same trigger did not buy. Most review-site quotes are labelled "Incentivized" (30 of 33 on TrustRadius; every Findstack review). [sig 2, cus 6.5, cus 6.6]
- INFERRED = my reading of the evidence, not stated by a source. Not found = the research looked and found nothing.
- Personas: [personas.md](personas.md).

---

## 1. Firmographic

### Size bands Ramp uses (from its job postings)

| Band | Wording and the posting it comes from | Source |
|---|---|---|
| SMB | "businesses with up to 150 employees", sold to "founders, CEOs, and finance leaders" (Account Executive, Inside Sales) | sig 4.1 |
| Mid-Market | "typically 100 to 999 employees, $50M to $100M in revenue" (a procurement product posting, not a sales posting) | sig 4.1 |
| Enterprise | "750+ employees" (Account Manager, Enterprise); also "Enterprise or large Mid-Market accounts (500+ employees)" | sig 4.1 |
| Strategic | "5,000+ employees" (SDR, Strategic); "6,000+ employees / Fortune 1000" (AE, Strategic); "2,500+ employees or Fortune 1000" (AM, Strategic) | sig 4.1 |

- The bands overlap and vary by posting, so we need our own working bands (section 8).
- SMB is mostly not an outbound motion at Ramp: SMB reps close "50–60 new customers a month per rep" and self-source "about 10% of your closed-won customers" through outbound. [sig 4.1]
- Mid-Market SDRs work from signals: "Build account strategies using company context, growth signals, financial workflows, and stakeholder priorities." [sig 4.1]
- Enterprise traction: "100%+" year-over-year enterprise growth and 3,200+ customers at $100K+ "in annualized revenue" (June 2026); that group up 113% (Oct 2026). Whether $100K is Ramp's revenue from the customer or the customer's own revenue is ambiguous in the coverage. [com 4, cus 1.2]
- Public sector (government and education, 1,600+) runs as a separate motion: contract vehicles "Carahsoft, OMNIA Partners, Velocity1" and dedicated SLED and Federal AEs. Out of scope for this ICP unless chosen. [com 2, sig 4.1]

### Primary outbound segment v1: US Mid-Market (LOCKED 2026-11-14)

Chosen by the owner on 2026-11-14 over Enterprise (fewer accounts, long implementations, services-led) and SMB (Ramp's own SMB motion gets about 10% of wins from outbound). Why Mid-Market: Ramp's Mid-Market SDRs already sell on "growth signals", and most named switcher stories are mid-size. [sig 4.1, sig 1.6, cus 7]

**List filters** (pull the list with these; all must pass)

| Filter | Value | Basis | Source |
|---|---|---|---|
| HQ country | United States | Home market; full product and ERP coverage. Canada (live since July 2026) and the UK (Xero and QuickBooks only at launch) are later segments (INFERRED choice) | com 4 |
| Employees | 100 to 999 | Ramp's Mid-Market wording "typically 100 to 999 employees". Overlaps Ramp's Enterprise "750+"; we keep 750 to 999 in this segment | sig 4.1 |
| Industry | 1) Software and technology; 2) Construction and engineering; 3) Healthcare (practices, multi-location providers, healthcare services) | Each has a Ramp industry page or segment claim and named mid-size case studies: software (Perplexity, Foursquare, Brandt, ElevenLabs); construction 5,500+ (Construction One, SAM Construction Group); healthcare 2,500+ (SAMGI, Candid, Align ENTA, Rarebreed). Choice of these three is INFERRED. Map to the data provider's industry taxonomy at build time | cus 1.4, cus 2, cus 5.2 |
| Company type | Privately held, for-profit company | Commercial card path; public sector runs a separate motion; nonprofits have their own Ramp package and are a candidate for a later segment (INFERRED choice) | com 2, cus 5.2 |

**Qualify filters** (enrich or confirm before outreach; drop the account if it fails)

| Filter | Pass | Basis | Source |
|---|---|---|---|
| Not already on Ramp | Not a Ramp customer, not partner-sourced, no open opportunity or recent loss | Section 6, Suppress | cus 1.1, sig 3 |
| Cash | Likely $25,000+ in US bank accounts (any funded or revenue-generating mid-market company should clear this; INFERRED) | Help-centre eligibility | com 3 |
| GL / ERP (if known) | NetSuite, Sage Intacct or QuickBooks Online; in construction also Sage 100 Contractor, Sage 300 CRE, Sage Intacct Construction, Viewpoint Vista or Spectrum, CMiC, Acumatica | Supported on the Free or Plus plan, or listed on the construction page. Unknown ERP does not disqualify, because ERP detection is not solved (section 2) | com 3, cus 5.2, sig 9 |
| Not a SAP, Oracle Fusion or Workday shop | Those point to Enterprise-tier pricing and services | Enterprise plan and SAP consultants | com 3, sig 4.1 |

**Positive fit markers** (raise priority; not required)
- Multiple entities, locations or subsidiaries. [sig 2.9, sig 6.2]
- Small finance team relative to headcount (no threshold in the research). [sig 2.1]
- Remote or travelling staff. [sig 1.6, sig 2.8]

Account count for this filter set: Not found; to pull in step 7.

### Fit criteria (commercial card path)

| Attribute | Fit | Evidence | Source |
|---|---|---|---|
| Legal entity | US-registered corporation, LLC or LP, with an EIN | Help-centre eligibility. Ramp's startups page: "Having an EIN does not guarantee approval." | com 3 |
| Cash | $25,000+ in a linked US bank account (CA$25,000 in Canada) | Help centre. Conflicts: Ramp's blog says cards fit companies with a US bank balance "often $20,000 or more"; a third-party review says "$75K or more in annual revenue" | com 3, sig 1.1 |
| HQ | US; Canada since 2026-07-28 (not Quebec or Saskatchewan); UK since 2026-09-15 | EU-headquartered businesses: waitlist; live EU countries Not found | com 4 |
| Ownership | VC-backed, PE-backed and bootstrapped all appear | VC and PE partner programmes; "more than half of the companies in the Forbes AI 50 run on Ramp"; Rarebreed has a PE sponsor; SwagUp is "bootstrapped" | sig 3, cus 1.3, cus 2, cus 3.28 |
| Industry (Ramp pages with counts) | Construction 5,500+; nonprofits 10,000+; healthcare 2,500+; sports 1,900+; law "thousands"; software and AI (no count) | Counts printed on Ramp's own pages | cus 1.4, cus 5.2 |
| Structure | Several entities, locations or subsidiaries | Heyday 30 entities; SAM Construction 11; Betterment 5 subsidiaries; Long Meadow Ranch "five different companies"; Align ENTA started on "five instances of QuickBooks" | sig 2.9, sig 6.2 |
| Distribution | Remote or travelling staff | FirstBlood across 9 time zones; Prosper about 25% remote; Liquid Measurement fraud on its "oft-traveling" BD team | sig 1.6, sig 2.8 |
| Finance team | Small relative to headcount | Attio: 3 in finance for about 160 staff; Broncos: about 10 in finance across 5 entities; City of Ketchum: 4 for 18 departments; Construction One: 90 staff, "a lean finance team" | sig 2.1, cus 2, sig 2.5 |

Size caution: case-study headcounts are today's size, not size at purchase. Rarebreed is 3,000+ employees now but had "7 locations when it joined Ramp in 2020" and about $40M revenue at the time of its card-limit problem. Size at purchase is Not found for most references. [cus 3.28]

---

## 2. Technographic

| Signal | What it looks like | Evidence | Source |
|---|---|---|---|
| GL / ERP | QuickBooks Online or Xero (Free plan); NetSuite or Sage Intacct (Plus); Workday or Oracle Fusion (Enterprise); construction ERPs such as Sage 100 Contractor, Viewpoint Vista and Spectrum, CMiC | Plan tier follows the ERP; "40+" accounting systems supported | com 3, sig 7.3, cus 5.2 |
| SAP | Enterprise only, services-led | Ramp hires SAP S/4HANA technical consultants, but SAP is not in Ramp's accounting integration list (only "SAP SuccessFactors" under HR). The SAP ECC end-of-support trigger ("forced migration decision") is Ramp's blog, grade B, no customer quote | sig 4.1, sig 7.3, sig 1.1 |
| UK stack | Xero or QuickBooks | UK launch lists accounting automation with Xero and QuickBooks; UK Plus is "Custom" | com 4, com 3 |
| Fragmented spend stack | Separate tools for card, expenses, AP and travel | Ramp: "your finance team is logging into four different platforms"; Studs: "We've consolidated four platforms into one with Ramp."; Sandboxx CEO lost hours each month across Expensify, Amex and Bill.com | sig 1.6, voi 1, cus 7 |
| Displaceable incumbent | Brex, Amex, BILL or Divvy, SAP Concur, Expensify, Chase and other bank cards, Coupa, Navan, Zip | Ramp runs versus pages for 34 competitors and switcher posts for 8. Ramp's own counts disagree between pages: Brex 5,500+ (versus page) and 4,200+ (switcher post); Amex 18,000+ and 11,500+; Concur 5,200+; Bill 17,000+; Expensify 1,900+ | cmp 3, sig 1.6, cus 1.3 |
| Spreadsheets as the system | Expenses or approvals run in Google Docs, Sheets, Excel or Slack | Construction One ran on "75 Google Docs"; Evans Hotels: "The goal was to get rid of all those Excel spreadsheets," | sig 2.5, cus 7 |
| Shared or founder card | One card used by many staff | WizeHire: "everyone was sharing one AmEx card"; JDC Power Systems: "We were using the founder's Amex card," | cus 7 |

- Detection: back-office ERPs and spend tools are hard to see from public web pages (UNVERIFIED third-party summary). BuiltWith's page does not mention accounting or ERP. Coverage of HG Insights or BuiltWith for these tools: Not found. Job posts that name the ERP are one route. [sig 9]
- AI spend is an expansion signal, not a new-logo signal: the 66.7% Mid-Market AI adoption figure and the AngelList quote are about existing Ramp customers. [sig 10]

---

## 3. Intent signals

Grades: **A** = a customer quote names it as the reason or the problem. **B** = Ramp narration, blog or guide. **C** = third-party, or the link to buying is INFERRED. Fire rate and cost per signal: Not found in the research; to measure in step 7.

### 3a. List triggers (can be seen from outside the account)

| Trigger | Evidence | Grade | Detection route named in research | Source |
|---|---|---|---|---|
| Headcount growth | TaskHuman: "We were growing too fast and needed a solution that could match that scale," UpEquity grew "from 20-25 employees to 80+" (narration) | A | Clay job-post signals such as "Find company jobs growth by department signal" | sig 2.1, sig 9 |
| International expansion | Notion: "Our previous vendor wasn't able to service our entire employee base," | A | Clay "Find company jobs growth by location signal" | cus 3.1, sig 9 |
| New finance leader (CFO, VP Finance, Controller) | Narration only: "As soon as Assistant Controller Tim Borse joined MAGNA-TILES, he knew the company needed a better corporate card system." No customer quote ties arrival to buying; Ramp content linking a new CFO to switching: Not found | B | LinkedIn Sales Navigator, UserGems job changes | sig 2.5, sig 5, sig 9 |
| Acquisition, new entities | Ramp: "Every acquisition adds entities, GL structures, approval chains, and local compliance requirements." Align ENTA's quote describes the result, not the reason | B | Press announcements | sig 1.1, sig 2.9, sig 9 |
| Incumbent acquired or restructured | Capital One closed Brex 2026-04-07; BILL explored a sale (Nov 2025) and cut up to 30% of staff (May 2026); Divvy became BILL Spend & Expense (2022); Paylocity bought Airbase (2024). Ramp itself: "Finance teams using Brex don't need to make a move yet." | B | Event: press. Which accounts use the incumbent: Not found | cmp 1, sig 1.2, sig 7.1 |
| Legacy ERP end of life (SAP ECC) | Ramp blog only; Enterprise only | B | Not found | sig 1.1 |
| Funding round | TaskHuman "entered a phase of hypergrowth" after its Series B (narration). No customer quote ties funding to buying. Ramp does build channels around funded companies: "Dedicated team to expedite underwriting for your portfolio" | C | Crunchbase `last_funding_at`; SEC Form D (filed "within 15 days after the first sale") | sig 2.2, sig 3, sig 9 |
| Finance or procurement role posted | Vendor blogs (Salesgear) call Controller and Procurement Manager postings a signal; no Ramp source | C | Clay job-post signals, public ATS feeds | sig 4.2, sig 9 |
| Regulation | 1099 threshold up to $2,000 for payments after 2025; Nacha ACH fraud monitoring Phase 2 in force 2026-06-19; UK failure-to-prevent-fraud offence for large organisations since 2025-09-01 | C (INFERRED link) | Applies by category, not by event | mkt table, mkt 1.9 |

Do not use: "new executives spend 70% of budget in the first 100 days" (untraceable) or UserGems' "2.5X" (no method). [sig 5]

### 3b. Discovery pains (not visible from outside; use on calls)

| Pain | In the customer's words | Grade | Source |
|---|---|---|---|
| Audit coming or failing | Fi: "The biggest pain point for us is the audit issue,"; Dragonfly Pond Works: "We wanted to ensure that we were always audit ready, with receipts and coding for all of our spend," | A | sig 2.3 |
| Close too long | Walther Farms CFO: "It was like finding a needle in a haystack each month,"; WizeHire: "Prior to Ramp, we were actually closer to net 12 days". Day counts for Mix Talent ("past 10 days") and Zola (20 to 25) are Ramp labels | A | sig 2.7, cus 7, sig 1.6 |
| Growing without adding finance staff | Brandt: "instead of hiring our way through it, we fixed the workflow so we can keep supporting the organization as we scale." | A | sig 2.1 |
| ERP sync unreliable | 8VC: "We couldn't be sure that we had captured all our expenses until the statements were received." | A | sig 2.6 |
| Card or bank deadline, limit too low | SAMGI: "We had just two weeks before most of our previous bank cards expired,"; Liquid Measurement: "We knew it was time to look for a new bank, and with that came the need to look for a new credit card system"; Rarebreed: "We had a $30,000 monthly limit for a $40M revenue business," | A | sig 2.8, cus 7 |
| Fraud on shared cards | WizeHire: "one fraud event would literally just ruin thousands of transactions that we have set up," | A | sig 2.8 |
| Tools that don't connect | Denver Broncos CFO: "Every one of those tools was a reasonable choice on its own but they didn't talk to each other." | A | cus 7 |
| Contract ending | Betterment narration: "As their contract with their previous platform drew to a close"; Ramp: a renewal leaves time for a full RFP, an acquisition needs a faster process | B | sig 2.6, sig 1.1 |
| First audit drives controller hiring | Ramp's former Senior Controller (2021): "Nine times out of 10, you're hired because your company is facing its first audit." Explains why controllers get hired, not why companies buy | B | sig 4.2 |

---

## 4. Persona (buying group)

Full profiles: [personas.md](personas.md).

| Role | Who | Evidence | Source |
|---|---|---|---|
| Champion | Controller family | "Every controller's performance is measured by how fast and how accurately the books close." | sig 1.1 |
| Economic buyer | CFO or VP Finance (founder or CEO only at SMB, outside the v1 segment) | SMB reps sell to "founders, CEOs, and finance leaders"; postings name "CFOs and Controllers" | sig 4.1 |
| Influencer | AP and accounting staff who do the daily work | AP Manager, Staff Accountant, Senior Accountant and Accounting Associate voices in case studies | cus 3, cus 7 |
| Other voices | Legal, security, risk, IT, business operations | Ramp: "Your Legal and Security teams lack visibility"; quotes from Prosper's Director of Enterprise Risk Management and Foursquare's Head of Business Operations | sig 1.1, cus 3.40, voi 1 |

---

## 5. Engagement readiness

The tiers are INFERRED; each input is sourced. Outbound data can only place an account in Tier 1 to 3. "Ready now" is confirmed on a call.

| Tier | Set from | Looks like | Evidence |
|---|---|---|---|
| Ready now | Discovery | A section 3b pain with a date attached (cards expiring, contract ending, audit booked, ERP go-live) and an owner in seat | SAMGI's two-week card deadline; Betterment's contract end [sig 2.8, sig 2.6] |
| Tier 1 | List data | In the US Mid-Market segment, not suppressed, plus a grade A list trigger (growth, international expansion) or a new finance leader | Section 3a |
| Tier 2 | List data | In segment, not suppressed, plus a B or C list trigger only (acquisition, incumbent event, funding, finance role posted) | Section 3a. Ramp on incumbent events: "For teams already experiencing friction, these moments can bring existing challenges into sharper focus." [sig 1.6] |
| Tier 3 | List data | In segment, not suppressed, no trigger | Ramp: "Manual work is usually what pushes you to switch expense platforms, not one dramatic failure, but the slow buildup of receipts, coding, and reconciliation that eats into every close cycle." [sig 1.6] |

- How long a trigger stays live: no reliable study. The decay window is set in step 7 and tested. [sig 5]
- What lowers the cost of a yes: "Most finance software takes months to implement. Ramp only takes days."; "Teams typically launch Ramp with a small pilot group and go live in under 2 weeks."; Pair Eyewear: "The process took about a month." [sig 1.3, cus 7]
- Why buyers switch spend tools, per a third-party review study: usability or a dated interface first, support second. [sig 7.2]

---

## 6. Not a fit

### Exclude

| Who | Why | Source |
|---|---|---|
| Not a US-registered corporation, LLC or LP, or under $25,000 cash in a linked US bank account (CA$25,000 in Canada) | Fails card eligibility (commercial path; public sector is a separate motion) | com 3 |
| HQ outside the US, Canada and UK, or in Quebec or Saskatchewan | Not available yet; EU is a waitlist | com 4 |
| Wants to carry a card balance or finance purchases on the card | Charge card with 30-day payback; "we do not profit from charging interest on carried balances" (fit conclusion INFERRED) | com 3 |
| Wants AR only | AR is "currently not available as a standalone product"; supports only QuickBooks Online and NetSuite | com 2 |

### Suppress (protects rep time)

| Who | Why | Source |
|---|---|---|
| Existing Ramp customers | 85,000+ already on Ramp | cus 1.1 |
| Accounts reached through Ramp partners | VC partners (8VC, Alpine, CoreTrust, BTV), PE partners, 4,500+ accounting firms and bank partners such as Hingham ("two dozen+" commercial clients moved via its programme). Channel conflict is INFERRED | sig 3, cus 1.4 |
| Public sector | Separate motion with its own contract vehicles and AEs | com 2, sig 4.1 |
| Open opportunities and recent losses | Needs CRM data; not in the research (INFERRED rule) | n/a |

### Qualify with care

| Who | Why | Source |
|---|---|---|
| Buyers who choose a card for points or the highest cashback | Ramp's own versus pages: "Airwallex advertises up to 2% cashback. Ramp is up to 1.5%." and "Ramp's 1.5% has no excluded merchants". Ramp's card and pricing pages print no rate. Brex says customers left Ramp for "more rewards and rebates" | cmp 3, com 3, sig 2.10 |
| UK companies on NetSuite or Sage | UK launch lists accounting automation with Xero and QuickBooks only | com 4 |
| Retailers on Lightspeed | "It does not integrate with Lightspeed so you need to use a universal csv process" | cus 6.3 |
| Buyers who want payroll in the same tool | Weak evidence: Capterra search snippets note no payroll; Ramp calls Rippling "an HR and IT platform" (INFERRED) | cus 6.2, cmp 3 |

---

## 7. Loss and churn patterns

Mostly competitor marketing (Brex) or unmoderated reviews; weight unknown.

| Pattern | Evidence | Source |
|---|---|---|
| Support delays | Landry/French Construction left Ramp for Brex after a new CFO joined: "Ramp customer service left them waiting weeks"; "Regaining the login took three weeks". Trustpilot 2.7 out of 5, 34% one-star, themes: support, vendor-payment delays, fund holds | sig 2.10, cus 6.4 |
| Wanted more than cards | Numeral: "Ramp felt designed around card management but not really spend management". Brex's framing: companies left "because they wanted more. More spend controls, more rewards and rebates, more countries and currencies supported." | sig 2.10 |
| Banking and credit limit | Chargeback: "The lack of a combined banking and credit card system was a killer for us" and "We wanted a credit limit that reflected our cash balance" (Ramp now sells banking; date of Chargeback's move Not found) | sig 2.10, com 2 |
| Country coverage | Fyxer used Ramp in the US, then switched providers when it moved to the UK, where Ramp wasn't yet available (Ramp launched in the UK on 2026-09-15; Fyxer is now named as a UK customer) | sig 2.9, com 4 |

---

## 8. Open questions

Needed before scaling outreach:
- Account count for the US Mid-Market filter set: Not found; needs a data source.
- Industry codes: map the three industries to the data provider's taxonomy.
- Fire rate and cost per list trigger: Not found; to measure in step 7.
- Backtest: for 10 to 15 named reference customers, did the list triggers fire before they bought? Needs public dates (funding, LinkedIn start dates).

Other:
- ACV by segment: only an older mirrored Mid-Market AE posting says "about 50K in ACV". [sig 4.1]
- Customer count by segment: Not found. [cus 8]
- Underwriting floor: $25,000 cash (help centre) vs "often $20,000 or more" (Ramp blog) vs "$75K or more in annual revenue" (Makerstack). [com 3, sig 1.1]
- Plus platform fee "based on team size": not published. [com 3]
- Brex churn after the Capital One close: no layoffs, price changes or product sunsets found. [sig 7.1]
- Next EU countries: Not found. [com 4]
