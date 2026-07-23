---
description: Build a complete GTM plan — all five steps, orchestrated
argument-hint: [company name or context]
---

Run the full Go2Rev journey for the user: intake → market-map → positioning
→ demand-plan → roadmap, in order.

Context provided: $ARGUMENTS

Rules of orchestration:

1. Read `.claude/gtm-planner.local.md` if it exists; resume from the first
   unconfirmed step. Tell the user where they are in the journey.
2. Execute one step at a time using the corresponding skill. At the end of
   each step, present the output summary and its open questions, and wait
   for the user's confirmation or corrections before moving on.
3. Update the journey state file after every confirmation.
4. Enforce decision gates between steps — do not advance silently:
   - Into positioning: the Business Snapshot's ICP section must be
     confirmed, not a low-confidence assumption.
   - Into demand-plan: the category decision must be explicitly confirmed
     by the user (it conditions everything downstream).
   - Into roadmap: no unresolved low-confidence open question may remain
     on category, ICP or engine selection.
   When a gate fails, present what is weak and the options to resolve it.
   The user can still override explicitly — record the override as an
   `assumption` open question with low confidence.
5. After the roadmap step, deliver the consolidated GTM Plan.

If no state file exists, create it from
`${CLAUDE_PLUGIN_ROOT}/settings/gtm-planner.local.md.example` after the
first step is confirmed.
