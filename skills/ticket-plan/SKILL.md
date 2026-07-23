---
name: ticket-plan
description: >-
  Use when a feature's questions.md has every open decision marked TRANCHÉ
  and it's time to write the final ticket.md and plan.md — turns resolved
  product/architecture decisions into an implementation-ready ticket and
  execution plan, following the project's existing ticket structure.
---

# Writing Feature Ticket + Plan

## Overview

Third and final step of the note.md → questions.md → ticket.md/plan.md flow
(see **spec-workflow:start** and **spec-workflow:analyze** for stages
1-2). Turns resolved decisions into the two documents that drive
implementation.

## When to Use

Only when every entry in `questions.md` reads `**Statut** : TRANCHÉ`.

## Process

1. Read `questions.md`. **If any entry is still `OUVERT`, stop and list
   exactly which ones** — do not guess a product decision on the user's
   behalf. This is the one hard gate in the whole flow.
2. Read `note.md` for the persona/scope framing (Que faire / Pour qui /
   Hors scope) — the ticket's Objectif section draws from this, not from
   questions.md alone.
3. If a "Précédent similaire" was named, read its `ticket.md`/`plan.md` in
   full — mirror its section structure and level of detail exactly, don't
   just skim it for vibes.
4. Explore the current codebase for every `fichier:ligne` cited in
   `questions.md` — they were written during the Q&A session and may be
   stale. Refresh before citing them in the ticket.
5. Write `ticket.md` from `templates/ticket.template.md` and `plan.md` from
   `templates/plan.template.md` (same directory as this skill). Every
   "Décision produit tranchée" in the ticket must trace back to a specific
   TRANCHÉ entry in `questions.md` — don't introduce a decision that isn't
   there.
6. Do not touch any implementation code — this skill only writes the two
   markdown files.

## Common Mistakes

- Resolving a leftover OUVERT question by picking "the reasonable answer" —
  even a good guess removes the user's decision. Stop and ask instead.
- Copying a precedent's decisions wholesale instead of checking whether
  this feature's own `questions.md` actually made the same call — the
  precedent is a structural reference, not a source of truth for this
  feature's decisions.
- Writing steps in a different order than the dependency between them
  implies (e.g. a migration step must come before the endpoint that needs
  the new column) — verify the plan is actually executable top-to-bottom.
- Leaving template placeholders (`<...>`) unfilled in the output.
