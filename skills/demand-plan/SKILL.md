---
name: demand-plan
description: >
  This skill should be used when the user asks to "design my demand plan",
  "how do we generate demand", "which channels should we invest in",
  "build our demand engines", "/gtm-planner:demand-plan", or needs the
  demand generation layer of a go-to-market plan. Fourth step of the Go2Rev
  methodology — selects demand engines and translates them into a channel mix.
metadata:
  version: "0.1.0"
  author: "RevOps Studio"
---

# Demand Plan

Design the demand layer of the plan in two connected levels:
**engines** (the repeatable mechanisms that generate demand) and
**channels** (where each engine runs). Engines are the what; channels are
the how. A channel list without engines is a wish list.

Respond in the language the user is writing in.

## Operating principles

- **Engines, not tactics.** An engine is a repeatable mechanism with inputs,
  outputs and operating logic. A tactic is a one-off action. The plan is
  built from 3–5 engines — never more. Catalog of common engine types in
  `references/engine-catalog.md`.
- **Triple fit screen.** Every candidate engine must pass: (1) coherence with
  the positioning — a "specialist in X" position cannot run undifferentiated
  mass-market engines; (2) operational viability — the team, budget and time
  the company actually has; (3) speed to first result — at least one selected
  engine must produce signal within the first 90 days.
- **Full-funnel coverage.** The selected engines together cover awareness →
  consideration → conversion → qualification. Five awareness engines and
  nothing else is not a system.
- **An engine the team cannot operate is an imaginary engine.** State the
  operating requirements (people, hours, budget, tools) for every engine.
- **Benchmarks only with sources.** Volumes, CPLs, conversion rates come from
  researched benchmarks with citations, or they are marked `needs-benchmark`.
  Never invent numbers. Rules in `references/benchmark-rules.md`.

## Process

1. **Load context.** Journey state + snapshot (constraints, team, budget,
   current funnel) + positioning (category, promise, ICP). If positioning is
   unconfirmed, warn and get explicit acceptance before proceeding.
2. **List candidate engines** (typically 6–10 from the catalog, adapted to
   this company). Screen each through the triple fit; discard failures with
   one line of reasoning — visible discards build trust.
3. **Select 3–5 engines** covering the funnel. For each: what it is, how it
   works operationally, funnel stage covered, inputs required, outputs
   produced, 3–5 health indicators, operating requirements, honest time to
   first result.
4. **Source readiness check.** Before benchmark research, run the check in
   `../market-map/references/source-readiness.md` (same pattern): confirm
   which of HubSpot, Ahrefs, Similarweb are actually authorized, tell the
   user what each unavailable source costs in precision, and offer the
   choice — web-research fallback, connect now, or manual data. Record in
   the journey state.
5. **Dispatch the benchmark-researcher agent** for the sector/channel
   benchmarks the design needs. If HubSpot is connected, calibrate against
   the real funnel; if Ahrefs/Similarweb are connected, ground organic and
   competitor-traffic assumptions.
6. **Translate engines into a channel mix** (3–6 channels). For each channel:
   which engine it serves, funnel function, weight (high/medium/low), phase
   (first 90 days / next quarter / later), organic vs. paid split and its
   logic, dominant messages (from the positioning pillars), indicative
   monthly investment range with stated assumptions, 3–5 health KPIs.
   Channel functions reference: `references/channel-functions.md`.
7. **Sequence activation.** Not everything starts at once: which engines and
   channels start in the first 90 days, which follow, and what each later
   activation is conditional on.
8. **State what this demand plan does NOT solve** — lead qualification
   handoff, sales process, measurement infrastructure — explicitly, one
   short section. These belong to execution readiness in the final plan.
9. **Coherence check:** engines consistent with positioning? Mix operable
   within declared constraints? Funnel fully covered? Every number sourced
   or flagged?
10. **Present + open questions.** On confirmation, update journey state and
   point to `/gtm-planner:roadmap`.

## Output structure

Sources used (one line) → Executive summary → Starting point (current funnel, constraints) → Design
principles (2–3, named) → Engine architecture (map, funnel coverage, how
engines feed each other) → Engine detail (3–5) → Channel mix (table +
per-channel detail) → Activation sequence → Operating requirements (team,
tools, budget ranges) → What this plan does not solve → Open questions.

## What NOT to do

- No lists of disconnected tactics.
- Never more than 5 engines or 6 channels.
- No engines the declared team and budget cannot operate.
- No invented benchmarks — `needs-benchmark` exists for a reason.
- No growth-hacking jargon; these are serious B2B companies.
- Do not proceed to roadmap without user confirmation.
