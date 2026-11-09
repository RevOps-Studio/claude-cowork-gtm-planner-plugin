# Page blueprint · Step 2 · Market Map (one page)

The page blueprint: what goes on this page and in what order. Build it with the components in `assets/design-system.md`. Example values come from the fictional Fluxen case; none of them belongs in a real page.

## Slots

- Hero title: the map's conclusion in one line (who the real rival is, or
  where the open space sits). Lede: the executive summary in one sentence.
- Three layers: rings stay as they are (labels only change language). The
  lists hold the names from the confirmed map: layer 1 direct, layer 2
  category, layer 3 non-competitive alternatives. The callout states where
  deals are actually lost — only if the map says so.
- Positioning map (.pmap): the two axes that differentiate this market.
    · .ax--xl / .ax--xr = left / right ends of the horizontal axis;
      .ax--yt / .ax--yb = top / bottom ends of the vertical axis.
    · Each competitor: `<span class="pt" style="--x:12%;--y:85%">Name</span>`
      (x from the left, y from the bottom, 5–95%). Near the right edge add
      .pt--right so the label sits left of its dot.
    · The company today: .pt--you, placed where the map honestly says it
      sits, even if that is "nowhere".
    · Each [GAP]: `<div class="gap" style="--x:80%;--y:20%;--w:26%">`
      `<span class="chip chip--gap">GAP</span></div>`; each
      [GAP HYPOTHESIS]: .gap--hyp with `<span class="chip chip--hyp">GAP HYPOTHESIS</span>`.
    · Positions are a qualitative reading of the map, not measurements.
      Keep the "qualitative placement" note under the plot.
- Priority competitors: the 3–5 analysed, one card each: claimed category
  (.claim), promise, strength, vulnerability, source (.src).
- Hypotheses: the 2–3 positioning hypotheses with their risk.
- Open questions panel + foot + credit, as in every deliverable.

## Structure

1. **Hero.** Eyebrow: GTM Planner · Market Map · [Company]. Status pill.
   Title with its second half in `.grad`; lede; tabs on the right with
   Market current.
2. **01 Three layers of competition** — aside "Who the buyer weighs you
   against, from the same offer out to doing nothing". A `.split`: the
   rings on the left; on the right three `.layer` blocks (Direct
   competitors · same offer, same ICP / Category competitors · same job,
   different offer / Non-competitive alternatives · what they do without
   the category), each with chips, then the callout.
3. **02 Positioning map** — a `.split--wide`: the `.pmap` with axis ends,
   gaps and points, and under it the source line "Qualitative placement
   from public positioning, not measured data"; on the right a stack of
   cards: one per GAP (chip, title, a `.test` list with Relevant / Open /
   Reachable), one `.card--line` per GAP HYPOTHESIS, and a `.card--line`
   "[Company] today" with its source.
4. **03 Priority competitors** — a four-column grid (three when there are
   three) of `.comp` cards.
5. **04 Positioning hypotheses for step 3** — aside "Directions with an
   argument, not decisions"; a three-column grid of cards labelled H1–H3,
   each with its argument or its **Risk:**.
6. **05 Open questions** — dark panel, same table as the snapshot.
7. **Foot** — note "**Category dynamics:** …"; sources line and "step 2
   of 5".
8. **Credit strip**, campaign `market-map`.

Example, for tone only: title "The real rival is doing nothing until the
audit"; axes "← Suite project, months to live" / "Live in days, on existing
meters →" / "↑ Corporate energy teams" / "↓ Plants with no energy manager".
