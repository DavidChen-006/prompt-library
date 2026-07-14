# Add a Prompt

The user has written (or is dictating) a new prompt. File it. The prompt text
is theirs — store it verbatim, never rewrite or "improve" it. If they gave you
an idea rather than prompt text, ask them to write the prompt (or draft one
and ask them to approve it word-for-word before filing).

Steps:

1. Pick a short kebab-case name that names the *move* the prompt makes
   (e.g. `reverse-engineer`, `steelman-objection`), not its topic.
2. Save the prompt verbatim to `prompts/<name>.md`.
3. Write the index entry in `index.md`:
   - **Does:** one line, what the prompt produces.
   - **Use when:** the situations, signals, and question-shapes it's for.
     Be specific enough that this entry cannot be confused with any other.
4. Overlap check — this is the important part. Compare the new "Use when"
   against every existing entry. If two entries could plausibly claim the
   same request, tell the user (e.g. "this overlaps with `reverse-engineer` —
   should this one take the code cases and that one everything else?"), let
   them decide, and sharpen BOTH entries to draw the boundary.
5. Log it: `## [YYYY-MM-DD] add | <name> | "<one-line description>"`
