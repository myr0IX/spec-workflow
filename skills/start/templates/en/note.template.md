<!--
How to fill in this file:
- Replace each section between <!-- --> with your own content, then delete the comment.
- The goal isn't word-for-word exhaustiveness, but not skipping the categories
  below: these are exactly the ones that generated back-and-forth last time.
-->

# Files involved

<!--
Existing project: for each relevant file/function, one line: path + what it
does, tagged:
- [plumbing]: just an interface, nothing special to say about it
- [risky]: business logic, computation, or non-trivial behavior

Greenfield project (no existing code for this feature): say so explicitly
("No existing code, greenfield project") instead of leaving the section
empty, then list the files/modules you plan to create with the same
[plumbing]/[risky] tag applied to each module's intended role (the tag is
about the component's nature, not about whether it exists yet).

Before closing this list, explicitly check (the 2 most frequent traps):
1. Is there an async webhook/callback somewhere in the feature's folder,
   even if none of the "obvious" files call it? (grep for "webhook" in
   the relevant api folder — for greenfield, check instead whether the
   planned flow implies one)
2. Does any of the files touch money (credits, billing, charges)?
   These two are almost always the ones that get forgotten to list even
   though they weigh the most on architecture decisions.
-->

# What to do

<!-- Objective in 2-3 sentences: what should exist at the end. -->

# How

<!-- High-level technical approach, ONLY what's already decided: which
component does what, how the pieces fit together (e.g. "separate Python
service that writes directly to the database, the backend only reads").
No code, no schema, no interface signature: that's spec-workflow:ticket-plan's
job once questions.md is resolved.

If a piece of the "how" isn't decided yet, do NOT write it here as if it
were settled: leave it out, spec-workflow:analyze will surface it as a
question in questions.md instead. This section only holds decisions already
made, never an assumption or a default choice. -->

# For whom?

<!-- The persona who will use this feature, what they already know, what they
don't have (e.g. no UI, no human session context). This alone often settles
flow questions by itself (cf. script/render podcast flow: no human review
possible on the API client side, so no intermediate editing step to expose). -->

# Out of scope

<!-- What you explicitly do NOT want to do in this ticket, even if it seems
related. Saying it now avoids rediscovering it as an open question later. -->

# Similar precedent

<!-- An existing ticket/folder (specs/<other-feature>/) that resembles this
one the most, to use as a reference for structure and decisions already made
(scopes, error handling, idempotence...). If none exists, say so explicitly. -->
