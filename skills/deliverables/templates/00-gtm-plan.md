# Page blueprint · Consolidated GTM Plan (long document, one file)

The page blueprint: what goes on this page and in what order. Build it with the components in `assets/design-system.md`. Example values come from the fictional Fluxen case; none of them belongs in a real page.
It consolidates the confirmed step outputs; it never introduces content
the steps did not confirm.

## Slots

- Hero title: "[Company]'s go-to-market plan" + the category bet in .grad.
- Decision chain (.dchain): the five decisions, one short line each:
  category → promise → engines → channels → commitments (90-day count).
- TOC: anchors to the eight chapters below. Keep the order.
- Chapters 2–6: condensed versions of each step, each ending with a
  .more link to its one-page deliverable when that file exists.
- Chapter 7 (ledger): every unresolved open question from all five steps.
  Never trim it. "Decision risk" (.risk) for low-confidence items touching
  category, ICP or engine selection. Evidence map: one tile per source type.
- Chapter 8 (execution readiness): the three workstreams + capacity note,
  as written by the roadmap step. Factual tone, no call to action, no
  "we can help" — the methodology forbids it here.

## Structure

1. **Hero.** Eyebrow: GTM Planner · GTM Plan · [Company]. Status pill.
   Title "[Company]'s go-to-market plan: [the category bet]", the bet in
   `.grad`; lede: the chain-of-decisions sentence. Under the body row, the
   `.dchain` with Category, Promise, Engines, Channels, Commitments.
2. **Contents bar** (`.toc`) with numbered links to the eight chapters.
3. **01 Executive summary** — a KPI strip, then the summary as a `.lead`.
4. **02 Business snapshot** — four cards (Offer, ICP, Funnel,
   Constraints); "Full snapshot →" as a `.more` link in the section head.
5. **03 Market map** — a `.split`: the map's conclusion as a `.lead`; two
   cards (the GAP, the GAP HYPOTHESIS marked parked or open).
6. **04 Positioning** — the promise block with eyebrow "Category [X],
   confirmed at the gate · core promise"; a grid of pillar cards (label and
   title, plus flags); the anti-messages as one aside line.
7. **05 Demand plan** — one `.engine` card per engine (time to first signal
   as label, name, funnel stage); the discards and spend as one aside line.
8. **06 Roadmap** — a compact table: # · Initiative · Owner · Result
   milestone · When; the 12-month outline and parked list as one aside
   line.
9. **07 Assumption & evidence ledger** — dark panel. Table: Type ·
   Question · Confidence · Decision risk (`.risk` when high) ·
   Recommendation. Then the label "What the plan stands on" and four
   evidence tiles: User-declared, Connected tools, Cited sources,
   Inference.
10. **08 Execution readiness** — aside "This plan decides positioning and
    demand. It does not build the machinery that converts and operates
    them."; three `.ws` cards (Conversion design, Deployment,
    Measurement) with their "If skipped"; the capacity note as a `.lead`.
11. **Foot** — note on the coherence check; sources line and
    "consolidated plan".
12. **Credit strip**, campaign `gtm-plan`.

Chapters 2–6 and 8 carry the `.chapter` class (rule above, new page in
print); the ledger is a dark panel instead.
