# Design system

The RevOps Studio visual system for every GTM Planner deliverable, written as
a specification. You build each page's stylesheet from it. The values here
are exact: use them as given, never approximate them, never add colours,
fonts or effects of your own.

## How a page is built

- One self-contained file: a doctype, `<html lang="…">` in the user's
  language, a `<head>` with `meta charset="utf-8"`, the viewport meta, the
  title, a meta description and the font link below, one `<style>` block,
  then the body. No scripts, no external images, no other stylesheets.
- Fonts: preconnect to `https://fonts.googleapis.com` and
  `https://fonts.gstatic.com` (crossorigin), then load
  `https://fonts.googleapis.com/css2?family=JetBrains+Mono:wght@400;500;700&family=Manrope:wght@400;500;600;700;800&display=swap`.
  Every font stack ends in system fallbacks, so the page stays readable
  offline.
- **One stylesheet per company.** The first deliverable written for a company
  carries the complete stylesheet: every section of this specification, not
  only the components that page uses. Every later page copies that `<style>`
  block unchanged from a page already in the folder. The set then looks like
  one document, and nobody has to rebuild it.
- Define the colours below as custom properties on `:root` and refer to them
  everywhere else. Inline `style` attributes are allowed only for the
  positional values named in the components (`grid-column`, `--x`, `--y`,
  `--w`, `--from`, `--to`).

## Tokens

### Colour

| Token | Value | Use |
|---|---|---|
| `--ink` | `#0a0612` | dark surfaces: hero, panels, credit strip |
| `--ink-2` | `#14091f` | boxes on dark |
| `--ink-3` | `#1f132e` | reserved |
| `--ink-4` | `#2c1d40` | row rules inside dark panels |
| `--line-dark` | `#3a2954` | borders on dark |
| `--paper` | `#faf7f2` | page background |
| `--paper-2` | `#f4ede2` | cards |
| `--paper-3` | `#e9dfd0` | tracks, empty meter segments on paper |
| `--line` | `#d6c9b3` | rules and borders on paper |
| `--line-soft` | `#e6dccb` | table row rules on paper |
| `--fg` | `#14091f` | text on paper |
| `--fg-2` | `#4a3d5c` | secondary text on paper |
| `--fg-3` | `#7a6e8a` | labels, sources, asides |
| `--on-dark` | `#faf7f2` | text on dark |
| `--on-dark-2` | `#c9bdd6` | secondary text on dark |
| `--on-dark-3` | `#8a7c9e` | asides on dark |
| `--lilac` | `#a99bbf` | muted half of a title; low-impact bars |
| `--purple-700` | `#8114b0` | section numbers, labels, medium-impact bars |
| `--purple-500` | `#b427a3` | hypothesis outlines |
| `--magenta` | `#e13798` | warnings in text, the company's own dot label |
| `--pink` | `#fe5688` | accents: eyebrow, active tab, goal, meters, risk |
| `--coral` | `#fb9a6a` | third funnel stage |
| `--yellow` | `#f7fd3d` | end of the brand gradient only |
| `--warn` | `#f8dd4b` | draft status, warning chips |
| `--ok` | `#2dd4a8` | confirmed status dot, pass chips |

### Gradients

- **Brand** (`--grad`): 135deg — `#8114b0` 0%, `#c129a1` 32%, `#fe5688`
  58%, `#fb9a6a` 78%, `#f7fd3d` 100%. Used for the GAP chip and dots.
- **Bar** (`--grad-bar`): 90deg — `#b427a3` 0%, `#e13798` 30%, `#fe5688`
  62%, `#fb9a6a` 100%. Used for high-impact bars, signal bars and the
  legend swatch.
- **Text** (`--grad-text`): 90deg — `#d42ea0` 0%, `#fe5688` 45%, `#fb9a6a`
  78%, `#f3d64a` 100%. Applied to `.grad` spans with background-clip text
  and a transparent text colour.

### Type

- Sans: Manrope, then ui-sans-serif, system-ui, -apple-system, "Segoe UI",
  sans-serif. Body text 16px, line-height 1.55, weight 400, antialiased.
- Mono: JetBrains Mono, then "SF Mono", Menlo, Consolas, monospace. Used for
  figures, labels, eyebrows, chips, sources and section numbers.
- Labels (`.label`): mono 500, 12px, letter-spacing .14em, uppercase,
  `--fg-3`.

### Shape and space

- Radii: 8px (small), 14px (medium), 22px (large: cards), 30px (extra:
  panels), 999px (pill).
- Page gutter `clamp(16px, 4.4vw, 86px)`; content max width 1760px, centred.
  `.wrap` applies both.
- Grid gaps `clamp(14px, 1.4vw, 24px)`. Section bottom margin
  `clamp(36px, 3.4vw, 56px)`.
- `box-sizing: border-box` everywhere; `print-color-adjust: exact` on
  `html` so dark surfaces print.

## Page frame

### Hero

- Full-width dark band (`.hero`, overflow hidden, text `--on-dark`).
  Background: `--ink` under two radial glows — an ellipse 55% × 140% at 92%
  −10% from `rgba(91,11,135,.55)` to transparent at 62%, and an ellipse
  35% × 90% at 78% −20% from `rgba(254,86,136,.22)` to transparent at 60%.
- Inner `.wrap` padding: top `clamp(36px,4vw,64px)`, bottom
  `clamp(36px,3.6vw,56px)`.
- **Top row** (`.hero__top`): flex, space-between, wraps. Left the eyebrow,
  right the status pill.
- **Eyebrow** (`.eyebrow`): mono 500, 13px, letter-spacing .2em, uppercase,
  `--pink`. Its parts are spans separated by a pink " · " drawn before each
  span after the first.
- **Status pill** (`.status`): mono 500, 13px, `--on-dark-2`, 1px
  `--line-dark` border, pill radius, padding 11px 18px, no wrapping.
  `.status--ok` adds a 7px `--ok` dot before the text; `.status--draft`
  turns text `--warn` and the border `rgba(248,221,75,.45)`.
- **Body row** (`.hero__body`): flex, space-between, aligned to the bottom,
  wraps, gap 32px 48px, top margin `clamp(28px,3vw,44px)`. Its first child
  grows (`flex: 1 1 720px`, min-width 0); a second child keeps its size.
- **Title** (`.hero__title`): Manrope 800, `clamp(38px,4.3vw,72px)`,
  line-height 1.04, letter-spacing −.035em, max width 24ch (none with
  `.hero__title--wide`). A `.grad` span carries the decisive half; a
  `.muted` span is `--lilac`.
- **Lede** (`.hero__lede`): 400, `clamp(16px,1.25vw,22px)`, line-height
  1.45, `--on-dark-2`, max width 62ch, top margin 18px.
- **Tabs** (`.tabs`): flex row of pills, gap 8px, wraps. Each link or span:
  15px Manrope 500, `--on-dark-2`, 1px `--line-dark` border, pill radius,
  padding 13px 16px, background `rgba(20,9,31,.5)`, no underline. The
  current page (`aria-current="page"`) is filled `--pink` with white 600
  text. A deliverable that doesn't exist yet is a span at 40% opacity.
  `.tabs--row` puts the tabs on their own row with top margin
  `clamp(24px,2.4vw,36px)`. Always six tabs, in this order, with these
  labels (translated) and `data-tab` values: "1 Snapshot" (`01`), "2 Market"
  (`02`), "3 Positioning" (`03`), "4 Demand" (`04`), "5 Roadmap" (`05`),
  "GTM Plan" (`00`). Each links to its fixed file name.
- **Goal chain** (`.chain`): flex row, gap 10px, wraps. Each step
  (`.chain__step`): `--ink-2` background, 1px `--line-dark` border, 14px
  radius, padding 16px 20px, min width 96px; value in a `b`, mono 500,
  `clamp(22px,1.7vw,30px)`; label in a span, mono 400 15px `--on-dark-2`,
  6px above. Arrows between steps are spans (`.chain__arrow`) holding "→", mono
  14px `--pink`. The goal
  step (`.chain__step--goal`) is filled `--pink` with `--ink` text.

### Main column and sections

- `main` is a `.wrap` with top padding `clamp(32px,3.2vw,56px)`.
- A **section** is a `section.section` (bottom margin as in Tokens), opened by
  a section head. Sections are numbered 01, 02… in page order; the KPI strip,
  the promise block and the foot are not numbered.
- **Section head** (`.section__head`): flex, space-between, baseline,
  wraps, 22px below. Title (`.section__title`): Manrope 700,
  `clamp(22px,1.7vw,30px)`, line-height 1.2, letter-spacing −.02em. Its
  number (`.n`) is mono 500 at .62em, `--purple-700`, 0.7em right margin,
  raised .18em. Aside (`.section__aside`): 15px, `--fg-3`, max 60ch.
- **Lead paragraph** (`.lead`): 500, `clamp(17px,1.25vw,21px)`, line-height
  1.5, max 78ch.

### Foot and credit

- **Foot** (`.foot`): flex, space-between, aligned to the bottom, wraps, gap
  24px 48px, padding `clamp(28px,3vw,56px)` top and
  `clamp(28px,2.6vw,44px)` bottom. Note (`.foot__note`): max 72ch,
  `clamp(16px,1.15vw,19px)`, `--fg-2`, its bold lead-in `--fg`. Sources
  (`.foot__src`): mono 13px, line-height 1.6, `--fg-3`, right-aligned.
- **Credit strip** (`.credit`): a full-width link on `--ink`, no underline,
  text `--on-dark-2`. Inside a `.wrap`: flex, centred, gap 14px, 16px
  vertical padding. Mark (`.credit__mark`): 16 × 18px, the RevOps Studio
  "R" as a background image — the exact data URI is in
  `../references/visual-rules.md`. Text (`.credit__text`): 14px, its bold
  part `--on-dark` 700. URL (`.credit__url`): mono 500 13px `--pink`,
  pushed right with an auto left margin; underlined on hover.

## Components

### Figures

- **KPI strip** (`.kpis`): grid of auto-fit columns, minimum 170px, gap
  `clamp(16px,2vw,28px)`, bottom margin `clamp(28px,2.6vw,40px)`. Each
  `.kpi`: 2px `--fg` top border, 18px top padding; value in a `b`, mono
  500, `clamp(26px,2.2vw,38px)`, letter-spacing −.01em; label in a span,
  16px `--fg-2`, 10px above. `.kpi--accent` makes the border `--pink`.
  `.kpi--est` marks a declared-but-unverified figure: after the value, a
  `small.est` holding "est." in the page's language, mono 500 11px `--fg-3`,
  letter-spacing .08em, 8px left margin, raised .9em. It is written in the
  markup, not generated by CSS, so the stylesheet stays the same in every
  language.
- **Confidence / weight meter** (`.meter`): inline-flex of three `i`
  segments, 18 × 6px, radius 4px, gap 6px, unfilled `#3a2954` (on paper,
  `.meter--light`, unfilled `--paper-3`). `data-level="1|2|3"` fills that
  many segments `--pink`; `0` fills none. An optional `b` after the
  segments carries the word (Low, Medium, High) in Manrope 700 16px, 8px
  left margin.
- **Dot** (`.dot`): 12px circle in the brand gradient; `.dot--mid` solid
  `--purple-700`; `.dot--low` hollow with a 2px `--purple-500` ring.

### Cards and grids

- Grids: `.grid` with `.g2` … `.g5` equal columns. `.split` is two columns
  5fr / 7fr, gap `clamp(18px,2vw,36px)`, aligned to the top;
  `.split--wide` swaps them to 7fr / 5fr.
- **Card** (`.card`): `--paper-2`, 22px radius, padding
  `clamp(20px,1.7vw,30px)`. Title (`.card__title`): Manrope 700 19px,
  line-height 1.3, 12px below; its number (`.num`) mono 14px `--purple-700`.
  Body text 16px `--fg-2`. `.card--line` is transparent with a 1px `--line`
  border. `.card--dark` is `--ink` with `--on-dark-2` text.
- **Quarter / phase label** (`.q-label`): mono 500 15px `--purple-700`,
  12px below.
- **Dark pill** (`.pill-dark`): `--ink`, white 600 15px, pill radius,
  padding 10px 16px, 12px above — a dated review or gate.
- **Callout** (`.callout`): `--ink`, `--on-dark`, 14px radius, padding
  16px 20px, Manrope 600 16px, preceded by a pink "→ ".
- **"More" link** (`.more`): mono 500 13px `--purple-700`, no underline
  until hover; `--pink` inside a dark panel.

### Chips and source lines

- **Chip** (`.chip`): mono 500 12.5px, `--fg-2`, 1px `--line` border, pill,
  padding 7px 12px, no wrapping. Variants:
  - `.chip--dark` — on dark panels: border `--line-dark`, text `--on-dark-2`.
  - `.chip--pink` — filled `--pink`, `--ink` text.
  - `.chip--warn` — border `#d9bf2c`, text `#7a6400`, fill
    `rgba(248,221,75,.18)`. For `unverified claim`, `needs benchmark`,
    `assumption` on paper.
  - `.chip--ok` — border `#2aa886`, text `#11624d`, fill
    `rgba(45,212,168,.12)`.
  - `.chip--gap` — brand gradient fill, no border, white 700.
  - `.chip--hyp` — dashed 1px `--purple-500` border, `--purple-700` text.
- `.chips`: flex wrap, gap 8px.
- **Owner to be named** (`.tbd`): Manrope 600 14px, `--pink` fill, `--ink`
  text, 8px radius, padding 4px 8px.
- **Source line** (`.src`): inline-block, mono 500 11.5px, line-height 1.5,
  letter-spacing .04em, `--fg-3`, preceded by "↳ ". Links inside are
  `--purple-700`.

### Dark panel and tables

- **Panel** (`.panel`): `--ink`, `--on-dark`, 30px radius, padding
  `clamp(22px,2.4vw,40px)`. Inside it the section title is `--on-dark`,
  its number `--pink`, the aside `--on-dark-3`.
- **Table** (`.tbl`, inside a horizontally scrollable `.table-wrap`): full
  width, collapsed borders, 16px. Header cells: mono 500 12.5px,
  letter-spacing .16em, uppercase, `--fg-3`, 16px below, 1px `--line`
  bottom rule, no wrapping. Body cells: padding 18px 16px 18px 0, 1px
  `--line-soft` bottom rule, top-aligned, `--fg-2`; `.strong` cells are
  `--fg` 600. Inside a panel: headers `--on-dark-2` with `--line-dark`
  rules, cells `--on-dark` with `--ink-4` rules, `.soft` cells
  `--on-dark-2`.
- **Risk tag** (`.risk`): mono 700 12px, letter-spacing .06em, uppercase,
  `--pink`.

### Roadmap: the Gantt

- `.gantt` (horizontal scroll) holds `.gantt__inner` (position relative,
  min width 980px). Custom properties on `.gantt`: `--label: 34%` (label
  column) and `--weeks: 13`.
- Rows (`.g-row`): grid of two columns, `var(--label)` and the rest;
  centred; 1px `--line-soft` bottom rule; min height 88px. The header row
  (`.g-row--head`) aligns to the bottom, has a `--line` rule and 14px
  bottom padding, and no min height.
- Track (`.g-track`): grid of `--weeks` equal columns, 12px left padding,
  above the blackout. Week cells (`.g-week`): mono 500 13px, `--fg-3`,
  centred, uppercase, letter-spacing .04em; a `small` inside shows the
  date on its own line, not uppercase.
- Label (`.g-label`, padding 16px 24px 16px 0): an `h4` in Manrope 700
  `clamp(16px,1.1vw,19px)` with its number (`.n`) in mono `--purple-700`;
  a `p` meta line 15px `--fg-2`, 5px above.
- Bar (`.bar`): sits on the track's first row, spans
  `grid-column: [first week] / [last week + 1]`, 36px high, pill radius,
  the bar gradient, flex centred, 16px side padding, position relative.
  `.bar--mid` is solid `--purple-700`; `.bar--low` is `--lilac`.
  Milestone (`.ms`): absolutely placed just right of the bar (14px gap),
  no wrapping, Manrope 500 15px `--fg-2`, preceded by "◆ " at .85em. With
  `.bar--in` the milestone sits inside the bar instead: static, white 600,
  ellipsis on overflow (`--ink` text on a low bar).
- Blackout (`.blackout`, optional, first child of `.gantt__inner`): an
  absolutely placed band behind the tracks from `--from` to `--to` (week
  numbers), positioned with `left: calc(var(--label) + 12px + (100% -
  var(--label) - 12px) * (var(--from) - 1) / var(--weeks))` and the
  matching width; 14px radius; diagonal hatching (−45deg repeating lines of
  `rgba(214,201,179,.55)` 2px every 13px) over `rgba(233,223,208,.6)`. Its
  label: mono 500 13px `--fg-2`, centred at the top.
- Legend (`.legend`): flex wrap, gap 12px 28px, 15px `--fg-2`, 20px above.
  Swatches are 38 × 12px rounded bars (bar gradient; `.mid` purple;
  `.low` lilac) with 10px right margin.

### Market map

- **Rings** (`.rings`): square, full width up to 500px, centred. Three
  absolutely centred circles: `.ring--3` 100% on `--paper-2` with a 2px
  dashed `--pink` border (alternatives; label `--magenta`); `.ring--2` 68% on
  `--paper-3` (category; label `--fg-2`); `.ring--1` 37% on `--ink`
  (direct; label `--on-dark`, centred vertically). Outer labels sit 14px
  from the top of their ring: mono 500 12.5px, letter-spacing .12em,
  uppercase, centred.
- **Layer list** (`.layer`): 3px left rule (`.layer--1` `--ink`,
  `.layer--2` `--lilac`, `.layer--3` `--pink`), 18px left padding, 22px
  below; an `h4` Manrope 700 17px with a `small` qualifier in mono 12px
  uppercase `--fg-3`; then chips.
- **Positioning map** (`.pmap`): 16:10, `--paper-2`, 22px radius, overflow
  hidden; two 1px `--line` rules through the centre — the vertical one at
  50% from the left, running from 7% below the top to 7% above the bottom;
  the horizontal one at 50% from the top, running from 5% to 5% of the
  sides. Axis ends (`.ax--xl`, `.ax--xr` on the horizontal
  middle, just below the rule; `.ax--yt`, `.ax--yb` at top and bottom, just
  right of the rule): mono 500 12px, letter-spacing .06em, `--fg-3`, max
  28% wide.
- Points (`.pt`): absolutely placed at `left: var(--x)`, `bottom: var(--y)`,
  centred on that spot, a 13px `--ink` dot then the name in Manrope 600
  14px, no wrapping, above the gaps. `.pt--you` is a 16px white dot with a
  3px `--pink` ring and a `--magenta` name. `.pt--right` puts the name on
  the left of its dot.
- Gaps (`.gap`): ellipse (aspect 1.6) of width `var(--w, 26%)` centred on
  `--x`/`--y`, 2px dashed `--pink` border, `rgba(254,86,136,.08)` fill,
  its chip centred. `.gap--hyp`: `--purple-500` border,
  `rgba(180,39,163,.05)` fill.
- **Competitor card** (`.comp`): name `h4` 700 18px; claimed category
  (`.claim`) mono 500 13px `--purple-700`; a vulnerability block
  (`.vuln`), 14px above, under a 1px `--line` rule with 12px padding,
  headed by a `b` label: mono 700 12px, letter-spacing .1em, uppercase,
  `--magenta`, on its own line.

### Positioning

- **Promise** (`.promise`): `--ink`, 30px radius, padding
  `clamp(28px,3.4vw,60px)`, position relative, overflow hidden. Its glow
  is a pseudo-element placed at inset auto −10% −60% 40% with 120% height:
  a radial gradient from `rgba(254,86,136,.22)` at the centre to
  transparent at 65%. Content sits above it.
  Eyebrow, then the promise in a `blockquote`: Manrope 800
  `clamp(28px,3.1vw,54px)`, line-height 1.08, letter-spacing −.03em, max
  24ch, its second half in `.grad`. Fallback (`.fallback`) 17px
  `--on-dark-2`; reasons (`.why`) 15px `--on-dark-3`, max 80ch.
- **Category matrix** (`.tbl.matrix`): 16px left padding on the first
  column. The chosen row (`tr.is-chosen`) gets a wash on its cells — a
  90deg gradient from `rgba(254,86,136,.10)` to `rgba(251,154,106,.05)` —
  and a 3px `--pink` inset rule on its first cell. Cells hold a light
  meter (14px segments, gap 4px) and a `small` reading (13px `--fg-3`,
  6px above).
- **Pillar** (`.pillar`): a card with its label, an `h4` 700 20px, then the
  test list (`.test`): no bullets, 1px `--line` top rule, 14px above. Each
  `li` is a three-column grid (22px · 118px · rest): a mark, the check name
  in a `b` (mono 500 11.5px uppercase `--fg-3`), the reason in a span
  14.5px `--fg-2`; rows 9px apart. Marks: "✓" `#11624d` (pass), "◐" `#9a7d00`
  (`.partial`), "✕" `--magenta` (`.fail`).
- **Funnel stage** (`.stage`): 3px top rule (`.stage--1` `--purple-700`,
  `.stage--2` `--pink`, `.stage--3` `--coral`), 16px top padding; label;
  the dominant message (`.msg`) Manrope 700 `clamp(18px,1.35vw,23px)`;
  variants as a 15px list.
- **Anti-messages** (`.anti`, inside a panel): no bullets; each `li` a
  two-column grid, 14px vertical padding, `--line-dark` bottom rule. The
  struck line (`s`) is `--on-dark` 600 with a 2px `--pink` strike; the
  reason (`span`) 15px `--on-dark-2`.

### Demand plan

- **Coverage table** (`.tbl.cov`): stage cells centred, holding dots.
- **Signal bar** (`.signal`): 10px high, 6px radius, `--paper-3` track,
  min width 140px; its `i` is the bar-gradient fill from `--from` to `--to`
  (percentages of the scale). Scale (`.signal-scale`): evenly spaced labels,
  mono 500 11px `--fg-3`, 6px above.
- **Engine card** (`.engine`): an `h4` 700 19px; a `.meta` row of chips and
  sources, 14px above.
- **Discard** (`.discard`): 1px dashed `--line` border, 14px radius,
  padding 16px 18px; its `h4` 700 16px struck through in `--magenta` (2px);
  reason 14.5px `--fg-2`.
- **Phase** (`.phase`): `--paper-2`, 22px radius, padding 22px 24px, list
  15.5px `--fg-2`. The first 90 days (`.phase--now`) is `--ink` with
  `--on-dark-2` text and a `--pink` label.

### Consolidated plan

- **Decision chain** (`.dchain`): five equal columns, gap 10px. Each step:
  `--ink-2`, 1px `--line-dark` border, 14px radius, padding 18px 18px 20px;
  a `.label` in `--pink`; the decision in a `p`, Manrope 600 16px
  `--on-dark`, 10px above. Each step (`.dchain__step`) but the last shows a
  pink "→" on its right edge, drawn after it.
- **Contents bar** (`.toc`): sticky at the top, `rgba(250,247,242,.92)`
  with an 8px backdrop blur, 1px `--line` bottom rule; a scrolling row of
  links, 14px `--fg-2`, pill hover on `--paper-2`, each with its number in
  mono 12px `--purple-700`.
- **Chapter** (`.chapter`): 1px `--line` top rule and
  `clamp(28px,2.6vw,44px)` top padding; starts a new page in print.
- **Evidence tiles** (`.evidence`, inside the ledger panel): four columns,
  gap 12px; each tile 1px `--line-dark` border, 14px radius, 16px padding;
  a mono 500 12px uppercase `--pink` heading; text 14.5px `--on-dark-2`.
- **Workstream card** (`.ws`): a card with an `h4` 700 19px and an
  "If skipped" block (`.skip`), 14px above, under a 1px `--line` rule
  with 12px padding: a `b` label in mono 700 12px uppercase `--magenta` on
  its own line, then 15px `--fg-2`.

## Responsive

- Up to 1100px wide: four- and five-column grids and three-column grids
  become two columns; `.split` and `.split--wide` stack; the decision chain
  and evidence tiles become two columns and the chain arrows disappear.
- Up to 680px wide: every grid is one column; anti-message rows stack; the
  pillar test drops its middle column (check name and reason both in the
  third); the credit URL loses its auto margin; sources align left; the
  status pill may wrap and the hero top row stacks; points on the
  positioning map shrink to 12px with the map at 4:5 and axis labels at
  10.5px (max 42% wide); tables keep a 620px minimum width and scroll.
- Never let the page itself scroll sideways: wide things (tables, the
  Gantt) scroll inside their own wrapper.

## Print

- Page: A4 landscape, no margin. Zoom the document to .62.
- Keep the desktop columns in print (grids, splits, decision chain,
  evidence tiles), even though the printed page is narrow.
- Avoid breaking inside sections, cards, Gantt rows, panels, the promise
  block and phases. Each chapter of the consolidated plan starts a new page.
- The contents bar stops being sticky; links lose their underline.
