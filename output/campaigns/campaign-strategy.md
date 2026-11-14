# Campaign Strategy for Ramp

Status: v1, 2026-11-15. Built with `/campaign-strategy` from `CLAUDE.md`, everything in `context/` (icp.md v2.1, personas.md, signal-matrix.md, positioning, messaging, facts.md, case-studies.md, research) and `knowledge-base/playbooks/workflow-anatomy.md`. No web research this pass: everything comes from the Context OS.

**Target audience (given):** US Mid-Market (100 to 999 employees), privately held, in software, construction and healthcare. CFO or VP Finance buys; the Controller champions; AP and accounting ops influence. (icp.md section 1)
**Core value proposition:** a finance operations platform that builds control into every dollar spent and closes the books automatically, so the finance team saves time and money. (positioning.md, messaging.md)
**Key differentiators:** control before spend; one platform instead of a stack; agents that review every expense and code every transaction; switching in days. (positioning.md)

How to read:

- **Volume per month is not measured.** No list has been pulled yet. Every volume is a relative INFERRED estimate (High, Medium, Low) until a Clay count replaces it.
- **Ranking:** each idea gets a Signal score (1 to 5, how strongly the trigger points to a buying reason, using the A/B/C evidence grades in icp.md) and a Data score (1 to 5, how easily a tool detects it). Ideas are ranked by the total, then by Signal. The Tier also weighs volume, build time and differentiation.
- Proof names in any copy must come from `context/messaging/facts.md` (today: Foursquare, Brandt, TaskHuman, Perplexity).
- This is a portfolio exercise. Nothing here is sent under Ramp's name.

---

## Customer discovery analysis

Source: [case-studies.md](../../context/docs/case-studies.md), 57 stories with problem and result.

| Pattern | What the case studies show |
|---|---|
| Most common industries | Software & Technology (12 of 57), then Healthcare & Biotech and Fintech & Financial Services (5 each), Nonprofit and Construction & Engineering (4 each) |
| Company sizes | Ramp's labels: Mid-size 27, SMB 17, Enterprise 13 |
| Roles that bought | Controllers (Perplexity, Construction One, Seed, Barry's), CFOs (Broncos, Walther Farms, FirstBlood), VP Finance or Accounting (Brandt, New Way Landscape, Skin Pharm), founders and CEOs at SMB (Sandboxx, Eight Sleep, WizeHire) |
| Common problems | Tools that don't talk to each other; manual receipts and coding; a slow month-end close; shared or founder cards; audit prep; multi-entity sprawl |

**Targeting recommendation:** the v1 ICP holds. The research shows two strong audiences outside it: nonprofits (Ramp claims 10,000+ on its nonprofit page, and launched "Ramp for Nonprofits" in October 2026) and accounting firms as a channel (Ramp partners with "more than 4,500 accounting firms"). Both appear below as Creative (non-ICP) campaigns. Public sector stays out: it runs a separate motion with contract vehicles (icp.md section 1).

**Best customers for the Lookalike campaign:** Perplexity, Foursquare, Brandt, TaskHuman. All four are mid-size Software & Technology case studies and the only names approved in facts.md.

---

## Campaign ideas (ranked)

| Rank | Campaign | Targeting | Mother intent | Tier | Segment and persona | Signal and data source | Angle | Volume / mo (INFERRED) | Difficulty | Signal | Data |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | **Hypergrowth headcount** | Focused | Companies in hypergrowth (headcount) | **Tier 1**: customer-quoted reason, reliable data | All three segments; CFO, then Controller | Headcount up 20%+ in 6 months; Clay company headcount enrichment, monthly snapshots | Save time: a finance stack that scales with the team, not more finance hires (TaskHuman) | Medium | Medium (needs 6 months of snapshots) | 5 | 4 |
| 2 | **First hires in a new country or state** | Niche | Hypergrowth (hiring velocity), location variant | Tier 2: low volume | Software first; CFO | First job posts outside current locations, last 60 days; Clay "jobs growth by location" signal | Save time: one platform for spend in every country and currency (Notion) | Low | Medium (needs a location baseline) | 5 | 4 |
| 3 | **Finance-ops hiring** | Focused | Hiring specific roles | **Tier 1**: most volume, one build for all segments | All three; Controller, then CFO | Controller, AP, Staff Accountant, Accounting Manager, Procurement Manager roles posted in the last 30 days; Clay "Find Jobs at Company" | Save money: hire, or fix the workflow (Brandt) | High | Low | 3 | 5 |
| 4 | **First audit coming** | Niche | Hiring specific roles (keyword variant) | Tier 2: needs description parsing | Software; Controller | A Controller or Accounting Manager posting whose description mentions "first audit", "audit readiness" or "SOX"; job description text from Clay | Mitigate risk: audit evidence collected at the moment of spend | Low | Medium | 4 | 4 |
| 5 | **Case-study champions on the move** | Niche | Champion/user migration | Tier 2: very low volume, strong fit | Any ICP segment; the moved person | Finance people quoted in Ramp's public case studies who change company; LinkedIn job-change tracking (Clay "Find People") | Save time: bring the setup you ran before to the new company | Low | Low | 4 | 4 |
| 6 | **New finance leader, software** | Focused | New leadership (past 90 days) | **Tier 1**: spec approved, Clay build plan written | Software; the new CFO, VP Finance, Head of Finance or Controller | Trigger title started 0 to 90 days ago, joined from outside; Clay people search with start date | Save time: set the finance process before the team inherits the old one | Medium | Medium | 3 | 4 |
| 7 | **Golden ICP: new leader rebuilding the team** | Niche | New leadership + Hiring specific roles | Tier 2: subset of #6, low volume | Software; new CFO or Controller | Rank 6 plus 2+ finance roles open plus a named incumbent tool in the job posts; same sources | Save money: rebuild once, on one system, off {{incumbent_tool}} | Low | Medium | 4 | 3 |
| 8 | **Recently funded software** | Focused | Companies fundraising | Tier 2: weak reason on its own | Software; CFO or founder | Series A to D in the last 90 days or a new SEC Form D; Crunchbase `last_funding_at`, EDGAR | Save money: put the new runway to work with control from day one | Medium | Low | 2 | 5 |
| 9 | **ERP change underway** | Niche | Hiring specific roles (keyword variant) | Tier 2: keyword noise | Software and construction; Controller | Postings mentioning "NetSuite implementation", "ERP migration" or "Sage Intacct implementation"; job description text | Save time: line-level real-time sync to the new ERP from the start | Low | Medium | 3 | 4 |
| 10 | **New finance leader at a nonprofit** | Focused | New leadership (past 90 days) | Tier 2: outside v1 ICP | **Non-ICP**: US nonprofits, 100 to 999 staff; new Finance Director or CFO | Trigger title started 0 to 90 days ago; Clay people search | Mitigate risk: audit-ready grant and program spend (Ramp for Nonprofits) | Medium | Low (reuses the #6 build) | 3 | 4 |
| 11 | **New finance leader, construction** | Focused | New leadership (past 90 days) | Tier 2: thinner data (INFERRED) | Construction; new CFO or Controller | Same as #6 with construction industry filters | Save money: spend tied to every job before it overruns | Medium | Medium | 3 | 3 |
| 12 | **AI spend sprawl** | Niche | Hiring specific roles | Tier 3: expansion evidence only | Software; CFO | Several AI or ML engineer postings in the last 60 days; Clay job data | Save money: one view of AI spend across providers and API keys | Medium | Low | 2 | 4 |
| 13 | **Moving off a named tool** | Niche | Competitor customers | Tier 2: compound signal only | All three; Controller | Finance job posts naming Expensify, SAP Concur, Bill.com, Divvy or Navan; keyword match on job text | Save time: card, expenses and AP on one platform instead of {{incumbent_tool}} plus a card | Low | Medium | 2 | 3 |
| 14 | **Lookalike of software case studies** | Broad | Lookalike of customers | Tier 2: no timing signal | Software; CFO | Companies similar to Perplexity, Foursquare, Brandt and TaskHuman (industry, size, stage); Clay lookalike and company search | Save money: what a similar company got (named proof from facts.md) | High | Low | 1 | 4 |
| 15 | **Creative Ideas** | Broad | Niche-specific play | Tier 2: no timing signal, fast build | All three; CFO | Base ICP list; AI reads the prospect's website | Save time: three specific ideas for how Ramp fits their business | High | Low | 1 | 4 |
| 16 | **Accounting and fractional CFO firms** | Niche | Niche-specific play (partner) | Tier 3: channel play, slow | **Non-ICP**: firms serving mid-market finance teams; firm partner | Firms whose site lists NetSuite or Sage Intacct services (INFERRED source: firm websites via Claygent) | Make money: give clients a better finance stack (Ramp's 4,500+ partner firms) | Low | High | 2 | 3 |
| 17 | **Healthcare roll-up acquisitions** | Niche | Niche-specific play (M&A) | Tier 3: data source not verified | Healthcare; CFO | Acquisition announced in the last 90 days; press releases (no tool verified, signal-matrix U6) | Save time: a new entity on the books without a new finance hire (Align ENTA) | Low | High | 3 | 2 |
| 18 | **Practice location growth** | Niche | Niche-specific play | Tier 3: data source not verified | Healthcare; CFO | Location count rising month over month; Google Places via Clay HTTP (signal-matrix N1) | Save time: every location coded and closed in one place | Low | High | 2 | 3 |

**Required types:** Creative Ideas (#15), New Hire (#6, also #10 and #11), Lookalike (#14), Creative non-ICP (#10 nonprofits, #16 partner firms). **Golden ICP:** #7. **Creative stretch:** #4, #5, #9, #12.

---

## Campaign overviews (copywriter handoff)

1. **Hypergrowth headcount.** Hook: the company's recent growth, stated loosely ("your team has grown fast this year"). Personal element: headcount trend and current finance team size. Proof: TaskHuman's Controller, "We were growing too fast and needed a solution that could match that scale." CTA: offer the TaskHuman story. Different from #3: the trigger is company growth, not a finance job post.
2. **First hires in a new country or state.** Hook: their first postings in a new location. Personal element: the location and role. Proof: global card issuing and reimbursements (company.md); Notion is not an approved proof name yet, so no customer named until facts.md adds one. CTA: ask how they plan to pay and reimburse the new team.
3. **Finance-ops hiring.** Hook: the role they're hiring (`{{role_title}}`). Personal element: role title, number of finance roles open, current tool if named. Proof: Brandt's "instead of hiring our way through it". CTA: offer the Brandt story before the new hire starts. Run U1-team (2+ roles) before single-role rows.
4. **First audit coming.** Hook: the audit language in their own job post. Personal element: the posting's audit wording. Proof: Ramp's audit-ready evidence at the moment of spend (messaging pillar 1). CTA: "Worth a look before the auditors arrive?" (wording for copy, to be approved).
5. **Case-study champions on the move.** Hook: they ran Ramp at their last company. Personal element: previous company and new title. Proof: their own previous setup (only if their old company is a facts.md proof name; otherwise generic). CTA: offer a short call to set up the same thing. Ethics check before building: these are public case-study names; keep it respectful and low volume.
6. **New finance leader, software.** Already specced: `output/campaigns/new-finance-leader-software/workflow-spec.md` (6 cells, persona x hiring) with a Clay build plan. Next step is `/campaign-copy`.
7. **Golden ICP.** The TEAM_BUILD cells of #6 where the job posts also name a current tool: a new leader, rebuilding the team, on a named tool. Highest relevance, lowest volume. Build as a route inside #6, not a separate workflow.
8. **Recently funded software.** Hook: the round, briefly. Personal element: round type and date. Proof: Foursquare (spend control) or median savings claim from facts.md. CTA: soft question about spend controls as the team grows. Stack with #1 or #3 before sending alone.
9. **ERP change underway.** Hook: the implementation they're hiring for. Personal element: ERP name. Proof: Ramp's real-time sync claim (competitors.md). CTA: "Worth connecting before go-live?" Watch keyword noise.
10. **New finance leader at a nonprofit.** Same build as #6 with nonprofit filters. Proof: none approved yet (add a nonprofit customer to facts.md first). Angle from Ramp for Nonprofits: grant tracking and audit-ready records.
11. **New finance leader, construction.** The original Flow B version before the switch to software; the construction angles were approved during the spec session (job costing, crew cards, PO before payment). Needs construction proof names in facts.md first.
12. **AI spend sprawl.** Hook: their AI hiring. Proof: Ramp's AI Spend Management launch (free to start per coverage). Weak new-logo evidence (signal-matrix kills it as a trigger); keep as a test.
13. **Moving off a named tool.** Never a trigger on its own (signal-matrix U7). Use as a route in #3 and #6; as its own campaign only for a small test.
14. **Lookalike of software case studies.** Hook: "companies like Foursquare" style references, named only from facts.md. Personal element: the closest case study by size and model. CTA: offer that case study.
15. **Creative Ideas.** AI reads the prospect's site (locations, entities, travel-heavy roles, vendor-heavy product) and writes three specific ideas. CTA: "Would any of these be useful?" Broad, so expect lower reply rates.
16. **Accounting and fractional CFO firms.** Partner play: the firm brings Ramp to clients. Needs a partner programme to point to (Ramp's partnerships page). Slow and relationship-led; not a sequence-only campaign.
17. **Healthcare roll-up acquisitions.** Verify a programmatic M&A source first.
18. **Practice location growth.** Verify the Google Places count works for practice brands first.

---

## No-AI campaigns

**Finance hire or finance fix** (list from #3, TEAM_BUILD rows only)

- Why it works without AI: the list filter is the message. Every company on it is hiring several finance people right now.
- Core message: they're hiring for finance; Brandt chose to fix the workflow instead of hiring through it; one question asking whether that's worth a look. Static copy, first name and company only.

**Moving off Expensify** (list from #13, Expensify named in a finance job post)

- Why it works without AI: one named tool, one clear comparison.
- Core message: they're hiring someone to run expenses on Expensify; Ramp puts the card, expenses and bill pay on one platform; ask if a short comparison is useful. No pricing or cashback claims (facts.md ban).

---

## Front-end offer suggestions

1. **Finance team benchmark.** Ramp runs a quiz page: "Under 3 minutes to benchmark your finance org against 85,000+ companies." (voice.md section 10). Low-commitment and gives the prospect something about themselves first.
2. **Free plan or Plus trial.** Ramp's Free plan is "$0/mo/user", and Plus has a "free 30-day trial" (company.md section 3). Self-serve quick win: issue cards with built-in limits and watch receipts match within the trial.
3. **AI spend snapshot.** AI Spend Management is "free to start" per launch coverage (company.md section 2). One view of AI spend across providers is a fast, visible result for software companies (#12).

Note: "free" is a banned word in our copy (copy-bans.yaml). These offers can be described without the word ("no cost to start", "a 30-day trial").

---

## What to do next

- #6 is already specced and has a Clay build plan, so the next step for it is copy (stretch step 12, `/campaign-copy`).
- Of the other Tier 1 ideas, #3 (finance-ops hiring) is the cheapest to build and has the most volume. #1 (headcount growth) has the strongest evidence but needs six months of headcount snapshots before it can fire.
- Pull a Clay count for #1, #3 and #6 to replace the INFERRED volumes.
- Build one, launch, learn, then pick the next.
