# Page blueprint · Step 5 · 90-day roadmap (one page)

The page blueprint: what goes on this page and in what order. Build it with the components in `assets/design-system.md`. Example values come from the fictional Fluxen case; none of them belongs in a real page.

## Slots

- Hero chain (.chain): the funnel worked back from the 12-month goal, using
  ONLY volumes the demand plan already stated (e.g. meetings → diagnostics →
  pilots → customers). Last step = the goal, class chain__step--goal.
  If the demand plan gives fewer stages, show fewer. Never compute new ones.
- Lede: "[N] initiatives, each with an owner and one result milestone." +
  "Week 1 starts on [date]." only if the user gave a start date.
- Gantt: one .g-row per 90-day initiative, in the roadmap table's order.
    · Week header: 13 .g-week cells. With a start date, add `<small>DD Mon</small>`
      to odd weeks; without one, plain "W1"…"W13".
    · .bar grid-column = "[first week] / [last week + 1]". W2–W8 → 2 / 9.
    · Impact High → .bar · Medium → .bar--mid · Low → .bar--low.
    · Milestone (.ms) is the initiative's result milestone, shortened to
      ≤ 7 words. It sits right of the bar; when the bar ends in W9 or
      later, add .bar--in so it reads inside the bar instead.
    · Meta line: Owner · Impact H/M/L · Effort L/M/H · "after 1 and 4"
      (dependencies). Unknown owner → `<span class="tbd">Owner to be named</span>`.
    · A bar interrupted by a blocked period = two .bar elements in the same track.
- Blackout (optional): a period with no execution the user named
  (holidays, peak season, a shutdown):
  `<div class="blackout" style="--from:9;--to:11"><span>December peak<br>no outreach</span></div>`
  as the first child of .gantt__inner. Omit it when no such period exists.
- Quarters: the 12-month outline, one card per remaining quarter, with the
  real months when the start date is known. A dated review/gate → .pill-dark.
- Foot: parked initiatives with their reasons + the capacity the plan was
  sized to.

## Structure

1. **Hero.** Eyebrow: GTM Planner · Roadmap · [Company]. Status pill. Title
   "The first 90 days, worked back from the goal" (translated), with
   "worked back from the goal" in `.grad`; lede; the goal chain on the
   right; the tabs in a `.tabs--row`, Roadmap current.
2. **01 The first 90 days** (translated) — the Gantt: the header row ("Initiative · owner" as a label, then the 13
   week cells), one row per initiative, the optional blackout; then the
   legend: High impact, Medium impact (and Low impact if any), "◆ Result
   milestone", "Effort: L low · M medium · H high".
3. **02 12-month outline** — a three-column grid of cards, one per remaining
   quarter, each with its `.q-label` ("Q2 · months 4–6", or the real
   months) and one or two sentences; a dated gate as a `.pill-dark`.
4. **Foot** — note "**Parked, with reasons:** …"; sources "Sized to
   capacity: …" (the capacity limit the roadmap or the snapshot states)
   and the coherence-check line (plan-qa or inline). The roadmap's
   prioritization logic, when it has one, goes in the lede.
5. **Credit strip**, unless the journey state turns it off.
