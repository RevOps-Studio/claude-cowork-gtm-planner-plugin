---
name: intake
description: >
  This skill should be used when the user wants to start a go-to-market plan,
  says "start my GTM plan", "build a business snapshot", "run intake",
  "/gtm-planner:intake", or describes their company and asks where to begin.
  First step of the Go2Rev methodology — produces the Business Snapshot that
  every later step builds on.
metadata:
  version: "0.1.0"
  author: "RevOps Studio"
---

# Intake — Business Snapshot

Produce the Business Snapshot: a structured, honest picture of the user's
business as it is today. It is the first link in the Go2Rev chain —
*a GTM plan is a chain of decisions: category → promise → engines → channels →
commitments. Each decision builds on the one before.* A shallow snapshot
produces a shallow plan.

Respond in the language the user is writing in, whatever it is.

## Operating principles

- **Declared vs. inferred.** Distinguish what the user stated from what was
  inferred from their materials. Mark inferences as open questions of type
  `assumption` with a recommendation.
- **Never fill gaps with plausible fiction.** If a section has no real data,
  raise an open question of type `missing-data`: what is missing, why it
  matters, how to get it. Then continue with what exists.
- **Every open question carries a confidence grade.** State how confident
  the current working answer is (high / medium / low) and what evidence it
  rests on. This grade travels with the question through every later step
  and into the final plan's ledger.
- **Source hierarchy.** When sources conflict (user statement vs. website vs.
  CRM data), prefer: (1) what the user tells you now, (2) live data from
  connected tools, (3) public materials. Surface every conflict as an open
  question of type `conflict` — show both versions and recommend which to trust.
- **Operator language, not agency language.** Revenue, pipeline, conversion,
  sales cycle, average deal size. Never "360 strategy", "holistic ecosystem",
  "brand activation journey".
- **Right-sized output.** If a section has three important points, write
  three points. Do not pad.

## Process

1. **Check journey state.** If `.claude/gtm-planner.local.md` exists, read it.
   If intake is already confirmed, tell the user and offer to update it
   instead of starting over.
2. **Gather materials.** Ask for the company website URL and any decks, docs
   or notes they can share. If Google Drive is available, offer to look there.
   If HubSpot is connected, use it for real funnel data. Do not block on any
   of this — work with what the user gives you.
3. **Dispatch the materials-analyst agent** to analyze the website, documents
   and CRM data. It returns findings with provenance.
4. **Run the guided interview.** Cover the snapshot sections below
   conversationally — a few questions at a time, adapting to what the
   materials already answered. Never re-ask what the analysis already
   established; instead confirm it ("Your site suggests X — accurate?").
5. **Draft the Business Snapshot** using the template in
   `references/snapshot-template.md`. Follow it exactly.
6. **Coherence check before presenting.** Is the ICP consistent with the sales
   cycle described? Does the average deal size make sense for the segments?
   Are the constraints consistent with the goals? Flag inconsistencies as
   `conflict` open questions.
7. **Present the snapshot + open questions.** End with a short "Snapshot
   confidence" note: what is solid, what is thin, and the single most valuable
   thing the user could add. Ask the user to confirm or correct.
8. **On confirmation**, update the journey state file (step 1 → confirmed,
   log resolved/pending open questions) and point to the next step:
   `/gtm-planner:market-map`.

## Snapshot sections

Business context · Current offer and value proposition · Target segments and
ICP · Current funnel and sales cycle · Stack and tools · Revenue team ·
Stated goals · Known constraints · Gaps and assumptions. Full structure in
`references/snapshot-template.md`.

## Connected tools

- **HubSpot connected:** pull real funnel metrics (lead sources, conversion
  rates, cycle length, deal sizes) instead of relying on declared numbers.
- **Not connected:** use declared numbers and note once: connecting HubSpot
  would let the plan calibrate against the actual funnel. Say it in one line
  and move on — never nag.

## What NOT to do

- Do not assume information that is not in the materials or the conversation.
- Do not proceed to market-map without explicit user confirmation of the snapshot.
- Do not reuse another company's snapshot as a reference, even same-sector.
