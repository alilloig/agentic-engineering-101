# Agentic Engineering 101

A collection of educational resources for learning agentic development with Claude Code.

## Contents

### `topics/`

Markdown files with introductory coverage of each course topic:

- **01-ml-basics** — Tokens, transformers, context windows, and context rot
- **02-installation** — CLI, Desktop app, and Chrome extension setup
- **03-basic-usage** — Prompting, CLAUDE.md, settings, plan mode, and permissions
- **04-day-0-setup** — Essential plugins for project setup, code quality, and git workflow
- **05-expanding-claude-code** — Skills, AGENTS.md, hooks, plugins, and MCPs

### `slides/`

Marp presentation decks generated from `topics/` using the `marp-slide-content` skill and styled with the Sui dark theme via `sui-marp-theme`. Each deck is self-contained with embedded CSS.

Render with:

```bash
marp slides/01-ml-basics.md --html
```

### `claudefiles/`

Example `~/.claude/` configuration for bootstrapping concepts taught in the course. *(Coming soon)*
