---
name: ticket-plan
description: >-
  Use when a feature's questions.md has every open decision marked TRANCHÉ
  and it's time to write the final ticket.md and plan.md: turns resolved
  product/architecture decisions into an implementation-ready ticket and
  execution plan, following the project's existing ticket structure.
---

# Writing Feature Ticket + Plan

## Overview

Third and final step of the note.md, questions.md, ticket.md/plan.md flow
(see **spec-workflow:start** and **spec-workflow:analyze** for stages
1-2). Turns resolved decisions into the two documents that drive
implementation.

## When to Use

Only when every entry in `questions.md` reads `**Statut** : TRANCHÉ` with a
non-empty `**Pourquoi**`.

## Process

1. Read `questions.md`. **If any entry is still `OUVERT`, or `TRANCHÉ` with
   an empty `Pourquoi`, stop and list exactly which ones.** Do not guess a
   product decision on the user's behalf, and do not treat an unexplained
   `TRANCHÉ` as resolved: a decision without a stated reason wasn't actually
   reasoned through. This is the one hard gate in the whole flow.
2. Ask the user to restate, from memory and without rereading `questions.md`,
   2-3 of the `TRANCHÉ` decisions (pick the ones tagged **arbitrage** if any
   exist, they're the ones worth checking). If what they recall doesn't
   match what's actually written, flag the mismatch and ask them to
   re-confirm that entry before moving on. This isn't a formality: it's the
   difference between a decision that was actually made and one that got
   rubber-stamped on the way past.
3. Read `note.md` for the persona/scope framing (Que faire / Pour qui /
   Hors scope): the ticket's Objectif section draws from this, not from
   questions.md alone.
4. If a "Précédent similaire" was named, read its `ticket.md`/`plan.md` in
   full: mirror its section structure and level of detail exactly, don't
   just skim it for vibes.
5. Explore the current codebase for every `fichier:ligne` cited in
   `questions.md`: they were written during the Q&A session and may be
   stale. Refresh before citing them in the ticket.
6. Write `ticket.md` from `templates/ticket.template.md` and `plan.md` from
   `templates/plan.template.md` (same directory as this skill). Every
   "Décision produit tranchée" in the ticket must trace back to a specific
   TRANCHÉ entry in `questions.md`: don't introduce a decision that isn't
   there.
7. Do not touch any implementation code, this skill only writes the two
   markdown files.

## Common Mistakes

- Resolving a leftover OUVERT question by picking "the reasonable answer":
  even a good guess removes the user's decision. Stop and ask instead.
- Treating an empty `Pourquoi` as good enough because the `Statut` says
  `TRANCHÉ`: the field exists precisely to catch decisions nobody actually
  thought through.
- Skipping the memory-recall step because "the user clearly knows their own
  decisions": that assumption is exactly what the step is there to check,
  not something to take for granted.
- Copying a precedent's decisions wholesale instead of checking whether
  this feature's own `questions.md` actually made the same call: the
  precedent is a structural reference, not a source of truth for this
  feature's decisions.
- Writing steps in a different order than the dependency between them
  implies (e.g. a migration step must come before the endpoint that needs
  the new column): verify the plan is actually executable top-to-bottom.
- Leaving template placeholders (`<...>`) unfilled in the output.
