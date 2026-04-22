# Future Topics

Parking lot for a follow-up session that picks up where the main talk leaves off. The first talk gets you productive with Claude Code; this one turns you into someone who shapes it.

## Hooks

Event-driven handlers that fire at lifecycle points — `SessionStart`, `UserPromptSubmit`, `PreToolUse`, `PostToolUse`, `Stop`, `PreCompact`, `SessionEnd`, and 25+ more. When an event fires and a matcher matches, Claude Code hands JSON context to your handler.

Four handler types: **command** (shell script), **HTTP** (POST to a URL), **prompt** (LLM yes/no decision), **agent** (subagent with tool access).

Configured in `settings.json` under `hooks`: event, optional matcher regex, one or more handlers. Canonical example: a `PreToolUse` hook with matcher `"Bash"` and a shell handler that denies `rm -rf` before it ever reaches the OS.

## Plugins beyond day zero

The official marketplace has over a hundred entries. The day-zero eight are a floor; real productivity gains come from task-specific plugins — language-specific linters, project-management integrations, deploy workflows.

Topics to cover:

- Finding plugins worth installing (marketplace browsing, plugin search).
- Building your own: `.claude-plugin/plugin.json` manifest, bundling skills/commands/hooks/agents/MCPs, namespace prefix.
- Publishing to a private marketplace (a GitHub repo works).
- Team distribution patterns.
- `/reload-plugins` during development.

## MCPs (Model Context Protocol)

An open standard for connecting AI tools to external data and services. USB-C for AI — Claude Code, Cursor, ChatGPT, VS Code, and others all speak it, so a server you build once integrates with all of them.

Configured via `claude mcp add` or `.mcp.json`. Two live transports: **stdio** (local process) and **HTTP** (remote streamable HTTP). Legacy **SSE** is deprecated. Scopes: `local` (private), `project` (team-shared in source control), `user` (all your projects).

```bash
claude mcp add --transport http stripe https://mcp.stripe.com
claude mcp add --transport stdio airtable -- npx -y airtable-mcp-server
```

Canonical integrations to demo:

- Chrome DevTools for live web-app debugging.
- Linear or Notion for project management.
- A custom API wrapper around an internal service.

## Subagents in anger

Beyond the basics. Composing teams of specialists. Using `Task` to delegate investigations that would otherwise pollute the main context. The `AGENTS.md` experiment (once it stabilizes).

## Advanced context management

- `/compact` strategies — when to summarize, what to preserve.
- Multi-session workflows with shared project memory.
- Context-aware CLAUDE.md patterns using `@imports` and `.claude/rules/`.
- Monitoring token usage and cost control.

## Workflow patterns

- TDD with Claude Code.
- Plan-mode-heavy workflows for legacy code.
- Parallel-agent patterns (the `code-review` plugin is a worked example).
- CI/CD with `dontAsk` mode and tight allowlists.

## References

- [Hooks](https://code.claude.com/docs/en/hooks)
- [Plugins](https://code.claude.com/docs/en/plugins)
- [MCP in Claude Code](https://code.claude.com/docs/en/mcp)
- [Model Context Protocol](https://modelcontextprotocol.io/introduction)
- [Subagents](https://code.claude.com/docs/en/subagents)
