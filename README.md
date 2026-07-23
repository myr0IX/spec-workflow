# spec-workflow

Claude Code plugin: 3-stage workflow to turn a feature idea into an
implementation-ready ticket and plan, before any code is written.

```
note.md  →  questions.md  →  ticket.md + plan.md
(start)     (analyze)        (ticket-plan)
```

- **`spec-workflow:start`** — scaffolds a specs folder and a guided
  note-taking template (`note.md`).
- **`spec-workflow:analyze`** — reads `note.md`, walks a fixed checklist
  (hidden async/webhook mechanisms, billing files, naming traps...) and
  produces/updates `questions.md`, one open decision at a time.
- **`spec-workflow:ticket-plan`** — once every entry in `questions.md` is
  `TRANCHÉ`, writes the final `ticket.md` and `plan.md`.

The user makes every product/architecture decision; the skills only
scaffold, surface gaps, and write down what was already decided.

## Install

```
/plugin marketplace add <owner>/<repo>
/plugin install spec-workflow@spec-workflow-marketplace
```

## Local testing

```
/plugin marketplace add ./spec-workflow
/plugin install spec-workflow@spec-workflow-marketplace
```
