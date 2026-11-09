# Page blueprint · Step 4 · Demand Plan (one page)

The page blueprint: what goes on this page and in what order. Build it with the components in `assets/design-system.md`. Example values come from the fictional Fluxen case; none of them belongs in a real page.

## Slots

- Hero chain: the demand math the plan stated (e.g. opportunities last
  year → opportunities needed → the goal). Only numbers the plan contains.
- KPI strip: budget ceiling, planned mix spend, capacity limit, number of
  engines selected and discarded. Figures from the plan only.
- Engine architecture (.cov): one row per selected engine (3–5). Columns =
  the funnel stages the plan names. A covered stage gets `<span class="dot">`
  (primary) or `<span class="dot dot--low">` (secondary). "First signal" uses
  .signal with --from/--to as % of the scale shown in .signal-scale
  (default 0–180 days: 60 days = 33%, 90 = 50%, 150 = 83%). Scale labels
  must be evenly spaced values: 0 · 30 · 60 · 90 · 120 · 150 · 180.
- Engine cards: mechanism, health indicators, operating requirements, and
  every benchmark with its source state:
    cited → `<span class="src">Source, year</span>`
    no credible source → `<span class="chip chip--warn">needs benchmark</span>`
    assumption → `<span class="chip chip--warn">assumption</span>`
- Discards: every engine screened out, with its one-line reason and source.
- Channel mix: 3–6 channels; weight as meter (3 high · 2 medium · 1 low);
  phase chip; monthly cost with "(assumption)" when it is one.
- Activation sequence: first 90 days in .phase--now, then the later phases
  with what each is conditional on.
- "Does not solve": the short section from the plan, as a card.

## Structure

1. **Hero.** Eyebrow: GTM Planner · Demand Plan · [Company]. Status pill.
   Title with its second half in `.grad`; lede on what the engines run on;
   the goal chain on the right; the tabs in a `.tabs--row` below, Demand
   current.
2. **KPI strip** — 3–4 KPIs, the planned spend as accent.
3. **01 Design principles** — three cards, title + one line each.
4. **02 Engine architecture** — aside: how the engines feed each other.
   A `.cov` table: Engine · one column per funnel stage · First signal (30%
   wide). A last row holds only the signal scale, under the signal column.
5. **03 The engines** — aside "Every benchmark carries its source, or the
   flag that it has none". A grid of `.engine` cards (one per engine):
   label "Engine N · [time to first signal]", name, mechanism, **Health:**,
   **Runs on:**, then the `.meta` row of source lines and flags.
6. **04 Discarded, visibly** — aside "Screened out on positioning fit,
   operability or speed to first result"; a three-column grid of `.discard`
   blocks with reason and source.
7. **05 Channel mix** — aside "Where each engine runs"; table: Channel ·
   Engine · Weight (light meter) · Phase (chip) · Monthly cost.
8. **06 Activation sequence** — aside "Not everything starts at once";
   three `.phase` blocks, the first `.phase--now`.
9. **07 Open questions** — dark panel; a decision risk gets a `.risk` tag
   after the question.
10. **Foot** — note "**What this plan does not solve:** …"; sources line
    and "step 4 of 5".
11. **Credit strip**, campaign `demand-plan`.
