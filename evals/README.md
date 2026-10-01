# Eval suite

Seven cases that test whether the planner's **method** survives contact with
a real request — not whether its research is good.

Each case takes a claim the README makes and turns it into a prompt where a
model without the plugin predictably does the opposite. `claude plugin eval`
runs every case twice: once with the plugin loaded and once with no plugin at
all. The number that matters is `Δ`, the difference. A case that scores 1.0 in
both arms proves nothing — Claude was already doing it.

## Run it

Pin both models. Without `--model`, the agents under test run on whatever your
Claude Code default is today, and a model change then reads as a plugin
change: a stronger baseline shrinks `Δ` without the plugin doing anything
differently.

```bash
claude plugin eval . --trust-plugin --model claude-opus-5 --judge-model claude-sonnet-5-5 -j 4
```

Add `--keep-temp` to keep each run's `trace.jsonl`, which is the only record of
which tools a run actually called. The HTML report doesn't include it.

While iterating on a rubric, skip the baseline arm and run each case once:

```bash
claude plugin eval . --trust-plugin --ablation none --runs 1 --case gate-blocks-premature-positioning
```

By tag: `--tag gates`, `--tag no-invented-data`, `--tag method`. A full pass
is 7 cases × 3 runs × 2 arms, so put a ceiling on it with `--max-cost-usd`.

## The cases

| Case | The claim it tests | What a no-plugin model does instead |
|---|---|---|
| `connector-honesty` | No connector is required, and Similarweb and Ahrefs need a paid API plan | Doesn't know the product; gives generic CRM advice |
| `intake-open-questions` | Open questions, not invented data | Fills the gaps with plausible funnel numbers |
| `gate-blocks-premature-positioning` | The category gate holds even when the user asks to skip the process | Delivers a confident positioning statement |
| `demand-plan-gates-without-foundation` | The demand step stops for its missing foundation | Returns a channel plan with a budget split |
| `demand-engines-not-tactics` | Engines, not tactics — given the foundation | Returns a channel list |
| `benchmarks-not-invented` | Estimates come with concrete routes to verified figures | Says to replace the estimates after weeks of spend |
| `positioning-pillar-test` | Pillars are tested for defensibility, not shipped on trust | Polishes unproven claims into messaging |

## Cold cases and warm cases

Every run starts in an empty workspace, with no `.claude/gtm-planner.local.md`.
For steps 2 to 5, which require the earlier steps confirmed, the right
behavior from a cold start is to stop and ask — so a cold case for those steps
tests the gate, not the step's output.

`demand-plan-gates-without-foundation` is that cold case. Its twin,
`demand-engines-not-tactics`, pastes a confirmed snapshot and positioning into
the prompt, the way a user who already did the work would, and only then
grades the engines. It also answers the source question up front, because the
demand step otherwise stops to ask which data sources to use.

## Tools

Runs grant only what a case lists in `allowed_tools`. Most cases list
`[Read, Glob, Grep, Skill]`: `Read` is what lets a skill open its own
`references/` files.

- **No web tools in any case.** That is what makes `benchmarks-not-invented` a
  real test: with no way to look a figure up, a model either says so or
  fabricates.
- **`Agent` is granted only in `demand-engines-not-tactics`**, which exercises
  the plugin's real architecture: the demand step dispatching the
  benchmark-researcher agent.
- **`Agent` is withheld from `benchmarks-not-invented` on purpose.** In the
  2026-09-30 run that case's replies described what the benchmark researcher
  found, although the case did not grant `Agent`. Either the tool was
  available anyway, or the reply narrated a dispatch that never happened. The
  `agent-dispatched` indicator and a `--keep-temp` trace settle which.
- **`AskUserQuestion` is withheld everywhere**, so the questions a step raises
  land in the final message where the graders can read them.

## Reading the result

Two kinds of grader are reported but **not scored**:

- `skill-fired` (`tool_used` on `Skill`) — Claude Code excludes these
  automatically, since they can never pass without the plugin.
- `agent-dispatched` (`tool_used` on `Agent`) — marked `arm: with-only` for the
  same reason.

Treat both as indicators, and don't read either as "did the plugin act".
`skill-fired` only sees the `Skill` tool: a reply shaped by an agent
description, or by an agent dispatch, can show the plugin's hand while
`skill-fired` reads 0.

If a case's indicator passes but `Δ` is negative, read the replies before
blaming the plugin. In the 2026-09-30 run the demand case scored `Δ` −0.22
because all three replies with the plugin correctly refused to plan channels
without a snapshot and positioning — and the rubric of the time demanded
engines. The plugin was right; the case was wrong.

## MCP servers

The plugin's four connectors need OAuth, and eval runs never stop to
authenticate. Under the default `--mocks record` their real servers are not
started, which is correct here: every case is written for the zero-connector
baseline. Testing a connected path means adding mocks under `evals/mocks/`.
