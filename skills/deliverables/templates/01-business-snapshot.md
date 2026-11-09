# Template · Step 1 · Business Snapshot (one page)

Body fragment that follows the design system (`assets/design-system.md`). Example content is the
fictional Fluxen case — replace ALL of it with the confirmed snapshot.
The page body is the `html` block under Body; nothing outside it goes in the output.

Slots
- `<title>`, meta description: "Business Snapshot — [Company]".
- .status: "Confirmed · [date]" (+ class status--ok) or "Draft — not confirmed"
  (class status--draft). "Example · …" is reserved for the plugin's own sample.
- Hero title: "[Company] `<span class=muted>→ [the move this plan is for]</span>`".
- Lede: offer in a few words · category · city/country.
- Tabs: `<a>` for deliverables that exist in the folder, `<span>` for the rest.
- KPI strip: 4–5 figures FROM THE SNAPSHOT only. The 12-month goal gets
  .kpi--accent. A declared-but-unverified figure gets .kpi--est. No figure →
  leave the KPI out; never estimate one to fill the strip. A recommendation
  from an open question is not a KPI.
- Cards 01–08 follow the snapshot sections 1–8, 2–3 sentences each.
- Open questions (section 9): every one, with type chip, confidence meter
  (data-level 1 low · 2 medium · 3 high) and the next step.
- Foot: the "Snapshot confidence" note + the sources line.
- Credit strip: keep unless the journey state says Deliverable credit: off.

## Body

Everything inside the block below is the page body that follows the design
system. Write it out with this company's content; never copy the block's
example content.

```html
<title>Business Snapshot — Fluxen</title>
<meta name="description" content="Business Snapshot for Fluxen, built with GTM Planner (Go2Rev methodology).">
</head>
<body>
<header class="hero">
  <div class="wrap">
    <div class="hero__top">
      <div class="eyebrow"><span>GTM Planner</span><span>Business Snapshot</span></div>
      <div class="status">Example · fictional company · figures invented</div>
    </div>
    <div class="hero__body">
      <div>
        <h1 class="hero__title hero__title--wide">Fluxen <span class="muted">→ beyond the founder network</span></h1>
        <p class="hero__lede">B2B SaaS · energy management for mid-size manufacturing plants · Valencia</p>
      </div>
      <nav class="tabs" aria-label="Plan deliverables">
        <a data-tab="01" href="01-business-snapshot.html" aria-current="page">1 Snapshot</a>
        <a data-tab="02" href="02-market-map.html">2 Market</a>
        <a data-tab="03" href="03-positioning.html">3 Positioning</a>
        <a data-tab="04" href="04-demand-plan.html">4 Demand</a>
        <a data-tab="05" href="05-roadmap.html">5 Roadmap</a>
        <a data-tab="00" href="00-gtm-plan.html">GTM Plan</a>
      </nav>
    </div>
  </div>
</header>

<main class="wrap">
  <section class="kpis" aria-label="Key figures">
    <div class="kpi"><b>€900k</b><span>ARR today, Spain only</span></div>
    <div class="kpi"><b>14</b><span>plants live, 92% retention</span></div>
    <div class="kpi kpi--accent"><b>8 plants</b><span>new in 12 months: the goal</span></div>
    <div class="kpi"><b>€18k</b><span>average deal, per plant per year</span></div>
    <div class="kpi"><b>≤ €4k</b><span>marketing budget per month</span></div>
  </section>

  <section class="grid g4 section" aria-label="Snapshot">
    <article class="card"><h3 class="card__title"><span class="num">01</span>Business context</h3>
      <p>Founded 2021, 11 people. Product signal is real (14 plants, 92% retention) but growth stalled when the founder's network ran out.</p></article>
    <article class="card"><h3 class="card__title"><span class="num">02</span>Offer</h3>
      <p>Real-time energy monitoring, anomaly alerts and ISO 50001 audit reports, on the plant's existing meters. €12–30k per plant per year.</p></article>
    <article class="card"><h3 class="card__title"><span class="num">03</span>Target segment</h3>
      <p>Plants of 50–500 people in energy-intensive processes, ISO 50001 certified or pursuing it, with no energy manager. Buyer: plant manager.</p></article>
    <article class="card"><h3 class="card__title"><span class="num">04</span>Funnel and cycle</h3>
      <p>~20 opportunities last year, ~60% from the founder's network. 2–4 month cycle, about 1 in 4 proposals closes (declared).</p></article>
    <article class="card"><h3 class="card__title"><span class="num">05</span>Stack</h3>
      <p>Pipedrive lightly used with no source tracking, Mailchimp dormant, WordPress site. No marketing automation.</p></article>
    <article class="card"><h3 class="card__title"><span class="num">06</span>Revenue team</h3>
      <p>The CEO sells and touches every deal; the CTO supports demos; one CS person onboards. No marketing hire.</p></article>
    <article class="card"><h3 class="card__title"><span class="num">07</span>Stated goals</h3>
      <p>8 new plants in 12 months (≈ +€150k ARR) and the first pipeline not originated by the founder.</p></article>
    <article class="card"><h3 class="card__title"><span class="num">08</span>Constraints</h3>
      <p>≤ €4k a month for marketing, nobody to run campaigns full-time, and the founder can carry ~4 opportunities at once.</p></article>
  </section>

  <section class="panel section" aria-labelledby="oq">
    <div class="section__head">
      <h2 class="section__title" id="oq"><span class="n">09</span>Open questions</h2>
      <p class="section__aside">Each with its type, the confidence in what we know, and the step that would settle it</p>
    </div>
    <div class="table-wrap"><table class="tbl">
      <thead><tr><th>Type</th><th>Question</th><th>Confidence</th><th>Next step</th></tr></thead>
      <tbody>
        <tr><td><span class="chip chip--dark">assumption</span></td><td>"Easiest to deploy" is the real reason customers buy</td>
          <td><span class="meter" data-level="1"><i></i><i></i><i></i><b>Low</b></span></td><td class="soft">Interview three recent wins before positioning</td></tr>
        <tr><td><span class="chip chip--dark">missing data</span></td><td>The real close rate and stage-by-stage funnel</td>
          <td><span class="meter" data-level="1"><i></i><i></i><i></i><b>Low</b></span></td><td class="soft">Turn on stage and source fields in Pipedrive now</td></tr>
        <tr><td><span class="chip chip--dark">assumption</span></td><td>The ISO 50001 deadline is the buying trigger</td>
          <td><span class="meter" data-level="2"><i></i><i></i><i></i><b>Medium</b></span></td><td class="soft">Validate in the same win interviews</td></tr>
      </tbody>
    </table></div>
  </section>

  <footer class="foot">
    <p class="foot__note"><b>Snapshot confidence:</b> solid on the offer, the ICP shape and the constraints; thin on funnel numbers and on the real buying reason. The most valuable input is three win interviews.</p>
    <p class="foot__src">Figures declared by the company · CRM not connected<br>Go2Rev methodology · step 1 of 5</p>
  </footer>
</main>

<a class="credit" href="https://rev-ops.studio/gtm-planner?utm_source=gtm-planner&amp;utm_medium=deliverable&amp;utm_campaign=business-snapshot">
  <div class="wrap"><span class="credit__mark" aria-hidden="true"></span>
    <span class="credit__text">Built with <b>GTM Planner</b>, a free Claude plugin by RevOps Studio</span>
    <span class="credit__url">rev-ops.studio/gtm-planner →</span></div>
</a>
</body>
</html>
```
