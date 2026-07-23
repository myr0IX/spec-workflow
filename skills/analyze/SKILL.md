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

Second step of the note.md → questions.md → ticket.md/plan.md flow (see
**spec-workflow:start** for stage 1, **spec-workflow:ticket-plan** for
stage 3). Turns a raw note into a grounded list of open decisions the user
needs to make before a ticket can be written — the user decides, this skill
only surfaces and grounds the questions.

## When to Use

- `note.md` exists in a feature's specs folder and has real content
- The user wants to know "what's missing before I can write a ticket"
- `questions.md` already exists but new raw notes were added — re-run to pick
  up new gaps only

## Process

1. Read `note.md`. Read every file it references, not just skim titles.
2. Look for a "Précédent similaire" pointer; if present, read that
   feature's `ticket.md`/`plan.md` as a structural reference for what kinds
   of decisions tend to matter (scopes, idempotence, error handling...).
3. Walk the checklist below explicitly — for each row, decide if it applies
   here, and if unclear, that's a candidate question. A baseline test run
   without this checklist found gaps in exactly these categories, so treat
   it as required, not optional.
4. For each real gap: write one question in the format below, grounded in
   `fichier:ligne`. One question = one decision, not a bundle.
5. If `questions.md` already exists, append only new questions (don't touch
   existing entries, don't renumber). Do this directly, no need to ask
   permission first — that's what the file is for.
6. If `questions.md` doesn't exist yet, create it with the header below.

## Checklist (walk every row)

| Category | Ask yourself |
|---|---|
| Execution model | Is there a hidden job/poll/webhook not mentioned in the "obvious" files? (grep the feature's api folder for "webhook") |
| Money | Does any file touch credits/billing/débit? |
| Entry point | What existing route convention is the closest match to mirror? |
| Product split | Does a hidden flag/scope actually hide two distinct features (separate routes vs one param)? |
| Sync/async flow | How many real steps happen on the third-party service side, where can the client inspect progress? |
| Client dependencies | Can the client actually obtain everything required (IDs, voices, credentials) without a UI? |
| Idempotence | What happens on a duplicate call/retry against the same resource? |
| Intermediate statuses | Does the existing generic job model cover every real status this flow can be in? |
| Minimal DTO | Which internal fields must never leak to the client? |
| Third-party capacity | Does an external service need a concurrency cap? |
| Validation | Do we replicate the third-party service's constraints in our own schema, or passthrough? |
| Error sanitization | Do we reuse the existing "never leak raw upstream detail" helper? |
| Vocabulary | Do internal names diverge from public-facing names (a naming trap)? |

## Output Format

```markdown
# Questions / décisions en attente — <feature>

Statut : `OUVERT` / `TRANCHÉ`. Remplir "Décision" + laisser "Pourquoi" quand tranché.

---

## N. <titre court>

**Contexte** : <faits observés, avec `fichier:ligne`>

**Question** : <une seule question précise>

**Statut** : OUVERT
**Décision** :
**Pourquoi** :

---
```

End with a "Hors ticket pour l'instant" section for anything explicitly
deferred rather than resolved.

## Common Mistakes

- Skipping a checklist row because the note didn't mention it — the note is
  written by someone who may not know to mention it either; that's exactly
  why the checklist exists independent of the note's content.
- Answering the questions yourself instead of leaving them OUVERT — this
  skill surfaces decisions, it doesn't make them.
- Producing free-form prose instead of the numbered Context/Question/Statut
  format — a baseline test without this skill did exactly that, and it's
  harder to track resolution over multiple rounds.
- Not comparing against the closest existing precedent when one exists —
  re-derives decisions from scratch that were already made once.
