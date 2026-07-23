---
name: ticket-plan
description: >-
  Use when a feature's questions.md has every open decision resolved
  (TRANCHÉ/RESOLVED) and it's time to write the final ticket.md and plan.md:
  turns resolved product/architecture decisions into an implementation-ready
  ticket and execution plan, following the project's existing ticket
  structure.
---

# Writing Feature Ticket + Plan

## Overview

Third and final step of the note.md, questions.md, ticket.md/plan.md flow
(see **spec-workflow:start** and **spec-workflow:analyze** for stages
1-2). Turns resolved decisions into the two documents that drive
implementation.

## When to Use

Only when every entry in `questions.md` reads its resolved status
(`TRANCHÉ` in the French variant, `RESOLVED` in the English one) with a
non-empty reason field (`Pourquoi` / `Why`).

## Process

1. Determine the language: match whatever `note.md` and `questions.md` are
   already written in against the subfolders of `templates/` in this
   skill's own directory (each subfolder name is a supported language code,
   e.g. `fr`, `en`). If there's no matching subfolder, default to `en`. Use
   that same language's template folder in step 7, don't re-detect from the
   current conversation, the whole flow for one feature should stay in one
   language.
2. Read `questions.md`. **If any entry is still open, or resolved with an
   empty reason field, stop and list exactly which ones.** Do not guess a
   product decision on the user's behalf, and do not treat an unexplained
   resolution as settled: a decision without a stated reason wasn't actually
   reasoned through. This is the one hard gate in the whole flow.
3. Ask the user to restate, from memory and without rereading `questions.md`,
   2-3 of the resolved decisions (pick the ones tagged as a tradeoff/judgment
   call if any exist, they're the ones worth checking). If what they recall
   doesn't match what's actually written, flag the mismatch and ask them to
   re-confirm that entry before moving on. This isn't a formality: it's the
   difference between a decision that was actually made and one that got
   rubber-stamped on the way past.
4. Read `note.md` for the persona/scope framing (what to do, for whom, out
   of scope): the ticket's Objective section draws from this, not from
   questions.md alone.
5. If a similar precedent was named, read its `ticket.md`/`plan.md` in
   full: mirror its section structure and level of detail exactly, don't
   just skim it for vibes.
6. Explore the current codebase for every `file:line` cited in
   `questions.md`: they were written during the Q&A session and may be
   stale. Refresh before citing them in the ticket.
7. Write `ticket.md` from `templates/<lang>/ticket.template.md` and
   `plan.md` from `templates/<lang>/plan.template.md` (same directory as
   this skill, `<lang>` from step 1). Every resolved decision listed in the
   ticket must trace back to a specific resolved entry in `questions.md`:
   don't introduce a decision that isn't there.
8. Do not touch any implementation code, this skill only writes the two
   markdown files.

## Common Mistakes

- Resolving a leftover open question by picking "the reasonable answer":
  even a good guess removes the user's decision. Stop and ask instead.
- Treating an empty reason field as good enough because the status says
  resolved: the field exists precisely to catch decisions nobody actually
  thought through.
- Skipping the memory-recall step because "the user clearly knows their own
  decisions": that assumption is exactly what the step is there to check,
  not something to take for granted.
- Copying a precedent's decisions wholesale instead of checking whether
  this feature's own `questions.md` actually made the same call: the
  precedent is a structural reference, not a source of truth for this
  feature's decisions.
- Mixing template languages (e.g. writing `ticket.md` from the English
  template when `note.md` was written in French): pick the language once,
  from `note.md`, and use it for every output file.
- Writing steps in a different order than the dependency between them
  implies (e.g. a migration step must come before the endpoint that needs
  the new column): verify the plan is actually executable top-to-bottom.
- Leaving template placeholders (`<...>`) unfilled in the output.
