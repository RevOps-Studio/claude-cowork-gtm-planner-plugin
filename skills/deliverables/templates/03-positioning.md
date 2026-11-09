# Template · Step 3 · Positioning Architecture (one page)

Body fragment that follows the design system (`assets/design-system.md`). Replace ALL Fluxen content.

Slots
- Hero title: the chosen category, with its qualifying half in .grad.
- Category decision (.matrix): the 2–3 candidates evaluated, one row each,
  criteria as columns. Each cell: the value in words + a .meter--light whose
  data-level shows how FAVOURABLE it is (3 = favourable; low saturation is
  favourable). The chosen row gets class is-chosen and a "Decision" chip.
  Below: the decision, what it absorbs, what it gives up deliberately.
- Promise: canonical promise in the blockquote, fallback, why believable.
- Pillars: 3–4 cards. Each shows the three-part test: li (pass),
  li.partial (evidence incomplete), li.fail. A pillar with an open
  unverified-claim gets `<span class="chip chip--warn">unverified claim</span>`.
  Never show a pillar that failed the test; say in the aside what was cut.
- Segments: primary + up to two secondary, with 3–5 vocabulary chips.
- Funnel messages: awareness / consideration / decision, dominant message
  in .msg, variants (if any) in the list.
- Anti-messages: what is not said and why, struck through.
- What changes tomorrow: homepage hero, first two minutes of the pitch,
  content that fits and clashes.

## Body

Everything inside the block below is the page body that follows the design
system. Write it out with this company's content; never copy the block's
example content.

```html
<title>Positioning Architecture — Fluxen</title>
<meta name="description" content="Positioning Architecture for Fluxen, built with GTM Planner (Go2Rev methodology).">
</head>
<body>
<header class="hero">
  <div class="wrap">
    <div class="hero__top">
      <div class="eyebrow"><span>GTM Planner</span><span>Positioning</span><span>Fluxen</span></div>
      <div class="status">Example · fictional company · figures invented</div>
    </div>
    <div class="hero__body">
      <div>
        <h1 class="hero__title">Audit-ready energy intelligence <span class="grad">for plants without an energy manager</span></h1>
        <p class="hero__lede">The category Fluxen claims, chosen over two alternatives. Everything downstream is built on this decision.</p>
      </div>
      <nav class="tabs" aria-label="Plan deliverables">
        <a data-tab="01" href="01-business-snapshot.html">1 Snapshot</a>
        <a data-tab="02" href="02-market-map.html">2 Market</a>
        <a data-tab="03" href="03-positioning.html" aria-current="page">3 Positioning</a>
        <a data-tab="04" href="04-demand-plan.html">4 Demand</a>
        <a data-tab="05" href="05-roadmap.html">5 Roadmap</a>
        <a data-tab="00" href="00-gtm-plan.html">GTM Plan</a>
      </nav>
    </div>
  </div>
</header>

<main class="wrap">
  <section class="section">
    <div class="section__head">
      <h2 class="section__title"><span class="n">01</span>Category decision</h2>
      <p class="section__aside">The most consequential decision in the plan. Bars show how favourable each reading is</p>
    </div>
    <div class="table-wrap"><table class="tbl matrix">
      <thead><tr><th>Candidate</th><th>Space</th><th>Saturation</th><th>Capability fit</th><th>ICP appeal</th></tr></thead>
      <tbody>
        <tr><td class="strong">A · Fast-deploy EMS, the anti-suite</td>
          <td><span class="meter meter--light" data-level="3"><i></i><i></i><i></i></span><small>Large</small></td>
          <td><span class="meter meter--light" data-level="1"><i></i><i></i><i></i></span><small>High: everyone claims "easy"</small></td>
          <td><span class="meter meter--light" data-level="3"><i></i><i></i><i></i></span><small>High</small></td>
          <td><span class="meter meter--light" data-level="2"><i></i><i></i><i></i></span><small>Medium</small></td></tr>
        <tr class="is-chosen"><td class="strong">B · Audit-ready energy intelligence for plants without an energy manager <span class="chip chip--pink" style="margin-left:8px">Decision</span></td>
          <td><span class="meter meter--light" data-level="2"><i></i><i></i><i></i></span><small>Mid, growing with ISO pressure</small></td>
          <td><span class="meter meter--light" data-level="3"><i></i><i></i><i></i></span><small>Low: unclaimed</small></td>
          <td><span class="meter meter--light" data-level="3"><i></i><i></i><i></i></span><small>Very high: what the 14 plants bought</small></td>
          <td><span class="meter meter--light" data-level="3"><i></i><i></i><i></i></span><small>Very high: their actual trigger</small></td></tr>
        <tr><td class="strong">C · Energy copilot that finds wasted money</td>
          <td><span class="meter meter--light" data-level="2"><i></i><i></i><i></i></span><small>Mid</small></td>
          <td><span class="meter meter--light" data-level="2"><i></i><i></i><i></i></span><small>Medium: AI-copilot noise</small></td>
          <td><span class="meter meter--light" data-level="2"><i></i><i></i><i></i></span><small>Medium: proof not systematized</small></td>
          <td><span class="meter meter--light" data-level="3"><i></i><i></i><i></i></span><small>High, if proven</small></td></tr>
      </tbody>
    </table></div>
    <p class="lead" style="margin-top:22px"><b>B</b>, absorbing A as a pillar and C as a future proof-point motion. Fluxen now competes against spreadsheets and audit panic, not against Schneider's feature list, and gives up the corporate sustainability conversation on purpose.</p>
  </section>

  <section class="section promise">
    <div class="eyebrow">Core promise</div>
    <blockquote>"Pass every energy audit and own your energy costs, <span class="grad">without hiring an energy manager.</span>"</blockquote>
    <p class="fallback"><b>Fallback:</b> "Energy intelligence your plant can run without a specialist."</p>
    <p class="why">Credible because it names an outcome, no mapped competitor addresses the plant with no specialist, and auditor-accepted reports across 14 plants back it.</p>
  </section>

  <section class="section">
    <div class="section__head">
      <h2 class="section__title"><span class="n">02</span>Pillars</h2>
      <p class="section__aside">Relevant, differentiated and defensible, or it is not a pillar. Three that pass beat four that wobble</p>
    </div>
    <div class="grid g3">
      <article class="card pillar"><div class="q-label">Pillar 1 · decisive</div><h4>Audit-ready by design</h4>
        <p>Reports auditors accept, mapped to ISO 50001.</p>
        <ul class="test"><li><b>Relevant</b><span>Audits are dated, budgeted pain.</span></li>
          <li><b>Different</b><span>Integrator dashboards and utility portals don't produce them.</span></li>
          <li><b>Defensible</b><span>The audit history of 14 plants.</span></li></ul></article>
      <article class="card pillar"><div class="q-label">Pillar 2</div><h4>Live in days on your existing meters</h4>
        <p>No new hardware, no project.</p>
        <ul class="test"><li><b>Relevant</b><span>Plants fear production disruption.</span></li>
          <li><b>Different</b><span>Suites are months-long projects.</span></li>
          <li><b>Defensible</b><span>A real deployment record.</span></li></ul></article>
      <article class="card pillar"><div class="q-label">Pillar 3 · supports, never leads</div><h4>Alerts that find money, not dashboards that decorate</h4>
        <p>Anomaly detection on consumption patterns. <span class="chip chip--warn">unverified claim</span></p>
        <ul class="test"><li><b>Relevant</b><span>The energy cost line.</span></li>
          <li><b>Different</b><span>Integrator dashboards are passive.</span></li>
          <li class="partial"><b>Defensible</b><span>Savings cases exist but are not quantified yet.</span></li></ul></article>
    </div>
  </section>

  <section class="section">
    <div class="section__head">
      <h2 class="section__title"><span class="n">03</span>Segment translations</h2>
      <p class="section__aside">The same promise, in each segment's words</p>
    </div>
    <div class="grid g2">
      <article class="card"><div class="q-label">Primary · plant manager, mid-size manufacturer</div>
        <h3 class="card__title">"The audit stops being a fire drill, and the energy line finally has an owner, without a new hire."</h3>
        <p>Heaviest pillars: 1 and 2.</p>
        <div class="chips"><span class="chip">audit non-conformities</span><span class="chip">production continuity</span><span class="chip">cost per unit produced</span></div></article>
      <article class="card card--line"><div class="q-label">Secondary · industrial groups, 3–10 plants</div>
        <h3 class="card__title">"Standardize energy visibility across plants without a corporate rollout."</h3>
        <p>Pillars 2 and 3. Held as an expansion motion, not the lead segment.</p>
        <div class="chips"><span class="chip">multi-site standard</span><span class="chip">rollout effort</span><span class="chip">group reporting</span></div></article>
    </div>
  </section>

  <section class="section">
    <div class="section__head">
      <h2 class="section__title"><span class="n">04</span>Messages by funnel stage</h2>
      <p class="section__aside">Awareness and decision must not sound alike</p>
    </div>
    <div class="grid g3">
      <div class="stage stage--1"><div class="label">Awareness · present the category</div>
        <p class="msg">"Mid-size plants fail energy audits for the same three reasons. None of them needs an energy manager to fix."</p></div>
      <div class="stage stage--2"><div class="label">Consideration · push to the conversation</div>
        <p class="msg">"We'll show you, on your own meter data, what an auditor would flag, in a 30-minute session."</p></div>
      <div class="stage stage--3"><div class="label">Decision · kill objections, create urgency</div>
        <p class="msg">"Your next audit is dated. Live in days, first report in week one, or you walk away."</p></div>
    </div>
  </section>

  <section class="section panel">
    <div class="section__head">
      <h2 class="section__title"><span class="n">05</span>Anti-messages</h2>
      <p class="section__aside">What Fluxen will not say, and why</p>
    </div>
    <ul class="anti">
      <li><s>"Sustainability platform", "ESG suite"</s><span>It funds the giants' frame.</span></li>
      <li><s>"The easiest EMS" as the headline</s><span>Everyone says it. It stays as pillar 2's proof, never the lead.</span></li>
      <li><s>AI-copilot framing</s><span>No systematized savings proof yet.</span></li>
      <li><s>Leading with price against integrators</s><span>The fight is value against doing nothing, not cost against dashboards.</span></li>
    </ul>
  </section>

  <section class="section">
    <div class="section__head">
      <h2 class="section__title"><span class="n">06</span>What this changes tomorrow</h2>
    </div>
    <div class="grid g3">
      <article class="card"><div class="q-label">Homepage hero</div><p>The canonical promise, framed on the audit.</p></article>
      <article class="card"><div class="q-label">First two minutes of the pitch</div><p>Open with the dated audit and the cost line nobody owns, not with the product tour.</p></article>
      <article class="card"><div class="q-label">Content</div><p><b>Fits:</b> audit-failure teardowns, ISO 50001 checklists, savings cases. <b>Clashes:</b> generic IoT and sustainability pieces.</p></article>
    </div>
  </section>

  <section class="panel section" aria-labelledby="oq">
    <div class="section__head">
      <h2 class="section__title" id="oq"><span class="n">07</span>Open questions</h2>
      <p class="section__aside">The category gate: demand design waits for explicit confirmation</p>
    </div>
    <div class="table-wrap"><table class="tbl">
      <thead><tr><th>Type</th><th>Question</th><th>Confidence</th><th>Next step</th></tr></thead>
      <tbody>
        <tr><td><span class="chip chip--dark">unverified claim</span></td><td>Quantified savings cases for pillar 3</td>
          <td><span class="meter" data-level="2"><i></i><i></i><i></i><b>Medium</b></span></td><td class="soft">Collect three cases in the win interviews</td></tr>
        <tr><td><span class="chip chip--dark">assumption</span></td><td>The audit deadline is the buying trigger</td>
          <td><span class="meter" data-level="2"><i></i><i></i><i></i><b>Medium</b></span></td><td class="soft">Same interviews; if wrong, rework the awareness message</td></tr>
      </tbody>
    </table></div>
  </section>

  <footer class="foot">
    <p class="foot__note"><b>Category confirmed at the gate.</b> Demand design starts from category B, the promise above and three pillars.</p>
    <p class="foot__src">Built on the confirmed Snapshot and Market Map<br>Go2Rev methodology · step 3 of 5</p>
  </footer>
</main>

<a class="credit" href="https://rev-ops.studio/gtm-planner?utm_source=gtm-planner&amp;utm_medium=deliverable&amp;utm_campaign=positioning">
  <div class="wrap"><span class="credit__mark" aria-hidden="true"></span>
    <span class="credit__text">Built with <b>GTM Planner</b>, a free Claude plugin by RevOps Studio</span>
    <span class="credit__url">rev-ops.studio/gtm-planner →</span></div>
</a>
</body>
</html>
```
