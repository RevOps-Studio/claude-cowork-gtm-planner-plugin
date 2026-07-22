---
name: setup
description: >
  This skill should be used right after installing the Go-to-Market Planner
  plugin, when the user asks to "set up gtm planner", "configure the
  planner", "connect my tools", "/gtm-planner:setup", or asks which
  connectors they need for a GTM plan. Guides connector setup and sets
  expectations about what works without any connectors.
metadata:
  version: "0.2.0"
  author: "RevOps Studio"
---

# Setup

Guide the user through an honest, pressure-free setup of the Go-to-Market
Planner. Respond in the language the user is writing in.

## Core message first

Lead with this: **the planner works fully with zero connectors** — web
research plus whatever materials the user shares. Connectors upgrade
precision; they never gate the journey.

## Walk through the connectors

For each, state what it adds, what it requires, and let the user decide:

- **HubSpot** — real funnel numbers (sources, conversion, cycle, deal
  sizes) instead of declared ones. Requires a HubSpot account with access
  to the portal. Free to connect via OAuth. Most valuable single connector
  for steps 1 and 4.
- **Notion** — saves the GTM Plan and roadmap where the team works.
  OAuth, any Notion account.
- **Similarweb** — competitor traffic scale and channel mix (steps 2, 4).
  **Requires a Similarweb account with API access (paid)** — a free
  account is not enough. Without it, the planner falls back to web-based
  deep research with estimates labeled as estimates.
- **Ahrefs** — competitor organic footprint and keyword reality (steps 2,
  4). **Requires an Ahrefs plan with API access.** Same fallback logic.
- **Google Drive** (native Claude integration, no MCP needed) — lets the
  intake step read decks and docs directly.

## Set expectations

Explain the tiering plainly: with zero connectors the plan is built on web
research + declared data, and every estimate is flagged; each connector
removes flags and adds precision. The market-map and demand-plan steps run
their own source readiness check before researching, so the user can also
connect tools mid-journey and re-run only the affected research.

## Finish

Offer to create the journey state file (`.claude/gtm-planner.local.md`)
from `settings/gtm-planner.local.md.example`, record which connectors are
active, and point to the first step: `/gtm-planner:intake`.
