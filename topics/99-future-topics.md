# Future Topics

Parking lot for a follow-up session that picks up where the main talk leaves off. The first talk gets you productive with Claude Code and introduces hooks, plugins, and MCPs conceptually. This one goes deep: building, publishing, and composing your own.

## Hooks in practice

The main talk covers what hooks are. The follow-up is authoring them.

- Practical hook patterns: formatter on `PostToolUse(Edit)`, commit-message gate on `PreToolUse(Bash(git commit))`, desktop notification on `SessionEnd`, policy checks that read environment context.
- Composing multiple hooks on the same event.
- Hook idioms using `HTTP` and `prompt` handlers, not just shell.
- Debugging hooks — inspecting the JSON context, logging, failure modes.

## Building and distributing plugins

The main talk installs eight plugins from the official marketplace. The follow-up builds one.

- Anatomy of a real plugin: `.claude-plugin/plugin.json` manifest, layout, namespace prefix, versioning.
- Bundling skills, commands, hooks, agents, and MCP servers into one package.
- Publishing to a private marketplace — a GitHub repo works.
- Team distribution patterns: shared marketplace, pinned versions, CI checks that a plugin still matches its manifest.
- `/reload-plugins` during development.
- Finding plugins worth installing beyond the day-zero eight: language-specific linters, project-management integrations, deploy workflows.

## Writing MCP servers and wiring integrations

The main talk says MCPs are tools the harness can call. The follow-up walks through what it takes to build one and the integrations worth wiring up.

- Building an MCP server: the spec, the SDKs, stdio vs. HTTP, when to pick which.
- Wrapping an internal API as an MCP server for your team.
- Canonical integrations to demo:
  - Chrome DevTools for live web-app debugging.
  - Linear or Notion for project management.
  - A custom API wrapper around an internal service.
- Security posture: scopes, secrets handling, what the model actually sees.

## Subagents in anger

- Composing teams of specialists — delegating pieces of a task to parallel subagents.
- Using `Task` to keep long investigations out of the main context.
- Patterns from the wild: the `code-review` plugin's five-agent pattern as a worked example.
- The `AGENTS.md` experiment once it stabilizes.

## Advanced context management

- `/compact` strategies — when to summarize, what to preserve, how to recover when it over-compresses.
- Multi-session workflows with shared project memory.
- Scaling CLAUDE.md past 200 lines: `@imports`, `.claude/rules/`, conditional rules.
- Monitoring token usage and cost control.

## Workflow patterns

- TDD with Claude Code.
- Plan-mode-heavy workflows for legacy code.
- Parallel-agent patterns (the `code-review` plugin, revisited).
- CI/CD with `dontAsk` mode and tight allowlists.

## References

- [Hooks](https://code.claude.com/docs/en/hooks)
- [Plugins](https://code.claude.com/docs/en/plugins)
- [MCP in Claude Code](https://code.claude.com/docs/en/mcp)
- [Model Context Protocol](https://modelcontextprotocol.io/introduction)
- [Subagents](https://code.claude.com/docs/en/subagents)
