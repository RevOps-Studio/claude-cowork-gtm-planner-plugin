# Template · Step 4 · Demand Plan (one page)

Body fragment that follows the design system (`assets/design-system.md`). Replace ALL Fluxen content.

Slots
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

## Body

Everything inside the block below is the page body that follows the design
system. Write it out with this company's content; never copy the block's
example content.

```html
<title>Demand Plan — Fluxen</title>
<meta name="description" content="Demand Plan for Fluxen, built with GTM Planner (Go2Rev methodology).">
</head>
<body>
<header class="hero">
  <div class="wrap">
    <div class="hero__top">
      <div class="eyebrow"><span>GTM Planner</span><span>Demand Plan</span><span>Fluxen</span></div>
      <div class="status">Example · fictional company · figures invented</div>
    </div>
    <div class="hero__body">
      <div>
        <h1 class="hero__title">From the founder's network <span class="grad">to four repeatable engines</span></h1>
        <p class="hero__lede">Engines the current team can run on ≤ €4k a month, staggered so the founder never carries more than four live opportunities.</p>
      </div>
      <div class="chain" aria-label="Demand math">
        <div class="chain__step"><b>~20</b><span>opps last year</span></div>
        <span class="chain__arrow">→</span>
        <div class="chain__step"><b>32–40</b><span>opps needed</span></div>
        <span class="chain__arrow">→</span>
        <div class="chain__step chain__step--goal"><b>8</b><span>new plants</span></div>
      </div>
    </div>
    <nav class="tabs tabs--row" aria-label="Plan deliverables">
      <a data-tab="01" href="01-business-snapshot.html">1 Snapshot</a>
      <a data-tab="02" href="02-market-map.html">2 Market</a>
      <a data-tab="03" href="03-positioning.html">3 Positioning</a>
      <a data-tab="04" href="04-demand-plan.html" aria-current="page">4 Demand</a>
      <a data-tab="05" href="05-roadmap.html">5 Roadmap</a>
      <a data-tab="00" href="00-gtm-plan.html">GTM Plan</a>
    </nav>
  </div>
</header>

<main class="wrap">
  <section class="kpis" aria-label="Key figures">
    <div class="kpi"><b>≤ €4k</b><span>budget ceiling per month</span></div>
    <div class="kpi kpi--accent"><b>~€2k</b><span>planned channel spend per month</span></div>
    <div class="kpi"><b>4</b><span>opportunities the founder can carry at once</span></div>
    <div class="kpi"><b>4 + 3</b><span>engines selected, engines discarded</span></div>
  </section>

  <section class="section">
    <div class="section__head">
      <h2 class="section__title"><span class="n">01</span>Design principles</h2>
    </div>
    <div class="grid g3">
      <article class="card"><h3 class="card__title">Trigger over volume</h3><p>Chase plants with a dated audit, not "all manufacturers".</p></article>
      <article class="card"><h3 class="card__title">The founder is the bottleneck</h3><p>Qualify hard and stagger the waves.</p></article>
      <article class="card"><h3 class="card__title">Runs on what exists</h3><p>≤ €4k a month and no marketing hire.</p></article>
    </div>
  </section>

  <section class="section">
    <div class="section__head">
      <h2 class="section__title"><span class="n">02</span>Engine architecture</h2>
      <p class="section__aside">Content arms the ABM and referral conversations; customers and integrators point to plants with dated audits</p>
    </div>
    <div class="table-wrap"><table class="tbl cov">
      <thead><tr><th>Engine</th><th>Capture</th><th>Consideration</th><th>Conversion</th><th style="width:30%">First signal</th></tr></thead>
      <tbody>
        <tr><td class="strong">1 · Customer referral system</td><td></td><td></td><td><span class="dot"></span></td>
          <td><div class="signal"><i style="--from:0%;--to:33%"></i></div></td></tr>
        <tr><td class="strong">2 · Audit-deadline ABM</td><td></td><td><span class="dot"></span></td><td><span class="dot dot--low"></span></td>
          <td><div class="signal"><i style="--from:33%;--to:50%"></i></div></td></tr>
        <tr><td class="strong">3 · Compliance content capture</td><td><span class="dot"></span></td><td></td><td></td>
          <td><div class="signal"><i style="--from:50%;--to:83%"></i></div></td></tr>
        <tr><td class="strong">4 · Integrator co-selling pilot</td><td></td><td><span class="dot"></span></td><td></td>
          <td><div class="signal"><i style="--from:50%;--to:100%"></i></div></td></tr>
        <tr><td></td><td></td><td></td><td></td><td><div class="signal-scale"><span>day 0</span><span>30</span><span>60</span><span>90</span><span>120</span><span>150</span><span>180</span></div></td></tr>
      </tbody>
    </table></div>
  </section>

  <section class="section">
    <div class="section__head">
      <h2 class="section__title"><span class="n">03</span>The engines</h2>
      <p class="section__aside">Every benchmark carries its source, or the flag that it has none</p>
    </div>
    <div class="grid g4">
      <article class="card engine"><div class="q-label">Engine 1 · first signal &lt; 60 days</div><h4>Customer referral system</h4>
        <p>14 plants, 92% retention, no systematic ask today. Referral ask after the first audit success, with a service-credit incentive.</p>
        <p><b>Health:</b> asks per month, intro-to-opportunity rate, referral share of pipeline.</p>
        <p><b>Runs on:</b> CS lead and founder scripts.</p>
        <div class="meta"><span class="chip chip--warn">needs benchmark</span><span class="src">referral conversion: track from month one</span></div></article>
      <article class="card engine"><div class="q-label">Engine 2 · 60–90 days</div><h4>Audit-deadline ABM</h4>
        <p>120 plants from public ISO registries whose certification expires in 6–12 months; founder-signed three-touch sequences.</p>
        <p><b>Health:</b> list coverage, reply rate, meetings per month against a capacity of 4.</p>
        <div class="meta"><span class="src">reply 5–12%: Lavender 2025, sector-generic</span></div></article>
      <article class="card engine"><div class="q-label">Engine 3 · 90–150 days</div><h4>Compliance content capture</h4>
        <p>6–8 assets answering what plants search before an audit: ISO 50001 checklist, non-conformity teardowns, report templates.</p>
        <p><b>Honest note:</b> a young domain. This compounds into year 2; it does not carry year 1.</p>
        <div class="meta"><span class="src">bottom-funnel conversion 2–6%: generic benchmark</span></div></article>
      <article class="card engine"><div class="q-label">Engine 4 · 90–180 days</div><h4>Integrator co-selling pilot</h4>
        <p>Three integrators whose dashboards die after handover keep the metering work; Fluxen takes the software layer.</p>
        <p><b>Health:</b> intros per quarter, pilot deals closed. Two-deal pilot before formalizing.</p></article>
    </div>
  </section>

  <section class="section">
    <div class="section__head">
      <h2 class="section__title"><span class="n">04</span>Discarded, visibly</h2>
      <p class="section__aside">Screened out on positioning fit, operability or speed to first result</p>
    </div>
    <div class="grid g3">
      <div class="discard"><h4>Paid search</h4><p>€6–12 per click on EMS terms buys about two clicks a day at this budget.</p><span class="src">WordStream industrial benchmarks 2025</span></div>
      <div class="discard"><h4>Trade-show sponsorships</h4><p>Cost per qualified meeting far above the referral path at this budget.</p></div>
      <div class="discard"><h4>Cold email at scale</h4><p>Generic industrial reply rates under 1%; this ICP answers specificity, not volume.</p><span class="src">Belkins 2025</span></div>
    </div>
  </section>

  <section class="section">
    <div class="section__head">
      <h2 class="section__title"><span class="n">05</span>Channel mix</h2>
      <p class="section__aside">Where each engine runs</p>
    </div>
    <div class="table-wrap"><table class="tbl">
      <thead><tr><th>Channel</th><th>Engine</th><th>Weight</th><th>Phase</th><th>Monthly cost</th></tr></thead>
      <tbody>
        <tr><td class="strong">Direct customer and CS touchpoints</td><td>1</td><td><span class="meter meter--light" data-level="3"><i></i><i></i><i></i></span></td><td><span class="chip">0–90 days</span></td><td>~€0 + incentives</td></tr>
        <tr><td class="strong">LinkedIn + email, founder-signed</td><td>2</td><td><span class="meter meter--light" data-level="3"><i></i><i></i><i></i></span></td><td><span class="chip">0–90 days</span></td><td>€200 in tools</td></tr>
        <tr><td class="strong">Website and SEO, compliance assets</td><td>3</td><td><span class="meter meter--light" data-level="2"><i></i><i></i><i></i></span></td><td><span class="chip">build now, live 90+</span></td><td>€1–2k production (assumption)</td></tr>
        <tr><td class="strong">Integrator partnerships</td><td>4</td><td><span class="meter meter--light" data-level="2"><i></i><i></i><i></i></span></td><td><span class="chip">90+ days</span></td><td>~€0</td></tr>
      </tbody>
    </table></div>
  </section>

  <section class="section">
    <div class="section__head">
      <h2 class="section__title"><span class="n">06</span>Activation sequence</h2>
      <p class="section__aside">Not everything starts at once</p>
    </div>
    <div class="grid g3">
      <div class="phase phase--now"><div class="q-label">Days 0–90</div><ul><li>Engines 1 and 2 live</li><li>Engine 3 in production</li><li>Engine 4 scoping</li></ul></div>
      <div class="phase"><div class="q-label">Days 90–180</div><ul><li>Content live</li><li>Integrator pilot</li><li>Second ABM wave on engaged accounts</li></ul></div>
      <div class="phase"><div class="q-label">Days 180–365</div><ul><li>Double down on whichever of engines 1 and 2 converts best</li><li>Formalize the integrator program if the pilot closes a deal</li></ul></div>
    </div>
  </section>

  <section class="panel section" aria-labelledby="oq">
    <div class="section__head">
      <h2 class="section__title" id="oq"><span class="n">07</span>Open questions</h2>
      <p class="section__aside">What the demand math rests on that is not settled yet</p>
    </div>
    <div class="table-wrap"><table class="tbl">
      <thead><tr><th>Type</th><th>Question</th><th>Confidence</th><th>Next step</th></tr></thead>
      <tbody>
        <tr><td><span class="chip chip--dark">assumption</span></td><td>A ~25% close rate holds beyond the founder's network <span class="risk">· decision risk</span></td>
          <td><span class="meter" data-level="1"><i></i><i></i><i></i><b>Low</b></span></td><td class="soft">Review at the first five non-network opportunities</td></tr>
        <tr><td><span class="chip chip--dark">assumption</span></td><td>The 120-account list can be built from public ISO registries</td>
          <td><span class="meter" data-level="2"><i></i><i></i><i></i><b>Medium</b></span></td><td class="soft">Validate list size in week 2; below 60, widen the trigger</td></tr>
        <tr><td><span class="chip chip--dark">needs benchmark</span></td><td>Referral-to-opportunity conversion in industrial SaaS</td>
          <td><span class="meter" data-level="0"><i></i><i></i><i></i><b>—</b></span></td><td class="soft">No credible public source; instrument the funnel from week 1</td></tr>
      </tbody>
    </table></div>
  </section>

  <footer class="foot">
    <p class="foot__note"><b>What this plan does not solve:</b> qualification criteria and handoff (urgent, given the founder bottleneck), the sales process itself, and funnel instrumentation in Pipedrive.</p>
    <p class="foot__src">Web benchmarks, cited · funnel figures declared · HubSpot, Ahrefs, Similarweb not connected<br>Go2Rev methodology · step 4 of 5</p>
  </footer>
</main>

<a class="credit" href="https://rev-ops.studio/gtm-planner?utm_source=gtm-planner&amp;utm_medium=deliverable&amp;utm_campaign=demand-plan">
  <div class="wrap"><span class="credit__mark" aria-hidden="true"></span>
    <span class="credit__text">Built with <b>GTM Planner</b>, a free Claude plugin by RevOps Studio</span>
    <span class="credit__url">rev-ops.studio/gtm-planner →</span></div>
</a>
</body>
</html>
```
