# Sample output — Fluxen (fictional)

This folder shows what the Go-to-Market Planner actually produces, end to
end, for **Fluxen** — a fictional B2B SaaS company invented for this demo.
Any resemblance to real companies is coincidental.

**How it was produced:** the full journey (`/gtm-planner:plan`), running in
**zero-connector mode** — web research and user-declared inputs only. That
is deliberate: it shows the floor, not the ceiling. Note how estimates are
labeled, missing data becomes open questions with confidence grades, and
the source readiness check shapes what the planner claims vs. flags.

**The case:** Fluxen sells an energy-management SaaS for mid-size
manufacturing plants. €900k ARR, 11 people, founder-led sales, Valencia
(Spain). Goal: 8 new plants in 12 months. A deliberately imperfect input:
vague ICP, no CRM export, strong opinions, thin funnel data — the situation
this planner is designed for.

| File | Step | What to look at |
|---|---|---|
| `01-business-snapshot.md` | Intake | Declared vs. inferred discipline; confidence-graded open questions |
| `02-market-map.md` | Market Map | Three-layer competition; "do nothing" as the real rival; gap vs. hole test |
| `03-positioning.md` | Positioning | Category decision table; the pillar test applied; anti-messages bank |
| `04-demand-plan.md` | Demand Plan | Engines vs. tactics; visible discards; sourced benchmarks and `needs-benchmark` flags |
| `05-roadmap.md` | Roadmap | Result-milestones; capacity-limited 90 days; parked initiatives with reasons |
| `00-gtm-plan.md` | Final | The consolidated plan with assumption & evidence ledger and Execution Readiness |
