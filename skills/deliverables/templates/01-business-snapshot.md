# Page blueprint · Step 1 · Business Snapshot (one page)

The page blueprint: what goes on this page and in what order. Build it with the components in `assets/design-system.md`. Example values come from the fictional Fluxen
case; none of them belongs in a real page.

## Slots

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

## Structure

1. **Hero.** Eyebrow: GTM Planner · Business Snapshot. Status pill. Wide
   title (`.hero__title--wide`): the company, then a `.muted` "→ [the move
   this plan is for]". Lede: what they sell · category · city. Right side:
   the tabs, with Snapshot current.
2. **KPI strip** — 4–5 KPIs.
3. **Snapshot cards** — a four-column grid of eight cards, numbered 01–08:
   Business context, Offer, Target segment, Funnel and cycle, Stack,
   Revenue team, Stated goals, Constraints.
4. **Open questions** — a dark panel, section 09, aside "Each with its type,
   the confidence in what we know, and the step that would settle it".
   Table: Type (dark chip) · Question · Confidence (meter with its word) ·
   Next step (`.soft`).
5. **Foot** — note "**Snapshot confidence:** …"; sources "Figures declared
   by the company · [what is or isn't connected]" and "Go2Rev methodology ·
   step 1 of 5".
6. **Credit strip**, unless the journey state turns it off.

Example, for tone only (fictional Fluxen): title "Fluxen → beyond the
founder network"; KPIs €900k ARR today, 14 plants live, "8 plants — new in
12 months: the goal" (accent), €18k average deal, ≤ €4k marketing budget per
month.
