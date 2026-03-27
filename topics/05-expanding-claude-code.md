# Expanding and Demystifying Claude Code

## Skills

### What Are Skills

A skill is just a `SKILL.md` file -- YAML frontmatter plus plain-text instructions. The frontmatter tells Claude *when* to use the skill (via a `description` field), and the markdown body tells it *how*. No compiled code, no runtime. You write prose, and Claude follows it.

Skills live under `.claude/skills/` (project-scoped), `~/.claude/skills/` (personal), or inside a plugin's `skills/` folder.

### How to Use Skills

Invoke a skill by typing `/skill-name`, or let Claude load one automatically when its description matches your task. Full content only loads on invocation, keeping context lean. `disable-model-invocation: true` restricts a skill to manual invocation; `user-invocable: false` hides it from the `/` menu but lets Claude invoke it automatically when relevant.

### Examples

Bundled skills include `/batch` (parallel large-scale changes across worktrees), `/claude-api` (building apps with the Anthropic SDK), `/debug` (session log analysis), `/loop` (recurring prompt execution on an interval), and `/simplify` (three parallel agents that review recent changes for reuse, quality, and efficiency, then apply fixes). Plugins add more -- a `code-review` plugin skill might check error handling, security, and test coverage on every review.

## AGENTS.md

### What It Is

AGENTS.md is a convention (not a built-in feature) for cataloging reusable agent roles for team-based workflows -- each with a system prompt, model preference, and behavioral constraints. Think of it as a cast list: each entry describes a specialist that you reference when spawning agent teams.

### How It Works

When spawning a team, Claude Code uses each role's system prompt as the base and appends task-specific instructions. A `move-agent` role, for instance, defines a Sui Move specialist with coding conventions, documentation lookup steps, and mandatory build/test verification. Requires `CLAUDE_CODE_EXPERIMENTAL_AGENT_TEAMS=1` in your `settings.json` env block.

### When You Need It

Use it when tasks benefit from parallel specialists -- a frontend agent and a contract agent working simultaneously, or a docs agent updating documentation while a code agent implements changes.

## Hooks

### What Are Hooks

Hooks are event-driven handlers that fire at specific lifecycle points -- validating commands before execution, auto-formatting after edits, or blocking dangerous operations. When an event fires and a matcher matches, Claude Code passes JSON context to your handler.

### Hook Events

Key events include `SessionStart`, `UserPromptSubmit`, `PreToolUse` (can block), `PostToolUse`, `Stop`, `PreCompact`, `Notification`, and `SessionEnd` -- plus many more (25+ total, including `PermissionRequest`, `SubagentStart/Stop`, `FileChanged`, and `PostCompact`). See the full list in the hooks documentation.

Four handler types: **command** (shell script), **HTTP** (POST to a URL), **prompt** (LLM yes/no decision), and **agent** (subagent with tool access).

### How to Configure Hooks

Define hooks in `settings.json` under a `hooks` key: specify an event, an optional `matcher` regex, and one or more handlers. Example: a `PreToolUse` hook with matcher `"Bash"` and a command handler pointing to `.claude/hooks/block-rm.sh` runs that script before every Bash command, letting it deny `rm -rf`.

## Plugins

### What Are Plugins

Plugins bundle skills, commands, hooks, agents, and MCP servers into a single installable package. Where standalone configuration in `.claude/` applies to one project, a plugin can be shared across teams, published to a marketplace, and versioned independently.

### How to Install and Manage Plugins

Plugins install from marketplaces -- the official Anthropic marketplace and private GitHub repositories are both supported. Manage installed plugins through `settings.json`. During development, `/reload-plugins` picks up changes without restarting.

### Plugin Anatomy

A plugin directory contains `.claude-plugin/plugin.json` plus root-level directories: `skills/`, `commands/`, `agents/`, `hooks/hooks.json`, and `.mcp.json`. The manifest `name` becomes the namespace prefix (e.g., `/my-plugin:deploy`), preventing conflicts.

## MCPs (Model Context Protocol)

### What Are MCPs

MCP (Model Context Protocol) is an open standard for connecting AI tools to external data and services -- think USB-C for AI. Claude Code, ChatGPT, Visual Studio Code, Cursor, and others all support it, so a server built once integrates everywhere.

### How to Use MCPs

Configure servers via `claude mcp add` or by editing `.mcp.json`. Two main transport types: **stdio** (local processes) and **HTTP** (remote Streamable HTTP). A legacy **SSE** transport also exists but is deprecated in favor of HTTP. Scopes control visibility: `local` (private), `project` (shared in version control), or `user` (all your projects).

```bash
claude mcp add --transport http stripe https://mcp.stripe.com
claude mcp add --transport stdio airtable -- npx -y airtable-mcp-server
```

### Common MCP Integrations

Common integrations include Chrome DevTools (debugging live web apps), Linear and Notion (project management), and custom API wrappers. Plugins can bundle MCP servers -- enabling `chrome-devtools-mcp` auto-connects its server at startup.

## Impact on the Context Window

Every extension ties back to the context window from Topic 01. Each consumes budget: **skills** load descriptions (~2% of the window) and full content on invocation; **hooks** run externally with minimal impact unless they inject messages; **MCP tools** add definitions to every turn (five servers with 20 tools each adds up); **plugins** combine all layers simultaneously.

Be intentional: enable what you need, disable what you do not. Use `disable-model-invocation: true` on manual skills to keep descriptions out of context. Disconnect unused MCP servers. Run `/context` to check budget limits. The system is powerful because every piece is optional and modular.

## References

- Skills: https://code.claude.com/docs/en/skills
- Hooks: https://code.claude.com/docs/en/hooks
- MCP in Claude Code: https://code.claude.com/docs/en/mcp
- Model Context Protocol: https://modelcontextprotocol.io/introduction
- Plugins: https://code.claude.com/docs/en/plugins
- Claude Code Overview: https://code.claude.com/docs/en/overview
