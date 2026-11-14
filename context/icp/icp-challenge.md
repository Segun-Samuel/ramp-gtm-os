# Sceptical Head of Sales challenge: icp.md

Date: 2026-11-14. Target: icp.md draft v1. Result: icp.md draft v2.

Method: a separate reviewer, briefed as a sceptical Ramp Head of Sales, attacked v1 and spot-checked about 60 quotes and numbers against `context/docs/research/`. I re-checked its key factual claims against the research files before changing anything.

Reviewer verdict on v1: "Not yet." It described Ramp's customer base well but was not an outbound targeting spec.

## Challenges and responses

| # | Challenge | Severity | Verdict | Change in v2 |
|---|---|---|---|---|
| 1 | No ICP, only Ramp's market: every size band, ownership type and many industries; no primary segment. Ramp's SMB reps get only "about 10% of your closed-won customers" from outbound | Blocker | Accepted | Added the SMB outbound fact and a "Primary outbound segment: DECISION PENDING" table. Not resolved: the research does not pick a segment, so it needs an owner decision |
| 2 | The A-grade signals (close length, shared card, card expiry, contract end) can't be detected from outside the account | Blocker | Accepted | Split section 3 into 3a list triggers, each with the detection route named in sig 9, and 3b discovery pains for calls. Fire rate and cost marked Not found |
| 3 | Grades measured "appears in a Ramp case study", not "predicts a purchase"; several A rows rest on Ramp's blog or narration | Major | Accepted | Grades redefined: A = customer quote; B = Ramp narration, blog or guide; C = third-party or INFERRED. New finance leader, acquisition, ERP migration and contract end moved to B. Growth now uses TaskHuman's own quote. Bias and no-base-rate note added |
| 4 | Two A-grade cases were churn away from Ramp: Landry/French (Brex's "switched from Ramp to Brex" page) and Fyxer (left Ramp when it moved to the UK) | Major | Accepted, my error | Both moved to a new section 7, "Loss and churn patterns" |
| 5 | Negative and competitor evidence ignored (Trustpilot 2.7, incentivised reviews, Brex's loss reasons) | Major | Accepted | Bias note in "How to read"; section 7 lists loss patterns |
| 6 | The entity rule excluded Ramp's own public-sector customers | Major | Accepted | Entity rule limited to the commercial card path; public sector described as a separate motion and suppressed for this ICP |
| 7 | Not-fit list missed the exclusions that save rep time; some rows had no filter value | Major | Accepted | Section 6 split into Exclude, Suppress (existing customers, partner-sourced accounts, public sector, open opportunities and recent losses) and Qualify with care (rewards seekers, UK on NetSuite or Sage, Lightspeed, payroll). Dropped the India and New York stablecoin rows |
| 8 | Readiness tiers couldn't be filled from outbound data | Major | Accepted | Tiers 1 to 3 now map from list triggers; "Ready now" set only in discovery. Decay window left open for step 7 because no study supports a number |
| 9 | Mid-Market band came from a procurement posting; band variants omitted | Minor to major | Accepted | Each band now names its posting; added the 500+ and 2,500+ variants; working bands listed as an open question |
| 10 | Case-study headcounts are current size, not size at purchase | Minor | Accepted | Size caution added (Rarebreed: "7 locations when it joined Ramp in 2020") |
| 11 | SAP listed as a fit ERP but not a Ramp integration | Minor | Accepted | SAP row: Enterprise only, services-led; SAP ECC trigger graded B with no detection route |
| 12 | AI-spend signal is circular (data is from existing Ramp customers) | Minor | Accepted | Moved to a note as an expansion signal |
| 13 | Funding and finance-hire signals graded C but have the best detection | Minor | Partly accepted | Grades kept (no customer ties funding to buying); detection route shown next to each so step 7 can rank by detectability and evidence. Ramp's VC and PE channels noted |

## Factual mismatches found and fixed

| # | v1 said | Research says | Fixed |
|---|---|---|---|
| 1 | "Ramp prints no US cashback rate" | Ramp's versus pages: "Ramp is up to 1.5%" (Airwallex) and "Ramp's 1.5% has no excluded merchants" (Slash). Card and pricing pages print none [cmp 3, com 3] | Yes |
| 2 | Landry/French as a reason to buy | Brex's "Customers who switched from Ramp to Brex" [sig 2.10] | Yes |
| 3 | Fyxer "needed a new provider after moving to the UK" | It left Ramp because Ramp wasn't yet in the UK [sig 2.9] | Yes |
| 4 | Apprentice.io and Construction One Controllers as new-leader evidence | Apprentice.io: "No quote on his arrival"; Construction One narration doesn't say the Controller was new [sig 2.5] | Yes, removed |
| 5 | Strategic band without the 2,500+ variant; Mid-Market without its procurement source | Both in sig 4.1 | Yes |
| 6 | Brex count 5,500+ only | Ramp's switcher post also says "over 4,200" [cus 1.3, sig 1.6] | Yes |
| 7 | "WizeHire 12 days" as a close length | Customer said "closer to net 12 days"; "Month-end close stretched to 12 days" is Ramp's label [cus 7, sig 1.6] | Yes, quotes the customer |
| 8 | "3,200+ customers paying $100K+" | Coverage is ambiguous on whose revenue [cus 1.2] | Yes, ambiguity noted |
| 9 | $25,000 floor stated without conflicts | Ramp blog: "often $20,000 or more" [sig 1.1] | Yes |
| 10 | EIN quote attributed to the help centre | It is from ramp.com/startups [com 3] | Yes |

## Still open after the challenge

- ~~Pick the primary outbound segment (blocker).~~ Resolved 2026-11-14: the owner chose US Mid-Market; filters locked in icp.md section 1 (v2.1).
- Account count per filter, fire rate and cost per list trigger: need external data, and that costs money (Clay, treg or similar).
- Backtest the list triggers on 10 to 15 named reference customers.
- Decay window for triggers.
