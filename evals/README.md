# Eval suite

Six cases that test whether the planner's **method** survives contact with a
real request — not whether its research is good.

Each case takes a claim the README makes and turns it into a prompt where a
model without the plugin predictably does the opposite. `claude plugin eval`
runs every case twice: once with the plugin loaded and once with no plugin at
all. The number that matters is `Δ`, the difference. A case that scores 1.0 in
both arms proves nothing — Claude was already doing it.

## Run it

```bash
claude plugin eval . --trust-plugin
```

While iterating on a rubric, halve the cost by skipping the baseline arm:

```bash
claude plugin eval . --trust-plugin --ablation none --runs 1
```

One case at a time:

```bash
claude plugin eval . --trust-plugin --case benchmarks-not-invented
```

By tag: `--tag no-invented-data`, `--tag method`, `--tag gates`.

Six cases × 3 runs × 2 arms is 36 agent runs, so a full pass is not free. Use
`--max-cost-usd` to put a ceiling on it.

## The cases

| Case | The claim it tests | What a no-plugin model tends to do instead |
|---|---|---|
| `connector-honesty` | No connector is required, and Similarweb and Ahrefs need a paid API plan | Doesn't know the product; gives generic CRM advice |
| `intake-open-questions` | Open questions, not invented data | Fills the gaps with plausible funnel numbers |
| `gate-blocks-premature-positioning` | The category gate blocks on a missing ICP | Delivers a confident positioning statement |
| `positioning-pillar-test` | Two out of three gets cut | Polishes all four pillars into messaging |
| `demand-engines-not-tactics` | Engines, not tactics | Returns a channel list with budget splits |
| `benchmarks-not-invented` | Every number is sourced or labeled an estimate | States CPL ranges as established benchmarks |

## Why no web tools

Eval runs grant only what a case lists in `allowed_tools`, and every case here
lists `[Read, Glob, Grep, Skill]`. `Read` is what lets a skill open its own
`references/` files; nothing else is granted.

That is deliberate. Leaving out `WebSearch` and `WebFetch` is what makes
`benchmarks-not-invented` a real test: with no way to look a figure up, a model
either says so or fabricates. To exercise the research agents instead, grant
them explicitly — but expect the no-invented-data cases to get easier, not
harder:

```bash
claude plugin eval . --trust-plugin --allow-tools WebSearch WebFetch
```

`AskUserQuestion` is also deliberately ungranted, so the questions a step
raises land in the final message where the graders can read them.

## Why every case runs from an empty directory

Each run starts in a fresh workspace with no `.claude/gtm-planner.local.md`, so
every case exercises a cold start. That is why no case tests resuming a
journey: that would need a `case.yaml` with a `context.history_file`, and it is
the obvious next case to add.

## Reading the result

`tool_used` graders on the `Skill` tool are reported but **not scored**. They
can never pass without the plugin, so counting them would push the baseline arm
toward zero and inflate `Δ`. Treat them as an indicator that the right skill
fired, and let the content graders carry the score.

If a case's `skill-fired` indicator passes but `Δ` is negative, suspect the
judge before the plugin — re-run that case with `--judge-model sonnet`.

## MCP servers

The plugin's four connectors need OAuth, and eval runs never stop to
authenticate. Under the default `--mocks record` their real servers are not
started, which is correct here: every case is written for the zero-connector
baseline. Testing a connected path means adding mocks under `evals/mocks/`.
