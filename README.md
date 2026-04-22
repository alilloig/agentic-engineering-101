# Agentic Engineering 101

A collection of educational resources for learning agentic development with Claude Code.

## Contents

### `topics/`

Markdown files with long-form coverage of each course topic:

- **01-intro** — Why this talk: the shift, the goal, and the cost of speed
- **02-ml** — ML basics: evolution of AI, the Transformer, self-attention, tokens, context windows, and training
- **03-the-harness** — What Claude Code actually is: the agent loop, tool calls, permissions, context window, CLAUDE.md, skills
- **04-setup** — Install the three surfaces and drop in the `.claude.example` bundle
- **99-future-topics** — Parking lot for a follow-up session (hooks, plugins, MCPs, advanced workflows)

Slides for the talk live in Google Slides — not in this repo. The topic files are the source of truth; slide content is extracted from them.

### `.claude.example/`

A working starter bundle for `~/.claude/` — `settings.json` with `auto` permission mode and auto-install of the day-zero plugins, a user-level `CLAUDE.md` template, and a `skills/` folder. Used live in chapter 04. Prototype of a standalone `claudefiles` repo that will get split out later.
