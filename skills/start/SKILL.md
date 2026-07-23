---
name: start
description: >-
  Use when kicking off a new feature that needs a written spec before
  implementation: scaffolds a dedicated specs folder with a guided
  note-taking template (note.md). Use even for features that feel small;
  the template's checklist catches hidden async/webhook mechanisms and
  money-touching files that are easy to skip when writing notes quickly.
---

# Starting a Feature Spec

## Overview

First step of a 4-stage flow: `note.md` (this skill), then `questions.md`
(**spec-workflow:analyze**), then `ticket.md` + `plan.md`
(**spec-workflow:ticket-plan**). This skill only scaffolds the folder and
the note-taking template, it does not analyze anything yet.

## When to Use

- Starting to think about a new feature, before any code or ticket exists
- You already have some notes in your head about relevant files/functions
  and want a place to capture them properly

Don't use for: trivial one-file fixes, or features where the note is
already written (use **spec-workflow:analyze** directly instead).

## Steps

1. Ask the user for the feature slug (kebab-case) and the specs root if not
   obvious.
2. Pick the template language: match it against the subfolders of
   `templates/` in this skill's own directory (each subfolder name is a
   supported language code, e.g. `fr`, `en`). If the user's language has no
   matching subfolder, default to `en`.
3. Create `<root>/<slug>/`.
4. Copy `templates/<lang>/note.template.md` to `<root>/<slug>/note.md`.
5. Tell the user the file is ready to fill in. Do not fill it in yourself,
   this is the user's own research to do. If the user explicitly asks you
   to dig into a specific file they've already identified (they know it
   matters but don't have time to read it themselves), that's fine, do that
   one piece of legwork for them. The line is: you never decide what goes
   in `note.md` on the user's behalf, but you can do delegated research work
   they explicitly ask for.

## Common Mistakes

- Pre-filling the note with unprompted guesses about the feature: the whole
  point is the user's own research (cf. the workflow this skill is part of:
  the user does the investigation and decisions, the assistant writes or
  advises from it, or does specific delegated digging when asked).
- Creating `questions.md`, `ticket.md`, or `plan.md` at this stage: they
  don't exist until there's real content to analyze.
