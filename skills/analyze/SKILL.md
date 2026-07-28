---
name: analyze
description: >-
  Use when a feature's note.md is written and ready to become a list of open
  product/architecture questions, before a ticket or plan can be written.
  Explores the codebase against a fixed checklist (hidden async/webhook
  mechanisms, billing/credit files, naming traps, third-party dependencies)
  and fills or updates questions.md accordingly.
---

# Analyzing Feature Notes

## Overview

Second step of the note.md, questions.md, ticket.md/plan.md flow (see
**spec-workflow:start** for stage 1, **spec-workflow:ticket-plan** for
stage 3). Turns a raw note into a grounded list of open decisions the user
needs to make before a ticket can be written. The user decides, this skill
only surfaces and grounds the questions.

## When to Use

- `note.md` exists in a feature's specs folder and has real content
- The user wants to know "what's missing before I can write a ticket"
- `questions.md` already exists but new raw notes were added, re-run to pick
  up new gaps only

## Process

1. Detect the language `note.md` is written in, and match it against the
   subfolders of `templates/` in this skill's own directory (each subfolder
   name is a supported language code, e.g. `fr`, `en`). If there's no
   matching subfolder, default to `en`. `questions.md` must be written in
   that same language, using `templates/<lang>/questions.template.md` as
   the format, don't switch language based on the current conversation.
2. Read `note.md`. Read every file it references, not just skim titles.
3. Look for a "similar precedent" pointer; if present, read that feature's
   `ticket.md`/`plan.md` as a structural reference for what kinds of
   decisions tend to matter (scopes, idempotence, error handling...).
4. Walk the checklist below explicitly, for each row, decide if it applies
   here, and if unclear, that's a candidate question. A baseline test run
   without this checklist found gaps in exactly these categories, so treat
   it as required, not optional.
5. For each real gap: write one question following the "## N." block in
   `templates/<lang>/questions.template.md`, grounded in `file:line`. If
   there's no existing code to cite (greenfield feature, or a codebase-wide
   convention that doesn't exist yet), ground it instead in the source doc
   and section that raised the question (e.g. `PRODUCT.md, section COMMENT`
   or `note.md, section Architecture`) — `file:line` is the default grounding
   when code exists, not a hard requirement when it doesn't. One question =
   one decision, not a bundle. Tag it factual (a lookup or a single grep
   settles it) or a tradeoff (it needs actual judgment: a product call, a
   real alternative, something a lookup can't resolve). This distinction is
   for the user: not every entry in `questions.md` deserves the same level
   of attention, and treating a real tradeoff as if it were a quick lookup
   is how decisions get rubber-stamped instead of made.
6. If `questions.md` already exists, append only new questions (don't touch
   existing entries, don't renumber). Do this directly, no need to ask
   permission first, that's what the file is for.
7. If `questions.md` doesn't exist yet, create it from
   `templates/<lang>/questions.template.md`.

## Checklist (walk every row)

For a greenfield feature (no existing codebase/conventions to check
against), a row that asks "what's the existing X" doesn't disappear: it
becomes the question itself ("what convention should we establish for X"),
tagged as a tradeoff. Don't skip the row just because there's nothing to
grep yet.

| Category | Ask yourself |
|---|---|
| Execution model | Is there a hidden job/poll/webhook not mentioned in the "obvious" files? (grep the feature's api folder for "webhook"; greenfield: does the planned flow imply one that isn't spelled out yet?) |
| Money | Does any file touch credits/billing/débit? |
| Entry point | What existing route convention is the closest match to mirror? (greenfield: no convention exists yet — this becomes "what convention do we establish") |
| Product split | Does a hidden flag/scope actually hide two distinct features (separate routes vs one param)? |
| Sync/async flow | How many real steps happen on the third-party service side, where can the client inspect progress? |
| Client dependencies | Can the client actually obtain everything required (IDs, voices, credentials) without a UI? |
| Idempotence | What happens on a duplicate call/retry against the same resource? |
| Intermediate statuses | Does the existing generic job model cover every real status this flow can be in? (greenfield: does the planned data model even have a status/state concept yet?) |
| Minimal DTO | Which internal fields must never leak to the client? |
| Third-party capacity | Does an external service need a concurrency cap? |
| Validation | Do we replicate the third-party service's constraints in our own schema, or passthrough? |
| Error sanitization | Do we reuse the existing "never leak raw upstream detail" helper? (greenfield: is there even a plan for one, or does every new caller reinvent error handling?) |
| Vocabulary | Do internal names diverge from public-facing names (a naming trap)? |

## Common Mistakes

- Skipping a checklist row because the note didn't mention it: the note is
  written by someone who may not know to mention it either, that's exactly
  why the checklist exists independent of the note's content.
- Answering the questions yourself instead of leaving them open: this skill
  surfaces decisions, it doesn't make them.
- Producing free-form prose instead of the numbered Context/Question/Status
  format from the template: a baseline test without this skill did exactly
  that, and it's harder to track resolution over multiple rounds.
- Not comparing against the closest existing precedent when one exists:
  re-derives decisions from scratch that were already made once.
- Mixing languages between `note.md` and `questions.md`, or within
  `questions.md` itself: pick the language from `note.md` once and stay in
  it for the whole file.
- Tagging every question a tradeoff (or every question factual) to save
  time: the tag is only useful if it's an honest read of what the question
  actually demands.
