# prompt-library

A prompt library that routes itself. Instead of memorizing triggers
(TextExpander-style), you describe what you want — the LLM matches your
request against a curated library and applies the right prompt. The human
writes and refines the prompts; the LLM does the selection.

**The prompts are functions; the LLM is the dispatcher; your request is the call.**

## Architecture

| Layer | File(s) | Owner |
|---|---|---|
| Prompts | `prompts/*.md` | Human (LLM never edits) |
| Index (routing table) | `index.md` | Co-owned: human intent, LLM sharpens |
| Dispatcher | `SKILL.md` | Co-evolved routing discipline |
| Log | `log.md` | LLM appends, human audits |

## Operations

- **Invoke** — `/prompt <your request>`. The dispatcher reads the index, picks
  the best-fit prompt, and answers as if you'd typed it in full. If nothing
  fits, it says so rather than improvising.
- **Add** — write a prompt, ask to file it. The LLM writes the index entry and
  checks it for overlap with existing entries.
- **Refine** — periodic health check: dead prompts, overlapping entries,
  gaps in the log, misroutes.

## Install

Symlink this repo into your skills directory (works with any Agent Skills
compatible harness):

```sh
ln -s "$(pwd)" ~/.claude/skills/prompt
```

Then: `/prompt explain how JWT refresh works like I'm building it myself`
