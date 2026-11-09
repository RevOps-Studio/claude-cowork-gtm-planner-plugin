---
name: deliverables
description: >
  This skill should be used to render the visual deliverables of a GTM plan:
  when a planner step has just been confirmed, or when the user asks to "make
  the one-pager", "render my snapshot", "show me the roadmap visually",
  "export the plan", "give me something I can share with my team or board",
  "print the plan to PDF", "/gtm-planner:deliverables", or to remove or
  restore the credit line. Turns confirmed step outputs into branded,
  self-contained HTML pages: Business Snapshot, Market Map, Positioning,
  Demand Plan, 90-day Roadmap and the consolidated GTM Plan.
argument-hint: [step to render, or "all"]
metadata:
  version: "0.4.0"
  author: "RevOps Studio"
---

# Visual deliverables

Each confirmed step of the journey has a one-page visual: the same content
the user confirmed, laid out so it can be read in two minutes, shared with a
team, sent to a board or printed to PDF. The consolidated GTM Plan is the
long-form version of all five.

A deliverable is a **view** of a confirmed output, never a new analysis. It
adds no figure, competitor, claim or recommendation that the confirmed step
does not contain, and it keeps every flag the step raised. The rules are in
`references/visual-rules.md`; read them before the first render of a session.

Respond in the language the user is writing in, and write the deliverable in
that language too.

## What gets rendered

| Deliverable | Rendered when | From | Template |
|---|---|---|---|
| `01-business-snapshot.html` | intake is confirmed | the confirmed snapshot | `templates/01-business-snapshot.html` |
| `02-market-map.html` | market-map is confirmed | the confirmed map | `templates/02-market-map.html` |
| `03-positioning.html` | positioning is confirmed | the confirmed architecture | `templates/03-positioning.html` |
| `04-demand-plan.html` | demand-plan is confirmed | the confirmed demand plan | `templates/04-demand-plan.html` |
| `05-roadmap.html` | roadmap is confirmed | the 90-day table + outline | `templates/05-roadmap.html` |
| `00-gtm-plan.html` | the GTM Plan is consolidated | the consolidated plan | `templates/00-gtm-plan.html` |

Templates live in `${CLAUDE_PLUGIN_ROOT}/skills/deliverables/`. Each is a
body fragment filled with the fictional Fluxen example and annotated with its
slots in an HTML comment at the top. The design system is
`assets/head.html`; it is copied verbatim, never edited per company.

## Process

1. **Locate the content.** Read `.claude/gtm-planner.local.md` for the
   journey state, the company name and the `Deliverables` settings. Read the
   confirmed step output from the deliverables folder (default `gtm-plan/`,
   e.g. `gtm-plan/01-business-snapshot.md`) or, right after a confirmation,
   from the conversation. A step that is not confirmed is rendered only if
   the user asks for it, and then as a draft (status "Draft — not
   confirmed"). If the journey state says `Format: markdown only`, render
   nothing unless the user asks.
2. **Read the template** for the deliverable and `references/visual-rules.md`.
3. **Write the body.** Replace every piece of example content with this
   company's confirmed content, following the slot notes in the template's
   top comment. Keep the template's structure, classes and section order;
   drop a section only when the step output has nothing for it, and say so
   in the reply. Translate every visible label into the user's language.
   Remove every template comment.
4. **Assemble one self-contained file** in the deliverables folder. Write the
   body to a temporary file, then join it to the design system:

   ```bash
   mkdir -p gtm-plan
   sed 's/<html lang="en">/<html lang="es">/' "${CLAUDE_PLUGIN_ROOT}/skills/deliverables/assets/head.html" > gtm-plan/01-business-snapshot.html
   cat gtm-plan/.body.html >> gtm-plan/01-business-snapshot.html && rm gtm-plan/.body.html
   ```

   Use the user's language code in the `sed` (`en`, `es`, `pt`, `fr`…).
   Without a shell, read `assets/head.html` and write the whole document in
   one file: the head block exactly as it is, then the body.
5. **Link the set.** In every deliverable already in the folder, turn the new
   one's tab into a link, e.g. for positioning:
   `sed -i 's|<span data-tab="03">\([^<]*\)</span>|<a data-tab="03" href="03-positioning.html">\1</a>|' gtm-plan/*.html`
6. **Self-check** the file against the checklist at the end of
   `references/visual-rules.md`. Fix what fails before telling the user.
7. **Hand it over** in two or three lines: the file path, that it opens in
   any browser and prints to PDF (landscape) from the browser's print
   dialog, and anything left out because the step had no content for it.
   If the client can display HTML or publish a page, offer that once.

## The credit line

Every deliverable ends with a one-line credit: *Built with GTM Planner, a
free Claude plugin by RevOps Studio*, linking to the plugin's page with
UTM parameters that name the deliverable (exact markup and links in
`references/visual-rules.md`). It is the only mention of RevOps Studio in the
deliverable. Never add sales copy, calls to action or service offers
anywhere else — least of all in Execution Readiness, which the methodology
keeps free of them.

When the user asks to remove it, remove it from the existing files, set
`Deliverable credit: off` in the journey state, and confirm in one line. No
pushback, no second ask. `on` restores it.

## What NOT to do

- No figure, name or claim that the confirmed step output does not contain.
  A visual that needs a number the step doesn't have shows the gap, not a
  plausible number.
- No dropping of flags (`assumption`, `needs-benchmark`, `unverified-claim`,
  estimates) or open questions to make a page cleaner.
- No editing of the design system, no external images, no company logos
  fetched from the web, no scripts.
- No leftover example content: "Fluxen", its figures or the "Example ·
  fictional company" status never appear in a real deliverable.
- No rendering before the step is confirmed unless the user asks, and then
  marked as a draft.
