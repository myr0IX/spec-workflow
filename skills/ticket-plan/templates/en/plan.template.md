# Dev plan: <Feature>

See `ticket.md` for the objective, product decisions, and acceptance criteria.
This file covers execution: files touched, steps/commits, tests, verification.

## Files to create / modify

```
<same list as ticket.md, kept in sync>
```

## Implementation plan: in this order (1 step = 1 commit)

### Step 1: <title> (scope `<scopes>`)

**What**: <!-- restates the ticket's "What to do", reworded for execution -->

**Why <technical choice>**: <!-- the alternative rejected and why -->

✅ **Validation**: <!-- identical to the ticket -->

<!-- Repeat one section per step, in the same order as ticket.md. -->

## Tests (TDD, high value only)

<!-- Per step: which cases are actually worth a test (behavior, not a
line-by-line re-assertion of the zod schema). State explicitly what you're
choosing not to test. -->

- **Step 1**: <happy path>, <error case>
- **Avoid**: <noise tests that add nothing>

## Manual end-to-end verification

```bash
# 1. <step>
curl -X <METHOD> $BASE/api/v1/<route> -H "Authorization: Bearer $KEY" ...

# 2. <next step>
```

Replay with the ticket's error cases (missing scopes, cross-tenant resource,
invalid input) to validate the rejections.
