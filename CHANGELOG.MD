# Changelog

## 0.2.0 — 2026-07-22

Improvements from the first end-to-end field test:

- **Source readiness check** in market-map and demand-plan: before any
  research, the planner inventories available sources (connectors,
  materials, web), shows what tier of analysis each data need will get,
  and lets the user choose per gap — web-based deep research fallback,
  connect the tool, or provide data manually.
- **New `setup` skill** (`/gtm-planner:setup`): guided, pressure-free
  connector walkthrough after install, with honest access requirements.
- Documented that **Similarweb and Ahrefs connectors require paid API
  access**; research agents now open their reports stating source
  coverage, and web-research fallback is the explicit baseline.
- Step outputs open with a one-line "Sources used" note.

## 0.1.0 — 2026-07-21

Initial public release: 5 skills (intake, market-map, positioning,
demand-plan, roadmap), 4 agents, 6 commands, optional connectors
(HubSpot, Notion, Similarweb, Ahrefs), session persistence.
