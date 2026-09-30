# Changelog

## 0.3.1 — 2026-10-01

Every entry point is now a skill, plus the directory review fixes. No
change to the methodology or to any step's output.

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

- **Listing icon** — `assets/icon.svg`, referenced from `plugin.json`, in
  the RevOps Studio palette. The listing no longer falls back to the
  GitHub avatar.
- **`privacyPolicyUrl`** in `plugin.json`, plus a **Credentials and
  privacy** section in the README.
- **`.gitignore` rewritten.** The Node boilerplate it shipped with
  referenced `.env` files, which read as credential handling in a plugin
  that has no build, no dependencies and no runtime. It is now a short
  list appropriate to a Markdown-and-JSON plugin.
- `displayName` added to `plugin.json`.

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
