---
name: plan
description: >
  This skill should be used when the user asks to "build my GTM plan", "run
  the whole journey", "do the full go-to-market plan", "take me through all
  five steps", "/gtm-planner:plan", or names a company and wants the
  complete go-to-market plan rather than one isolated step. Orchestrates the
  full Go2Rev methodology — intake, market map, positioning, demand plan,
  roadmap — one step at a time, with decision gates between them.
argument-hint: [company name or context]
metadata:
  version: "0.1.0"
  author: "RevOps Studio"
---

# The full Go2Rev journey

Run the five steps in order — intake → market-map → positioning →
demand-plan → roadmap — and deliver the consolidated GTM Plan at the end.

A GTM plan is a chain of decisions: category → promise → engines → channels
→ commitments. Each decision builds on the one before, so this skill does
not run the steps in parallel and does not let a weak link pass silently.

Respond in the language the user is writing in.

## Operating principles

- **One step at a time.** Execute the step's own skill, present its output
  summary and its open questions, and wait for the user's confirmation or
  corrections before moving on. Never chain two steps without a checkpoint.
- **Resume, don't restart.** The journey is designed to be built across
  several short sessions. Always pick up where the user left off.
- **Gates are not suggestions.** A gate-critical decision resting on a
  low-confidence assumption blocks the next step until it is resolved or
  explicitly overridden.
- **An override is recorded, not hidden.** The user can always overrule a
  gate. When they do, write it into the journey state as an `assumption`
  open question with low confidence, so it travels into the final plan.

## Process

1. **Locate the journey.** Read `.claude/gtm-planner.local.md` if it exists
   and resume from the first unconfirmed step. Tell the user where they are
   before doing anything else. If no state file exists, create it from
   `${CLAUDE_PLUGIN_ROOT}/settings/gtm-planner.local.md.example` once the
   first step is confirmed.
2. **Run the step** using its skill — `intake`, `market-map`,
   `positioning`, `demand-plan`, `roadmap` — following that skill's process
   exactly, with the context the user has given in the conversation (and
   any passed with the command: $ARGUMENTS).
3. **Checkpoint.** Present the output summary and the open questions the
   step raised. Wait for confirmation or corrections.
4. **Update the journey state** after every confirmation — status, date,
   output location, and any new or resolved open questions.
5. **Check the gate** before advancing (table below). When a gate fails,
   present what is weak, the options to resolve it, and that the user can
   override it explicitly — an override is recorded, not hidden. Don't
   advance on your own.
6. **Deliver the consolidated GTM Plan** after the roadmap step.

## Decision gates

| Advancing into | The gate |
|---|---|
| Positioning | The Business Snapshot's ICP section is confirmed, not a low-confidence assumption |
| Demand plan | The category decision is explicitly confirmed by the user — it conditions everything downstream |
| Roadmap | No unresolved low-confidence open question remains on category, ICP or engine selection |

## What NOT to do

- No running two steps back to back without the user's confirmation between
  them.
- No silent gate passes, and no advancing while a gate-critical decision is
  a low-confidence assumption.
- No overriding a gate on the user's behalf — an override is theirs to make
  and yours to record.
- No restarting a journey that already has confirmed steps in its state file.
- No consolidated plan before the roadmap step's coherence check has run.
