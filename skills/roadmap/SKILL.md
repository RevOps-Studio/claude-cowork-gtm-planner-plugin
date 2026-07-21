---
name: roadmap
description: >
  This skill should be used when the user asks to "build my roadmap", "turn
  the plan into actions", "what do we do in the next 90 days", "prioritize
  initiatives", "/gtm-planner:roadmap", or wants to finalize a go-to-market
  plan. Fifth and final step of the Go2Rev methodology — prioritizes,
  sequences, and consolidates the full GTM Plan.
metadata:
  version: "0.1.0"
  author: "RevOps Studio"
---

# Roadmap + GTM Plan

Convert everything designed so far into an executable roadmap — prioritized
initiatives, sequenced, owned, with measurable milestones — and consolidate
the five steps into the final GTM Plan document.

A design without a roadmap is a paper system. A roadmap without a design is
a task list without a strategy. This step joins them.

Respond in the language the user is writing in.

## Operating principles

- **Impact × effort, with dependencies visible.** Initiatives are prioritized
  by impact on the plan's goals versus implementation effort, with blocking
  dependencies stated explicitly. Never impact alone.
- **Milestones are results, not activities.** "Launch the campaign" is not a
  milestone; "first 20 meetings booked from the campaign" is. One milestone
  per initiative — if it needs two, it is two initiatives.
- **Every initiative has an owner.** A named person or specific role — never
  "the marketing team". Unknown owner → `[OWNER TBD]`, visibly.
- **Capacity is a constraint, not a suggestion.** The first 90 days hold what
  the actual team can execute — typically 4–7 initiatives, not 20.
- **90 days in detail, 12 months in outline.** The near term is specific; the
  rest is directional and revisited after the first quarter's evidence.

## Process

1. **Load all confirmed outputs** — snapshot, market map, positioning,
   demand plan — plus every pending open question from the journey state.
2. **Extract candidate initiatives** from the positioning ("what this changes
   tomorrow") and the demand plan (engine activations, channel launches,
   required capabilities). Typically 10–20 candidates emerge.
3. **Score impact × effort**, note dependencies, and select: 4–7 initiatives
   for the first 90 days, the rest mapped to the 12-month outline or
   explicitly parked — with one line on why.
4. **Sequence** the 90 days respecting dependencies and capacity. Assign
   owners and one result-milestone per initiative.
5. **Dispatch the plan-qa agent** for the transversal coherence check: does
   the roadmap prioritize what the market map and positioning flagged? Does
   every selected engine have its activation initiative? Are critical open
   questions reflected? Fix what it finds before presenting.
6. **Build the consolidated GTM Plan** using
   `references/gtm-plan-template.md` — the five steps' confirmed outputs,
   the consolidated open questions, and the Execution Readiness section
   built per `references/execution-readiness.md`.
7. **Present the roadmap first, then the full plan.** On confirmation,
   update the journey state to complete. If Notion is connected, offer to
   save the GTM Plan and the roadmap table there. Offer XLSX/PPTX exports
   only if the user asks for them.

## Roadmap table format

| # | Initiative (result-phrased) | Source step | Impact | Effort | Owner | Depends on | Milestone | When |

## What NOT to do

- No 20-initiative first quarters.
- No default owners like "marketing" — role or name, or `[OWNER TBD]`.
- No activity milestones.
- No hiding parked initiatives — show them with the reason.
- Do not present the consolidated plan before the plan-qa check has run.
