# <Feature>: <one-line objective>

⏱️ **Estimate: <N days>** (<summary of the big pieces: N endpoints + migration + e2e tests...>)

## Objective

<!-- 2-4 sentences: by the end of this ticket, the client can do X by calling Y.
Mention dependencies on other tickets if any. -->

Context: <!-- what already exists (webapp, third-party service...) and what this
ticket exposes/hardens/centralizes, not a reinvention. -->

**Resolved product decisions:**
<!-- One per line, short format, each traceable to a RESOLVED entry in questions.md.
Don't re-explain the full reasoning here, just the decision, the detail is in
questions.md. -->
- <decision 1>
- <decision 2>

## Read before starting

<!-- Files/routes that give the necessary context, with what to remember in
one line each. Include the similar precedent if one exists. -->

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
