# Source Readiness Check

Run this check BEFORE dispatching research agents in any step that depends
on external data (market-map, demand-plan). Output quality tracks source
quality — make that visible to the user up front, not after the fact.

## 1. Inventory what is actually available

Check, in order:
- **Connected tools:** which of Similarweb, Ahrefs, HubSpot are connected
  AND authorized right now? A connector that is installed but not
  authenticated counts as unavailable — test with a lightweight call if
  unsure, never assume.
- **User materials:** websites, decks, internal data the user has shared.
- **Web research:** always available (baseline).

Note on access: Similarweb and Ahrefs MCP connectors require an account
with API access on those platforms (paid plans) — a free account is not
enough. Do not press the user to connect them; state what each would add
and move on.

## 2. Tell the user what tier they are working at

Present a one-screen summary before researching:

| Data need | Best source | Available now | Fallback in use |
|---|---|---|---|
| Competitor traffic scale & channel mix | Similarweb | yes/no | Deep web research (public data, estimates flagged) |
| Competitor organic footprint, keywords | Ahrefs | yes/no | Web research on visible content + SERPs |
| Own funnel reality | HubSpot / CRM export | yes/no | User-declared numbers |
| Category dynamics, positioning, pricing | Web research | always | — |

## 3. Offer the choice explicitly

When a preferred source is unavailable, ask the user to pick — do not
decide silently:

- **(a) Proceed with fallback** — web-based deep research; estimates are
  labeled as such and the limitation travels to the open questions ledger.
- **(b) Connect / authorize the tool now** — then re-run just the affected
  research, not the whole step.
- **(c) Provide the data manually** — the user may have platform exports,
  a recent audit, or an analyst report on hand.

Any combination is valid per data need. Record the choice in the journey
state so later steps (and re-runs) know what they are standing on.

## 4. Stamp the output

The step's output opens with a one-line "Sources used" note (tools, web,
user data) and every estimate carries its source or an `assumption` /
`needs-benchmark` flag. No silent downgrades.
