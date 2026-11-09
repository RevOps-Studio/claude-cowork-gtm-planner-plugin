# Visual rules

The deliverables carry the plan's honesty into a format people actually
read. A beautiful page that drops a flag or adds a number undoes the method,
so fidelity rules come first and layout rules second.

## Fidelity

1. **Only confirmed content.** Every figure, name, quote, date and claim on
   the page appears in the confirmed step output (or, for a draft, in the
   draft the user is looking at). Shortening and rephrasing are allowed;
   adding is not. That includes the "connective" numbers a layout tempts you
   to compute: totals, percentages, conversion steps, dates. If the step
   doesn't state it, the page doesn't either.
2. **Flags survive.** `assumption`, `missing-data`, `conflict`,
   `unverified-claim` and `needs-benchmark` stay visible wherever the step
   showed them, as chips or in the open-questions table. Declared estimates
   keep their "est." mark (`.kpi--est`). Benchmarks keep their source, or
   their `needs benchmark` chip.
3. **Every open question.** The snapshot, each step page and the GTM Plan's
   ledger show all unresolved open questions of that scope, however many
   there are. The table grows; it is never trimmed. The one-page tables
   carry type, question, confidence and next step; why it matters and the
   evidence stay in the step's Markdown and in the ledger.
4. **Omit, don't fill.** A KPI with no figure is left out. A chain step with
   no volume is left out. A section with no content is dropped, and the
   reply says what was dropped and why.
5. **Encodings mean something.** Confidence meters: 1 low · 2 medium ·
   3 high, 0 when there is no working answer. Favourability meters in the
   category matrix: 3 = favourable. Bar colour on the roadmap: impact.
   Positions on the positioning map are qualitative and say so.
6. **The plugin's own sample is the only Fluxen.** The blueprints' example
   values come from the plugin's fictional case; a real page never carries
   them. When the user is genuinely rendering the sample, treat its status
   like that of any other confirmed step.
7. **A recommendation is not a decision.** The next step attached to an
   open question stays in the open-questions table. It never moves into the
   KPI strip, a card, the hero or the roadmap as if it were settled — "treat
   month 9 as the go/no-go" is a proposal until the user confirms it.
8. **Status tells the truth.** `Confirmed · [date]` with `status--ok` for a
   confirmed step, using the confirmation date recorded in the journey
   state; when no date is recorded, write `Confirmed` alone — never work a
   date out from "yesterday" or "last week". `Draft — not confirmed` with
   `status--draft` otherwise.
   "Example · fictional company · figures invented" belongs to the plugin's
   own sample and never appears in a real deliverable.

## Language and format

- Every visible label is in the user's language: eyebrow, section titles,
  table headers, chips, legend, tabs, credit line. Keep the mono style; only
  the words change. Set `lang` on `<html>` when assembling.
- Dates in the user's locale (`19 Oct` / `19 oct.`); currency as the step
  states it.
- File names stay fixed in every language — the tabs link to them:
  `00-gtm-plan.html`, `01-business-snapshot.html`, `02-market-map.html`,
  `03-positioning.html`, `04-demand-plan.html`, `05-roadmap.html`.
- Tabs: a deliverable that exists in the folder is a link
  (`<a data-tab="03" href="03-positioning.html">3 Positioning</a>`); one that
  doesn't is `<span data-tab="03">3 Positioning</span>`. Mark the current
  page with `aria-current="page"`.

## Writing for the page

- Hero title: the step's conclusion, not its name, eight to fourteen words,
  with the decisive half in `<span class="grad">` — unless the blueprint
  gives the title another form (the snapshot's "[Company] → [the move]").
- Cards: two or three sentences, about 45 words at most. Card titles: three
  to six words.
- Table cells: one line where possible. Roadmap milestones: seven words at
  most.
- Operator language, as in the steps: no "360", "holistic", "journey",
  "ecosystem", "transformation".
- Escape `&`, `<` and `>` in content (`&amp;` `&lt;` `&gt;`).

## Design system

`assets/design-system.md` specifies the RevOps Studio visual system:
Manrope and JetBrains Mono, ink and paper, the purple-to-yellow gradient,
and every component a page uses, with exact values. Follow it as written:
no colours, fonts, effects, external images, scripts or client logos of your
own. Inline `style` is allowed only for the positional values the
blueprints use (`grid-column`, `--x`, `--y`, `--w`, `--from`, `--to`). Fonts
load from Google Fonts; offline, the page falls back to system fonts and
stays readable. Once a company has one deliverable, every later page reuses
its stylesheet unchanged.

## Credit line

The last element before `</body>`, unless the journey state says
`Deliverable credit: off`. English:

```html
<a class="credit" href="https://rev-ops.studio/gtm-planner?utm_source=gtm-planner&amp;utm_medium=deliverable&amp;utm_campaign=CAMPAIGN">
  <div class="wrap"><span class="credit__mark" aria-hidden="true"></span>
    <span class="credit__text">Built with <b>GTM Planner</b>, a free Claude plugin by RevOps Studio</span>
    <span class="credit__url">rev-ops.studio/gtm-planner →</span></div>
</a>
```

Spanish: link to `https://rev-ops.studio/es/gtm-planner?…` (same
parameters), text *Hecho con **GTM Planner**, un plugin gratuito para Claude
de RevOps Studio*, url label `rev-ops.studio/es/gtm-planner →`. Other
languages: translate the text and use the English link.

The mark's background image, exactly (one line, in the `.credit__mark`
rule):

`data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='90 61 212 245'%3E%3Cdefs%3E%3ClinearGradient id='g' x1='0' y1='1' x2='1' y2='0'%3E%3Cstop offset='0' stop-color='%238114b0'/%3E%3Cstop offset='.5' stop-color='%23fe5688'/%3E%3Cstop offset='1' stop-color='%23f7fd3d'/%3E%3C/linearGradient%3E%3C/defs%3E%3Cpath fill='url(%23g)' d='M301.73 305.99H240.41L196.6 221.75H143.43V305.67H90.1V61.61H213.51C231.13 61.61 246.19 65.02 258.69 71.83 271.19 78.64 280.74 88.15 287.35 100.35 293.96 112.53 297.27 126.78 297.27 143.07 297.27 161 293.25 176.19 285.21 188.64 277.17 201.09 265.67 210.08 250.71 215.61ZM143.43 106.96V176.42H204.76C218.79 176.42 228.87 173.35 235.02 167.21 241.18 161.05 244.26 152.55 244.26 141.69 244.26 130.51 241.1 121.93 234.8 115.94 228.5 109.95 218.48 106.96 204.76 106.96Z'/%3E%3C/svg%3E`

`CAMPAIGN` is the deliverable: `business-snapshot`, `market-map`,
`positioning`, `demand-plan`, `roadmap`, `gtm-plan`. The parameters carry no
company or user data — never add any.

## Self-check before handing over

Read the page you wrote back and check:

- [ ] It starts with the doctype, has one `<style>` block, and contains no
      Markdown and no code fences.
- [ ] "Fluxen", "fictional company" and the blueprint's example values
      appear nowhere (unless the company really is Fluxen).
- [ ] Every number, date and name on the page is in the confirmed step
      output or the journey state. List the figures on the page and tick
      each one off against the step.
- [ ] No open question's recommendation appears anywhere as a decision.
- [ ] Every flag and every open question of the step is visible.
- [ ] Status is Confirmed or Draft, with the right date.
- [ ] All labels are in the user's language, and `lang` is set.
- [ ] Tabs link only to files that exist.
- [ ] The credit line follows the journey-state setting; nothing else on the
      page promotes RevOps Studio.
- [ ] If an earlier deliverable exists, the `<style>` block is identical to
      its block.
