# spec-workflow

**Don't lose your brain.** A Claude Code plugin that keeps you the one
doing the thinking — the model scaffolds, surfaces gaps, and writes down
decisions, but every product/architecture call stays yours.

3-stage workflow to turn a feature idea into an implementation-ready
ticket and plan, before any code is written.

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
/plugin marketplace add myr0IX/spec-workflow
/plugin install spec-workflow@spec-workflow-marketplace
```

## Local testing

```
/plugin marketplace add ./spec-workflow
/plugin install spec-workflow@spec-workflow-marketplace
```

## Usage

### 1. `spec-workflow:start` — write the note

Ask Claude to start a spec for the feature you're about to build:

> Use spec-workflow:start for the "podcast-generation" feature.

Claude will ask for a feature slug (kebab-case) and a specs root folder if
it isn't obvious from context, create `<root>/<slug>/`, and copy the
`note.template.md` scaffold there as `note.md`.

**`note.md` is yours to fill in, not Claude's.** The skill deliberately
stops after copying the template — it does not pre-fill guesses about your
feature. The template has 5 sections:

- **Fichiers concernés** — every relevant file/function, tagged `[plomberie]`
  (plain interface) or `[risqué]` (real business logic). Before closing this
  list, check explicitly for the two traps that get skipped most often:
  a webhook/callback the "obvious" files don't call, and any file that
  touches money (credits, billing, débit).
- **Que faire** — the objective, in 2-3 sentences.
- **Pour qui ?** — the persona using this feature and what it does/doesn't
  have access to (e.g. no UI, no human session) — this alone often settles
  flow questions later.
- **Hors scope** — what you're explicitly NOT doing, stated now so it
  doesn't resurface as an open question later.
- **Précédent similaire** — the closest existing feature/spec to use as a
  structural reference, or an explicit "none" if there isn't one.

Do the research yourself (read the actual files, not just titles) before
moving to the next stage — the quality of `questions.md` and the final
ticket depends entirely on what you put in `note.md`.

### 2. `spec-workflow:analyze` — turn the note into open questions

Once `note.md` has real content:

> Use spec-workflow:analyze on <slug>.

Claude reads `note.md` and every file it references, walks a fixed
checklist (execution model, money, idempotence, minimal DTO, vocabulary
traps...), and writes `questions.md` — one numbered, grounded
(`fichier:ligne`) question per open decision, each starting as `OUVERT`.
You answer them by filling in **Décision** and **Pourquoi** and flipping
**Statut** to `TRANCHÉ`. Re-running this skill later only appends new
questions from new note content — it never touches or renumbers existing
entries.

### 3. `spec-workflow:ticket-plan` — write the ticket and plan

Only once every entry in `questions.md` reads `TRANCHÉ`:

> Use spec-workflow:ticket-plan on <slug>.

Claude writes `ticket.md` and `plan.md` from the resolved decisions. If any
question is still `OUVERT`, it stops and lists exactly which ones instead
of guessing — this is the one hard gate in the whole flow.
