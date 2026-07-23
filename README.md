# Go-to-Market Planner

A [RevOps Studio](https://rev-ops.studio) plugin for Claude Cowork and Claude Code.

**Build a defensible go-to-market plan — positioning, demand engines, and a
90-day roadmap — with a methodology, not a template.**

Most GTM tools help you execute: write the email, enrich the lead, launch
the campaign. Almost none help you decide what all that execution should
serve. The result is familiar — busy channels, inconsistent messaging, and a
pipeline that depends on the founder's network.

Go-to-Market Planner works one level up. It walks you through the five
strategic decisions of a go-to-market plan using **Go2Rev**, the methodology
RevOps Studio uses with its B2B clients:

> **A GTM plan is a chain of decisions: category → promise → engines →
> channels → commitments. Each decision builds on the one before.**

## The journey

| Step | Command | You get |
|------|---------|---------|
| 1. Intake | `/gtm-planner:intake` | **Business Snapshot** — an honest, structured picture of your business today |
| 2. Market Map | `/gtm-planner:market-map` | **Market Map** — three layers of competition, positioning axes, real gaps vs. holes |
| 3. Positioning | `/gtm-planner:positioning` | **Positioning Architecture** — category decision, core promise, tested pillars, messages, anti-messages |
| 4. Demand Plan | `/gtm-planner:demand-plan` | **Demand Plan** — 3–5 demand engines and a phased channel mix with sourced benchmarks |
| 5. Roadmap | `/gtm-planner:roadmap` | **90-Day Roadmap + the consolidated GTM Plan** |

Or run the whole journey with one command:

```
/gtm-planner:plan Acme Logistics — B2B freight software, ~€2M ARR, Spain
```

Each step ends with a confirm-or-correct checkpoint. Your progress persists
between sessions, so the plan can be built across a week of short sessions.

## What makes it different

- **Engines, not tactics.** The demand layer is designed as 3–5 repeatable
  mechanisms with inputs, outputs and operating requirements — not a list of
  channels to "try".
- **The pillar test.** Every message pillar must be relevant to your ICP,
  differentiated from your mapped competitors, and defensible with evidence
  you have today. Two out of three gets cut.
- **Open questions, not invented data.** When information is missing or
  assumed, the planner says so — every gap becomes an open question with a
  recommendation, and unresolved ones travel into the final plan.
- **An honest ending.** The plan closes with an Execution Readiness section
  that maps what it deliberately does not cover — conversion design,
  deployment, measurement — and what capacity executing it requires.

## Connectors

The planner works fully with just web research and whatever materials you
share. Each connector adds grounding:

| Connector | What it adds | Used in |
|-----------|--------------|---------|
| **HubSpot** | Your real funnel: sources, conversion, cycle, deal sizes | Steps 1, 4 |
| **Notion** | Saves your GTM Plan and roadmap where your team works | Step 5 |
| **Similarweb** | Competitor traffic scale and channel mix. Requires API access (paid plan) | Steps 2, 4 |
| **Ahrefs** | Competitor organic footprint, keyword reality. Requires API access (paid plan) | Steps 2, 4 |
| Google Drive (native) | Your decks and docs as intake material | Step 1 |

None is required. Before researching, the market-map and demand-plan steps
run a **source readiness check**: they show which sources are available,
what each missing one costs in precision, and let you choose — web-based
deep research as fallback, connect the tool, or provide the data yourself.
Estimates are always labeled as estimates.

Run `/gtm-planner:setup` after installing for a guided walkthrough.

## See it before you run it

`sample-output/` contains a complete end-to-end case — a fictional company
taken through all five steps in zero-connector mode, including the
consolidated GTM Plan with its assumption & evidence ledger. If you read
one thing in this repo, read that. A 60–90s walkthrough lives in
`demo-script.md`.

## Quick start

1. Install the plugin and open Claude Cowork.
2. Run `/gtm-planner:intake` with your website URL — or just describe your
   company.
3. Confirm the Business Snapshot, then follow the journey. Most teams
   complete a full plan in 2–5 working sessions.

## Under the hood

**Skills** carry the methodology and orchestrate each step. **Agents** do
the heavy autonomous work — analyzing your materials, researching
competitors, sourcing benchmarks, and QA-ing the final plan — and always
show their sources. **Commands** are the explicit entry points. Progress
lives in `.claude/gtm-planner.local.md` in your project (template in
`settings/`).

```
skills/     setup · intake · market-map · positioning · demand-plan · roadmap
agents/     materials-analyst · market-researcher · benchmark-researcher · plan-qa
commands/   plan · intake · market-map · positioning · demand-plan · roadmap
```

## Why this is not a prompt pack

A prompt pack gives you words; this gives you an order of operations with
enforcement. The journey is gated — the planner will not advance to
demand design while the category decision rests on a low-confidence
assumption, and it will not consolidate a roadmap that ignores what the
market map flagged. Every output carries its evidence map (what came from
you, from tools, from cited sources, from inference), every assumption is
graded and tracked to resolution, and a QA agent checks the whole chain
for coherence before the final plan is assembled. You can fork the words;
the discipline is the product.

## Review notes (for marketplace & partner evaluation)

- **What it does:** turns incomplete GTM inputs into a staged, evidence-
  aware operating plan — five gated decisions, one consolidated document.
- **What it does not do:** execute campaigns, write outreach at scale, or
  replace the conversion/deployment/measurement workstreams (it maps them
  honestly in each plan's Execution Readiness section).
- **Data it touches:** user-provided materials; optionally HubSpot (read),
  Notion (write, user-directed), Similarweb/Ahrefs (read). Full detail per
  connector in `connectors-and-permissions.md`. No credentials handled by
  the plugin; OAuth is managed by the Claude client.
- **How it avoids invented data:** source readiness check before research,
  benchmark rules requiring citations, `needs-benchmark` and confidence
  grading, and a final ledger where every unresolved assumption is visible.
- **Uncertainty handling:** open questions with recommendations at every
  step; gates block silent progress on weak foundations; explicit user
  overrides are recorded, not hidden.

## About

Built by [RevOps Studio](https://rev-ops.studio), a revenue consultancy
for B2B companies. Go2Rev is the go-to-market layer of RevOS, the studio's
full revenue system — which also covers the conversion design, deployment
and measurement workstreams this plugin's plans point to.

The planner responds in your language, whatever language you work in.

MIT licensed. Issues and PRs welcome.
