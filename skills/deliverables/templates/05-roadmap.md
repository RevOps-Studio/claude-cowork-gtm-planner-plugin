# Template · Step 5 · 90-day roadmap (one page)

Body fragment that follows the design system (`assets/design-system.md`). Replace ALL Fluxen content.

Slots
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
      ≤ 7 words. It sits right of the bar; when the bar ends after W8, add
      .bar--in so it reads inside the bar instead.
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

## Body

Everything inside the block below is the page body that follows the design
system. Write it out with this company's content; never copy the block's
example content.

```html
<title>90-day roadmap — Fluxen</title>
<meta name="description" content="90-day GTM roadmap for Fluxen, built with GTM Planner (Go2Rev methodology).">
</head>
<body>
<header class="hero">
  <div class="wrap">
    <div class="hero__top">
      <div class="eyebrow"><span>GTM Planner</span><span>Roadmap</span><span>Fluxen</span></div>
      <div class="status">Example · fictional company · figures invented</div>
    </div>
    <div class="hero__body">
      <div>
        <h1 class="hero__title">The first 90 days, <span class="grad">worked back from the goal</span></h1>
        <p class="hero__lede">Six initiatives, each with an owner and one result milestone, sized to what the founder can carry.</p>
      </div>
      <div class="chain" aria-label="Funnel worked back from the goal">
        <div class="chain__step"><b>32–40</b><span>qualified opps</span></div>
        <span class="chain__arrow">→</span>
        <div class="chain__step"><b>~1 in 4</b><span>proposals close</span></div>
        <span class="chain__arrow">→</span>
        <div class="chain__step chain__step--goal"><b>8</b><span>new plants</span></div>
      </div>
    </div>
    <nav class="tabs tabs--row" aria-label="Plan deliverables">
      <a data-tab="01" href="01-business-snapshot.html">1 Snapshot</a>
      <a data-tab="02" href="02-market-map.html">2 Market</a>
      <a data-tab="03" href="03-positioning.html">3 Positioning</a>
      <a data-tab="04" href="04-demand-plan.html">4 Demand</a>
      <a data-tab="05" href="05-roadmap.html" aria-current="page">5 Roadmap</a>
      <a data-tab="00" href="00-gtm-plan.html">GTM Plan</a>
    </nav>
  </div>
</header>

<main class="wrap">
  <section class="section" aria-label="90-day plan">
    <div class="gantt"><div class="gantt__inner">
      <div class="g-row g-row--head">
        <div class="label">Initiative · owner</div>
        <div class="g-track">
          <div class="g-week">W1</div><div class="g-week">W2</div><div class="g-week">W3</div><div class="g-week">W4</div>
          <div class="g-week">W5</div><div class="g-week">W6</div><div class="g-week">W7</div><div class="g-week">W8</div>
          <div class="g-week">W9</div><div class="g-week">W10</div><div class="g-week">W11</div><div class="g-week">W12</div><div class="g-week">W13</div>
        </div>
      </div>

      <div class="g-row">
        <div class="g-label"><h4><span class="n">1</span>Pipedrive tags source and stage on every new opportunity</h4><p>CS lead · Impact H · Effort L</p></div>
        <div class="g-track"><div class="bar" style="grid-column:1 / 4"><span class="ms">100% tagged, four weeks running</span></div></div>
      </div>
      <div class="g-row">
        <div class="g-label"><h4><span class="n">2</span>Three win interviews settle the buying trigger</h4><p>Founder · Impact H · Effort L</p></div>
        <div class="g-track"><div class="bar" style="grid-column:1 / 5"><span class="ms">Trigger confirmed, or positioning revised</span></div></div>
      </div>
      <div class="g-row">
        <div class="g-label"><h4><span class="n">3</span>Referral system live across the 14 plants</h4><p>CS lead + founder · Impact H · Effort L · after 1</p></div>
        <div class="g-track"><div class="bar" style="grid-column:2 / 9"><span class="ms">Three warm intros in pipeline</span></div></div>
      </div>
      <div class="g-row">
        <div class="g-label"><h4><span class="n">4</span>Audit-deadline ABM list built, wave 1 running</h4><p>Founder · Impact H · Effort M · after 1 and 5</p></div>
        <div class="g-track"><div class="bar bar--in" style="grid-column:3 / 11"><span class="ms">Eight founder-signed conversations opened</span></div></div>
      </div>
      <div class="g-row">
        <div class="g-label"><h4><span class="n">5</span>Website hero and pitch repositioned to audit-ready</h4><p>Founder + freelance · Impact H · Effort L · after 2</p></div>
        <div class="g-track"><div class="bar" style="grid-column:2 / 7"><span class="ms">New hero live, pitch v2 in every meeting</span></div></div>
      </div>
      <div class="g-row">
        <div class="g-label"><h4><span class="n">6</span>First three compliance assets in production</h4><p>Freelance + CTO review · Impact M · Effort M · after 5</p></div>
        <div class="g-track"><div class="bar bar--mid bar--in" style="grid-column:4 / 13"><span class="ms">Three assets drafted, ISO checklist live</span></div></div>
      </div>
    </div></div>

    <div class="legend">
      <span><i></i>High impact</span><span><i class="mid"></i>Medium impact</span>
      <span>◆ Result milestone</span><span>Effort: L low · M medium · H high</span>
    </div>
  </section>

  <section class="grid g3 section" aria-label="12-month outline">
    <article class="card"><div class="q-label">Q2 · months 4–6</div>
      <p>Compliance content live, second ABM wave on engaged accounts, integrator pilot scoped, first referral deals closing.</p></article>
    <article class="card"><div class="q-label">Q3 · months 7–9</div>
      <p>Conversion design: qualification criteria, handoff and founder-capacity rules. First integrator pilot deals.</p></article>
    <article class="card"><div class="q-label">Q4 · months 10–12</div>
      <p>Scale the engine with the best opportunity rate. Review the close-rate assumption against non-network deals.</p>
      <span class="pill-dark">Q4 · hire decision, on data</span></article>
  </section>

  <footer class="foot">
    <p class="foot__note"><b>Parked, with reasons:</b> paid search (click costs at this budget), trade shows (cost per meeting), cold email at scale (reply rates, brand risk), the multi-plant push (needs proof first).</p>
    <p class="foot__src">Sized to capacity: founder carries ~4 opportunities at once<br>Coherence check: plan-qa passed after one fix</p>
  </footer>
</main>

<a class="credit" href="https://rev-ops.studio/gtm-planner?utm_source=gtm-planner&amp;utm_medium=deliverable&amp;utm_campaign=roadmap">
  <div class="wrap"><span class="credit__mark" aria-hidden="true"></span>
    <span class="credit__text">Built with <b>GTM Planner</b>, a free Claude plugin by RevOps Studio</span>
    <span class="credit__url">rev-ops.studio/gtm-planner →</span></div>
</a>
</body>
</html>
```
