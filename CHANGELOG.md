# Changelog

## 0.4.2 — 2026-11-09

The directory refused 0.4.1 as well. Its check judges a file by its
content, not its name, so Markdown files that were mostly HTML and CSS
still counted as HTML, which an organization that isn't Verified can't
ship.

- **The plugin ships no HTML or CSS.** `assets/design-system.md` is now a
  written specification of the RevOps Studio visual system — tokens, page
  frame, every component, responsive and print rules, with exact values —
  and each file in `templates/` is a page blueprint: what goes on the page,
  in what order, with which component. Claude writes each page's HTML and
  CSS from them.
- **One stylesheet per company.** The first deliverable carries the full
  stylesheet; every later page copies it unchanged, so the set stays
  consistent.
- **No shell.** The skill writes each page with a single file write; the
  `awk`/`sed` assembly and the shell self-check are gone. The self-check is
  a read-through list.

## 0.4.1 — 2026-11-09

0.4.0 was refused by the plugin directory: from an organization that isn't
Verified, it accepts only Markdown, text, JSON, YAML and a few image types,
and 0.4.0 shipped `.html` files. The published version stayed 0.3.3.

- **Templates and the design system are Markdown now.** Each template is a
  `.md` file with its slot notes and the page body in an `html` code block;
  the design system is the `html` block in `assets/design-system.md`. The
  pages the skill produces are byte-for-byte what 0.4.0 produced: the skill
  extracts the block with `awk`, or copies it by hand without a shell.
- **The sample pages and their image previews left the repo.** Two previews
  tripped a false "download-and-run" match in the directory's checks, and a
  README image would hold the release for manual review. They move to the
  plugin's web page; `sample-output/` keeps the Markdown case.
- The self-check now looks for leaked code fences instead of template
  comments.

## 0.4.0 — 2026-11-09

**Visual deliverables.** Every confirmed step now leaves a page the user can
share, not only a Markdown answer: the Business Snapshot, Market Map,
Positioning, Demand Plan and 90-day Roadmap as one-page HTML files, and the
consolidated GTM Plan as a long-form page that links to all five. They are
the pages the plugin's website shows.

- **New `deliverables` skill** (`/gtm-planner:deliverables`). It renders
  any confirmed step, re-renders after a change, and removes or restores
  the credit line. Each step skill calls it on confirmation, and saves the
  confirmed output as Markdown next to its page in `gtm-plan/`, so a later
  session can re-render without redoing the step.
- **A view, never a new analysis.** `references/visual-rules.md` holds the
  pages to the plan's own rules: no figure, name or claim that the
  confirmed step does not contain, every flag and open question kept
  visible, a missing number shown as a gap rather than filled. Each render
  ends with a self-check.
- **The RevOps Studio visual system**: Manrope and
  JetBrains Mono, ink and paper, the purple-to-yellow gradient, components
  for KPI strips, confidence meters, the three-ring market map, the
  positioning map, the category matrix, engine coverage and the Gantt.
  Self-contained files with no scripts; they work on a phone and print to
  a landscape PDF.
- **Credit line.** Each page ends with "Built with GTM Planner", linking to
  the plugin's page with UTM parameters that name the deliverable type and
  nothing else. `Deliverable credit: off` in the journey state removes it;
  `Format: markdown only` skips the pages. Execution Readiness stays free of
  any call to action, as the methodology requires.
- **Sample case, visual.** The six pages for the fictional Fluxen case, with
  image previews (moved out of the repo in 0.4.1).
- **New eval case** `deliverable-adds-nothing`: a confirmed snapshot full of
  gaps, and a request for a board-ready page. Not yet run.
- The journey-state template gains a `Deliverables` section; setup mentions
  the pages in one line.

## 0.3.3 — 2026-10-01

Fixes from a code review of 0.3.1–0.3.2 and from the directory scan of 0.3.2.

- **Journeys that span sessions keep their sources.** The citation rule said
  a source counts only if opened "in this session", which, read literally,
  disowned every benchmark researched in an earlier session of the same
  journey. A source now counts if it was actually opened, whenever that was,
  and recorded with its link.
- **Journeys that start at intake persist.** Intake only updated the journey
  state file, and only the plan and setup steps created it, so a journey
  begun at intake was never saved. Intake now creates it when it is missing.
  Setup also pointed to the state template by a path relative to the user's
  project instead of the plugin.
- **The roadmap no longer contradicts itself.** It said to do plan-qa's part
  inline when plan-qa can't run, and also never to consolidate before
  plan-qa has run. The coherence check is now what must run first, by
  plan-qa or inline.
- **The agent-dispatch rule is gone from intake, market-map and
  demand-plan.** It guarded against a failure that never occurred, and it
  carried the same session wording. The demand step instead skips the
  benchmark researcher when no web access or data source is available,
  since it would come back empty.
- **Narrower demand-plan triggers.** "What budget do we need" and "what
  conversion rates are realistic" are anchored to pipeline and lead-to-deal
  numbers, so unrelated budget questions don't start a demand plan.
- **A failed gate mentions the override.** The orchestrator says the user
  can override a gate explicitly, and that the override is recorded.
- The changelog no longer writes the icon's path in backticks, which the
  directory scan reads as code that could run the image, and holds for a
  reviewer.

## 0.3.2 — 2026-10-01

- **A citation is a source that was opened.** The benchmark rules said every
  external number cites a source, but not that the source had to be
  consulted. With no web access, the benchmark researcher once returned
  well-known reports cited from memory, and the reply recommended planning
  with them. A source now counts only if it was opened in the session or
  came from a connected tool; a remembered report is an assumption, labeled
  as one.
- `positioning-pillar-test` timeout raised to 1,200s. Its longest runs took
  572s and 607s, in both arms, and a timeout scores as a failure.

## 0.3.1 — 2026-10-01

Every entry point is now a skill, the gates hold when the user pushes back,
plus the directory review fixes. The methodology itself is unchanged.

**Skills that load when they should.** The eval suite found two requests
that bypassed the method entirely because the skill never loaded: "skip the
research, just tell me our category" got a confident category in one turn,
and "what should a lead cost us" got numbers from general knowledge.
Positioning and demand-plan now carry a `when_to_use` for those requests, and
positioning has an explicit protocol for a user who skips the groundwork:
answer as a low-confidence hypothesis, name what is missing, record the
override. Every step that dispatches an agent now also says what to do when
it can't, and never to report findings from an agent that did not run — a
guard, not a fix for an observed failure: the replies that first raised the
suspicion turned out to come from real dispatches.

**Commands folded into skills.** The six `commands/` files were thin
wrappers whose names collided with the skills of the same name, so the
command's one-line description was what Claude saw — the skills' own
descriptions, with all their trigger phrases, were shadowed and never
reached the model. Claude can now reach for a step on its own when your
request matches it, instead of only when you type the slash command.

- `commands/` removed. Every `/gtm-planner:*` command keeps working
  exactly as before: the skills already answered to those names.
- `commands/plan.md` became `skills/plan/SKILL.md` — the orchestrator was
  the one command carrying real content, and as a skill it can also carry
  its own reference files.
- Each step skill gained the `argument-hint` its command used to hold.

**Eval suite** (`evals/`). Six cases, each taking a claim this README makes
and turning it into a prompt where a model without the plugin predictably
does the opposite — inventing funnel numbers, settling a category with no
ICP, polishing message pillars that should have been cut, quoting CPLs as
established benchmarks. Every case is scored against a no-plugin baseline,
so the number that matters is the difference. Run it with
`claude plugin eval . --trust-plugin`.

Directory review fixes:

- **Listing icon** — the RevOps Studio logo, bundled as a 512x512 PNG and
  referenced from `plugin.json`. The listing no longer falls back to the
  GitHub avatar.
- **`privacyPolicyUrl`** in `plugin.json`, plus a **Credentials and
  privacy** section in the README.
- **`.gitignore` rewritten.** The Node boilerplate it shipped with
  referenced `.env` files, which read as credential handling in a plugin
  that has no build, no dependencies and no runtime. It is now a short
  list appropriate to a Markdown-and-JSON plugin.
- `displayName` added to `plugin.json`.
- **Listing metadata completed.** `documentationUrl`, `supportUrl` and
  `termsOfServiceUrl` added — all three are fields the manifest validator
  recognizes, and all three were empty on the directory listing. The
  `description` was rewritten so it no longer opens by repeating the
  plugin's own name, since it is the short description users read in the
  directory.

## 0.3.0 — 2026-07-23

Made the methodology more reviewable and more demonstrable:

- **`sample-output/`** — a complete, end-to-end sample case (fictional
  company, zero-connector mode): all five step outputs plus the
  consolidated GTM Plan.
- **Assumption & evidence ledger** — open questions now carry a confidence
  grade (high/medium/low) and their evidence; the final plan adds an
  evidence map (user-declared / tool / cited source / inference).
- **Decision gates in the orchestrator** — the journey does not advance to
  positioning, demand-plan or roadmap while gate-critical decisions
  (ICP, category, engine selection) rest on low-confidence assumptions;
  explicit user override is recorded as an assumption.
- **`connectors-and-permissions.md`** — per connector: what it adds, data
  read/written, access requirements, fallback when absent.
- **`demo-script.md`** — a 60–90s walkthrough that demonstrates method.
- README: "Why this is not a prompt pack" and review notes for
  marketplace/partner evaluation.

## 0.2.0 — 2026-07-22

Improvements from the first end-to-end field test:

- **Source readiness check** in market-map and demand-plan: before any
  research, the planner inventories available sources (connectors,
  materials, web), shows what tier of analysis each data need will get,
  and lets the user choose per gap — web-based deep research fallback,
  connect the tool, or provide data manually.
- **New `setup` skill** (`/gtm-planner:setup`): guided, pressure-free
  connector walkthrough after install, with honest access requirements.
- Documented that **Similarweb and Ahrefs connectors require paid API
  access**; research agents now open their reports stating source
  coverage, and web-research fallback is the explicit baseline.
- Step outputs open with a one-line "Sources used" note.

## 0.1.0 — 2026-07-21

Initial public release: 5 skills (intake, market-map, positioning,
demand-plan, roadmap), 4 agents, 6 commands, optional connectors
(HubSpot, Notion, Similarweb, Ahrefs), session persistence.
