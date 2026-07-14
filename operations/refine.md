# Refine (Health Check)

Audit routing quality. The failure mode of a prompt library is not bad
prompts but bad selection — and misroutes almost always trace to an index
entry, not the router.

Read `index.md`, `log.md`, and the list of files in `prompts/`. Report on:

1. **Dead prompts** — prompts never (or rarely) selected in the log. Either
   dead weight or a bad index entry hiding a good prompt. Propose which.
2. **Overlaps** — pairs of "Use when" entries that could claim the same
   request. Propose sharper boundary lines for both.
3. **Gaps** — log entries with `NONE` (no prompt matched). These are the
   backlog: name the prompt the user should write for each cluster.
4. **Misroutes** — log entries with corrective notes, or near-ties. Propose
   a sharper "Use when" line for the entry that caused each one.
5. **Mergers** — two prompts that are really one prompt with a parameter.

Propose changes to `index.md` entries and to `SKILL.md` routing discipline;
apply them only after the user approves. NEVER edit files in `prompts/` —
if a prompt itself should change, say so and let the user rewrite it.

Log the pass: `## [YYYY-MM-DD] refine | <summary of changes>`
