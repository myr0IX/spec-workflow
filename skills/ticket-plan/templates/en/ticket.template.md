# <Feature>: <one-line objective>

⏱️ **Estimate: <N days>** (<summary of the big pieces: N endpoints + migration + e2e tests...>)

## Objective

<!-- 2-4 sentences: by the end of this ticket, the client can do X by calling Y.
Mention dependencies on other tickets if any. -->

Context: <!-- what already exists (webapp, third-party service...) and what this
ticket exposes/hardens/centralizes, not a reinvention. -->

**Resolved product decisions:**
<!-- Only cross-cutting decisions that have no single dedicated step to live in (e.g.
overall architecture choice, product scope). If a RESOLVED decision in questions.md
maps 1:1 to a plan step, its rationale lives in that step's "Why / for whom" and must
NOT be repeated here — each decision has exactly one place to live in the ticket. One
per line, decision + why in one short clause (the "Why" of the matching RESOLVED
entry, condensed). The ticket must read standalone: never point back to questions.md
to understand a decision, and don't cite Q<n> numbers in the final text (questions.md
stays the historical record of options considered, not required reading to
implement). If no decision is genuinely cross-cutting, delete the section entirely
rather than filling it by default. -->
- <decision 1> — <why, in one clause>
- <decision 2> — <why, in one clause>

## Read before starting

<!-- Only files that are genuinely load-bearing to understand the ticket as a whole:
the exact precedent to mirror, a non-obvious internal convention, the third-party
contract. Do NOT list every file the implementation will touch or cross-reference
(that's what "Files to create / modify" and each step's own detail are for): if a
file only helps once its matching step is underway, leave it there, not here. Aim for
the smallest set that makes the ticket understandable, not exhaustive coverage.
Include the similar precedent if one exists. -->

- `<file>`: <what to remember>

## Files to create / modify

```
<path>                          ← <new|extend|delete> (<what it does>)
```

<!-- Add a risk section (🚨) only if a real security/data risk exists
(e.g. SSRF if the client provides a URL). Don't invent one if there isn't. -->

<!-- Add a trap section (🪤) only if there's a real vocabulary/internal
convention trap to untangle before coding (e.g. misleading naming between layers). -->

## Implementation plan: in this order (1 step = 1 commit)

### Step 1: <title> (scope `<scopes>`)

**What to do**: <!-- actionable description, no vague prose -->

**Why / for whom**: <!-- why this approach rather than an obvious alternative,
reference the corresponding resolved decision if useful -->

✅ **Validation**: <!-- what proves the step works, happy path + error case -->

<!-- Repeat one section per step. -->

## Acceptance criteria

- [ ] <full end-to-end scenario, with curl if possible>
- [ ] <error case 1>
- [ ] <error case 2>
- [ ] API documentation up to date; typecheck + tests pass

## Security checklist

<!-- Only points that genuinely apply, don't copy a generic checklist if a
point doesn't apply to this feature. -->

- [ ] <applicable security point>

## Out of scope

<!-- Carried over from the "Out of scope" section of note.md, plus anything
explicitly deferred in questions.md ("Not in this ticket for now"). -->

- <out-of-scope item>
