---
name: positioning
description: >
  This skill should be used when the user asks to "define my positioning",
  "choose a category", "craft our core promise", "build our messaging",
  "/gtm-planner:positioning", or needs the strategic positioning and
  messaging architecture of a go-to-market plan. Third step and heart of the
  Go2Rev methodology — decides category, promise, pillars and messages.
metadata:
  version: "0.1.0"
  author: "RevOps Studio"
---

# Positioning Architecture

Build the positioning and messaging architecture: which category the company
claims, what it promises differentially, which pillars support that promise,
and how it translates into messages per segment and funnel stage.

This is not copy — it is the infrastructure copy is later built on. Without
it, every channel ends up telling a different story.

Respond in the language the user is writing in.

## Operating principles

- **Category before product.** An identical product positioned in two
  different categories sells to different buyers, competes against different
  alternatives, and commands a different price. Category choice is strategic,
  not descriptive. Method in `references/category-decision.md`.
- **Promise, not description.** The core promise states what the customer
  gets, not what the company does. "We help sales teams close faster" is
  description. "Closing stops depending on your head of sales" is promise.
- **The pillar test.** Every message pillar must pass three checks:
  (1) relevant to the ICP, (2) differentiated from the competitors in the
  Market Map, (3) defensible with real, current capabilities. Two out of
  three is not a pillar — it is noise. Full test in
  `references/pillar-test.md`. 3–4 pillars; fewer leaves the promise exposed,
  more dilutes it.
- **Segments are translations, not variations.** Messages per segment
  translate the same promise into each segment's codes. If a segment needs a
  radically different message, it is probably a different market — say so.
- **Anti-messages are part of the architecture.** What the company will NOT
  say is as protective as what it will. Method in
  `references/anti-messages.md`.
- **Operator language, not agency language.** Ban "transformation journey",
  "holistic ecosystem", "360 experience", "integral solutions" and their
  relatives. Messages must sound like an operator, not an agency.

## Process

1. **Load context.** Journey state + confirmed Business Snapshot + Market Map.
   Both inputs matter: positioning is decided against the market, grounded in
   real capabilities. If either is missing, warn, offer to run it, and only
   proceed with explicit acceptance of the limitation.
2. **Evaluate 2–3 candidate categories** (start from the Market Map's
   positioning hypotheses). Score each against: size of the space, saturation,
   fit with actual capabilities, appeal to the ICP. Present the comparison and
   the recommendation — the user decides. This is the single most consequential
   decision in the plan; make that explicit.
3. **Craft the core promise.** One sentence, ideally under 15 words, plus one
   fallback phrasing. Verify: outcome (not activity)? Differential against the
   Map? Credible given the snapshot?
4. **Build 3–4 pillars.** Each answers "why should we believe this promise?"
   For each: what it claims, why it is credible, why it is differential, and
   available evidence — or an `unverified-claim` open question.
5. **Translate per segment** (primary + up to 2 secondary): what keeps this
   decision-maker up at night, the promise in their language, which pillars
   weigh most, 3–5 vocabulary terms.
6. **Messages per funnel stage:** awareness (present the category), 
   consideration (push toward the conversation), decision (kill objections,
   create urgency). Dominant message + 2–3 variants each. Awareness and
   decision messages must not resemble each other.
7. **Anti-messages bank:** what we do not say, competitor lines we do not
   imitate, claims we cannot defend yet.
8. **"What this changes tomorrow":** brief — homepage headline, first two
   minutes of the sales pitch, content themes that fit and clash.
9. **Coherence check:** category consistent with the Map? Promise consistent
   with real customer evidence? Every pillar passes the three-part test?
10. **Present + open questions.** On confirmation, update journey state and
    point to `/gtm-planner:demand-plan`.

## Output structure

Executive summary → Category decision (candidates evaluated, choice,
argument, implications) → Core promise (canonical + fallback + why believable)
→ Pillars (3–4, each with the three-part test shown) → Segment translations →
Messages per funnel stage → Anti-messages bank → What this changes tomorrow →
Open questions.

## What NOT to do

- No promise that describes activity instead of customer outcome.
- Never more than 4 pillars.
- No awareness messages that look like decision messages.
- Do not ignore the Market Map — positioning is defined against it.
- Do not proceed to demand-plan without user confirmation.
