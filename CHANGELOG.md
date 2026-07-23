# Changelog

## 0.3.0 — 2026-07-23

Made the methodology more reviewable and more demonstrable:

- **`sample-output/`** — a complete, end-to-end sample case (fictional
  company, zero-connector mode): all five step outputs plus the
  consolidated GTM Plan.
- **Assumption & evidence ledger** — open questions now carry a confidence
  grade (high/medium/low) and their evidence; the final plan adds an
  evidence map (user-declared / tool / cited source / inference).
- **Decision gates in the orchestrator** — the journey does not advance to
  positioning, demand-plan or roadmap while gate-critical decisions
  (ICP, category, engine selection) rest on low-confidence assumptions;
  explicit user override is recorded as an assumption.
- **`connectors-and-permissions.md`** — per connector: what it adds, data
  read/written, access requirements, fallback when absent.
- **`demo-script.md`** — a 60–90s walkthrough that demonstrates method.
- README: "Why this is not a prompt pack" and review notes for
  marketplace/partner evaluation.

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
