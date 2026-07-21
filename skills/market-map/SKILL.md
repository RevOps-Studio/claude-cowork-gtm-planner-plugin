---
name: market-map
description: >
  This skill should be used when the user asks to "map my market", "analyze my
  competitors", "who do we really compete with", "find positioning gaps",
  "/gtm-planner:market-map", or needs competitive and category intelligence
  for a go-to-market plan. Second step of the Go2Rev methodology — reads the
  market so positioning can be decided against it.
metadata:
  version: "0.1.0"
  author: "RevOps Studio"
---

# Market Map

Produce the Market Map: a strategic reading of the market the company operates
in — not a list of competitors. Who competes, how each one is positioned, what
narrative categories exist, and where there is defensible open space. A market
map that does not inform positioning decisions is filler.

Respond in the language the user is writing in.

## Operating principles

- **Three layers of competition.** (1) Direct competitors — same offer, same
  ICP. (2) Category competitors — different offer, same job to be done.
  (3) Non-competitive alternatives — what the buyer would do if this category
  did not exist: hire internally, do it by hand, do nothing. "Do nothing" is
  usually the biggest competitor in B2B. Details in
  `references/three-layer-model.md`.
- **Positioning, not features.** Read how each competitor positions itself:
  what it promises, to whom, in what tone, which narrative category it claims.
  Never produce a feature comparison table.
- **Gaps vs. holes.** A gap is a defensible, desirable position nobody holds.
  Some holes are empty for a reason. Apply the test in
  `references/gap-vs-hole.md` and label accordingly: `[GAP]` vs.
  `[GAP HYPOTHESIS]`.
- **Depth over coverage.** Analyze the 3–5 competitors that matter most for
  this company's decisions — not the biggest names in the market. Never more
  than 5 in depth.
- **Verifiable sources.** Every claim about a competitor traces to a public
  source (website, LinkedIn, press, case studies) — cite it. If it comes from
  the user, mark it `[source: user]`. If inferred, raise an `assumption` open
  question.

## Process

1. **Load context.** Read the journey state and the confirmed Business
   Snapshot. If no snapshot exists, say the map will be weaker without it,
   offer to run intake first, and proceed only if the user prefers —
   marking the limitation in the output.
2. **Frame the search.** From the snapshot: who does the user name as
   competitors? What job does the offer do? What would buyers do without it?
3. **Dispatch the market-researcher agent** with the company context and
   competitor candidates. It researches autonomously and returns findings
   with sources. If Similarweb/Ahrefs are connected it enriches with traffic
   and organic footprint data.
4. **Build the three-layer map** and select the 3–5 priority competitors —
   most relevant to this company's decisions, not largest.
5. **Analyze each priority competitor:** narrative category claimed, core
   promise, apparent ICP, differentiation mechanism, visible strengths,
   observable vulnerabilities, sources.
6. **Synthesize the positioning map:** the 2–3 axes on which this market
   actually differentiates, who holds which position, where the user's
   company sits today (honestly — even if they believe otherwise), and the
   open spaces labeled `[GAP]` or `[GAP HYPOTHESIS]`.
7. **Draft 2–3 positioning hypotheses** for the next step — directions with
   an argument, not decisions.
8. **Coherence check:** are the priority competitors the ones the snapshot
   pointed to? Is every gap tested against `gap-vs-hole.md`? Any competitor
   ignored by default that should be here?
9. **Present the Market Map + open questions.** On confirmation, update the
   journey state and point to `/gtm-planner:positioning`.

## Output structure

Executive summary (max 250 words) → Market definition (narrative categories
in play, job to be done, non-competitive alternatives) → Three-layer map →
Priority competitor analysis (3–5) → Positioning map (axes, occupied
positions, the company today, gaps) → Category dynamics (trends, emerging
language, saturation signals) → Positioning hypotheses (2–3) → Open questions.

## What NOT to do

- No feature comparison tables.
- No more than 5 competitors in depth, even if more exist.
- No unsourced claims about competitors.
- No soft judgments ("they're good at X", "they're modern") — state exactly
  what they do and what it implies.
- Do not proceed to positioning without user confirmation.
