# Page blueprint · Step 3 · Positioning Architecture (one page)

The page blueprint: what goes on this page and in what order. Build it with the components in `assets/design-system.md`. Example values come from the fictional Fluxen case; none of them belongs in a real page.

## Slots

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

## Structure

1. **Hero.** Eyebrow: GTM Planner · Positioning · [Company]. Status pill.
   Title: the chosen category, qualifying half in `.grad`. Lede: that this
   is the category chosen over the alternatives and that everything
   downstream builds on it. Tabs with Positioning current.
2. **01 Category decision** — aside "The most consequential decision in
   the plan. Bars show how favourable each reading is". A `.matrix` table:
   Candidate · one column per criterion; the chosen row `is-chosen` with a
   pink "Decision" chip after its name. Then a `.lead` paragraph: the
   decision, what it absorbs, what it gives up.
3. **Promise block** — eyebrow "Core promise", the blockquote, fallback,
   why it is credible.
4. **02 Pillars** — aside on the three-part test and on any pillar cut;
   a three-column grid (four when there are four) of `.pillar` cards:
   label "Pillar N" (plus "· decisive" or "· supports, never leads" when the
   step says so), title, one-line claim, the test list.
5. **03 Segment translations** — a two-column grid: primary segment as a
   card, secondary as `.card--line`; label with the segment, the promise in
   their words as the title, the heaviest pillars, vocabulary chips.
6. **04 Messages by funnel stage** — aside "Awareness and decision must not
   sound alike"; three `.stage` columns: Awareness · present the category /
   Consideration · push to the conversation / Decision · kill objections,
   create urgency.
7. **05 Anti-messages** — dark panel with the `.anti` list.
8. **06 What this changes tomorrow** — three cards: Homepage hero, First two
   minutes of the pitch, Content (Fits / Clashes).
9. **07 Open questions** — dark panel.
10. **Foot** — note on the gate (confirmed or pending); sources "Built on
    the confirmed Snapshot and Market Map" and "step 3 of 5".
11. **Credit strip**, unless the journey state turns it off.
