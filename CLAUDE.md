# Ramp GTM Context OS

## Company

Ramp (https://ramp.com), New York. Finance operations platform: corporate cards, expenses, bill pay, procurement, travel, banking and accounting automation, sold to US, Canadian and UK businesses from startups to enterprise. 85,000+ customers and over $2B annualized revenue (Ramp, Oct 15, 2026). Sources: context/docs/research/company.md, checked 2026-11-14. ICP and buyers: context/icp/icp.md and context/icp/personas.md.

## How this folder works

Read the folders in this list when the task matches.

- CLAUDE.md: this map. Loads every session.
- README.md: what this repo is, for people who find it on GitHub.
- .claude/skills/: skills Claude runs, one folder each with a SKILL.md. Read when a task matches a skill.
- context/icp/: ICP, personas and signal matrix. Read before any targeting, list building or messaging.
  - icp.md: the ICP in five layers (firmographic, technographic, intent signals, persona, engagement readiness), who is not a fit, open questions.
  - personas.md: champion (Controller), economic buyer (CFO or VP Finance; founder or CEO at SMB), influencer (AP and accounting operations).
  - icp-challenge.md: the sceptical Head of Sales challenge on icp.md, with each response and fix.
  - signal-matrix.md: segments x personas with angles (Matrix 1), buying signals scored on the four tests (Matrix 2), top five to build first, workflow tracker (Matrix 3).
- context/positioning/: value proposition, positioning, competitors. Read before writing messaging or comparing to competitors.
  - value-proposition.md: job, pain, gain and proof for each persona.
  - positioning.md: category, target customer, today's alternative, unique value, proof, positioning statement.
  - competitors.md: main competitors, where Ramp wins and loses, how to respond.
- context/messaging/: core message, pillars, facts file. Read before writing any copy.
  - facts.md: the only source of names, numbers and claims for copy. Rows are usable only once the owner has approved them.
  - messaging.md: core message, four pillars with proof, angle per persona, words to use and avoid.
- context/brand-kit/: tone of voice and key phrases. Read before writing any copy.
  - brand.md: Ramp's tone of voice, key phrases and naming, from its own copy.
- context/docs/: GTM system architecture and case studies. Read when designing or changing a workflow.
  - gtm-system.md: the outbound system end to end (12 steps, tool and decisions per step, pillar check, open decisions).
  - case-studies.md: every customer story in the research (customer, size, industry, problem, result, quote, source).
- context/docs/research/: raw research, every fact with a source and a date. Read to check where a claim came from.
- knowledge-base/playbooks/: methods and templates. Read before building a matrix, a spec or a campaign.
- knowledge-base/learnings/: what worked and what did not. Read before repeating an experiment.
- meetings/: notes and transcripts. Read when a task refers to a call.
- output/campaigns/: everything Claude makes, one folder per workflow. Read when continuing a campaign.
  - campaign-strategy.md: 18 ranked campaign ideas with mother intent, tier, segment, signal, angle, volume and difficulty.
  - new-finance-leader-software/: workflow-spec.md (STRUCTURE-APPROVED) and its Clay build guide and flow diagram.
- tools/: scripts and helpers. Read before running any bulk data job.
- weekly-priorities/: one file per ISO week, linked to that week's work log. Read at the start of every session.
- work-log/: timestamped log of every change, same file name as the week's priorities. Append after every change.
- .env: API keys. Never committed, never read aloud, never pasted into a file.

## Skills

Pulled in from gtm-starter-kit (https://github.com/bolaji-ships/gtm-starter-kit). Each lives in .claude/skills/<name>/SKILL.md. Type / to list them.

From research to copy, in this order:

- signal-matrix: ICP segments, the buying signals that find them, and the 3 to 5 signals to build first.
- campaign-strategy: 15 to 25 outbound campaign ideas, each with a mother intent and a Tier 1 to 3 priority.
- build-workflow-spec: the structure of one workflow, with approval gates, saved as workflow-spec.md. Writes no copy.
- campaign-copy: cold email and LinkedIn copy from an approved workflow spec and verified facts only.
- miro-gtm-flowchart: draws the GTM system as an editable flow chart on Miro. Needs the Miro MCP connected.

Building in Clay (uses tools/rex):

- build-clay: build or audit an outbound workbook (Companies table, people sourcing, one shared People table).
- clay-build-plan: turns a workflow spec into a step-by-step Clay build guide plus a flow diagram. Writes instructions only.
- prompt-builder: per-row prompts for Clay AI columns, with JSON output, tested on the model that runs them.
- campaign-contract: writes contract.md, the build sheet for one Clay campaign.
- design-clay-table-json: writes the Clay table JSON from a contract.
- import-clay-table: imports that JSON into Clay, proves each paid column on one row, then checks the budget.
- save-clay-schema: saves an approved Clay table into the local registry.
- calculate-costs: what one Clay table actually cost in dollars and credits.
- workspace-cost-audit: what a whole Clay workspace spent in a month.
- export-tables: exports Clay tables to CSV.
- campaign-qa: checks a Clay table or sequencer campaign against its workflow spec before launch.

Research and deliverability:

- crawl4ai: crawls pages or whole sites into Markdown, free and local.
- agent-browser: drives a real browser to click, fill forms, log in and take screenshots.
- inbox-placement-test: tests where cold emails land (inbox, promotions or spam). Built for EmailBison and MailReach.

## Rules

- Cite a source (URL and date checked) for every company fact.
- Never invent numbers. If a fact cannot be found, write "Not found".
- Mark anything inferred as INFERRED.
- No em dashes in any copy.
- Ask before sending or publishing anything.
- Log every change in this week's work log.
- Keep keys, lead lists and personal data out of the repo.

## Tools

The tools used for GTM in this repo. Helper scripts live in tools/. Read tools/ before any bulk data job.

- Clay: enrichment tables and Claygent research. Claude works inside Clay through tools/rex (unofficial, uses my own browser session) and the Clay skills above.
- HubSpot: CRM. Where qualified leads and deals land.
- n8n: workflow automation between the tools. Trial starts in Week 4, not earlier.
- GitHub CLI (gh): creates and manages this repo and its pushes.
- Notion: where the finished work is published (step 14). Published copy: [Ramp GTM OS](https://app.notion.com/p/4197c7a1c9e081a9ac0eff2de67a48f3), a private page in my workspace, copied from GitHub on 2026-11-15. GitHub stays the source of truth; re-publish a page when its file changes.
- Miro: where the GTM system is drawn (step 13), through the miro-gtm-flowchart skill.
- treg (treg.to): catalog of external data and enrichment tools, used through the treg skill or the treg CLI. Scoped here to the treg project "Ramp GTM OS" (slug ramp-gtm-os) inside the growthpalx-team team, so calls bill to that team's balance. Before any call over $0.10, or any loop or batch, state the expected total and wait for my OK. Never run treg scan or treg upload in this repo, they read .env files.
