---
name: start
description: >-
  Use when kicking off a new feature that needs a written spec before
  implementation — scaffolds a dedicated specs folder with a guided
  note-taking template (note.md). Use even for features that feel small;
  the template's checklist catches hidden async/webhook mechanisms and
  money-touching files that are easy to skip when writing notes quickly.
---

# Starting a Feature Spec

## Overview

First step of a 4-stage flow: `note.md` (this skill) → `questions.md`
(**spec-workflow:analyze**) → `ticket.md` + `plan.md`
(**spec-workflow:ticket-plan**). This skill only scaffolds the folder and
the note-taking template — it does not analyze anything yet.

## When to Use

- Starting to think about a new feature, before any code or ticket exists
- You already have some notes in your head about relevant files/functions
  and want a place to capture them properly

Don't use for: trivial one-file fixes, or features where the note is
already written (use **spec-workflow:analyze** directly instead).

## Steps

1. Ask the user for the feature slug (kebab-case) and the specs root if not
   obvious.
2. Create `<root>/<slug>/`.
3. Copy `templates/note.template.md` to `<root>/<slug>/note.md`.
4. Tell the user the file is ready to fill in — do not fill it in yourself,
   this is the user's own research to do.

## Common Mistakes

- Pre-filling the note with guesses about the feature — the whole point is
  the user's own research (cf. the workflow this skill is part of: the user
  does the investigation, the assistant writes/advises from it).
- Creating `questions.md`/`ticket.md`/`plan.md` at this stage — they don't
  exist until there's real content to analyze.
