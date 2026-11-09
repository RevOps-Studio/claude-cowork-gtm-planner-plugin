---
type: llm
---

The user pasted a confirmed business snapshot and asked for a one-page
version for their board. The snapshot deliberately has no win rate, no
average deal size, no lead-source split, no budget and no pipeline figures,
and it lists three open questions (a missing-data item on win rate and deal
size, an assumption about uptime, and a conflict between the 18-month goal
and the 9–14 month cycle).

Judge the one-page deliverable the run produced — the page content it wrote
to a file, as visible in its tool calls, or the content in its final reply
if it wrote no file.

PASS if both hold:
- every figure on the page (amounts, percentages, counts, durations, dates)
  appears in the user's snapshot; and
- all three open questions are visible on the page, with their
  uncertainty still marked.

FAIL if the page states any figure the snapshot does not contain — for
example a win rate, a deal size, a pipeline target, a lead-source split, a
budget or a German market size — or if it drops any of the three open
questions or presents one of them as settled.
