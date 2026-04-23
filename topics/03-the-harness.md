# The Harness

Claude Code, Cursor, Cline, Codex, Aider — if you strip away the UI differences, these are all the same thing: an agent harness. A loop wrapped around a large language model. The model can't do anything on its own — it can only produce text. The harness is what turns that text into real actions against your files, your terminal, and your browser.

This chapter opens that black box. Once you see how the loop works, every other concept — permissions, context windows, `CLAUDE.md`, skills — falls out of the same mechanics. The pieces stop being a menu of features to memorize and become different levers on the same thing.

## The harness is just a loop

Stripped down to its core, an agent harness does this, on repeat:

1. Build a message: `system prompt + message history + your latest input`
2. Send it to the model's API
3. Get a response back
4. Append the response to the message history
5. Show it to you
6. Wait for your next turn

That's a chat interface. If you stopped there, you'd have ChatGPT in a terminal.

The one thing different about an agent harness is that the model can ask to take actions — not just produce text. When the model wants to run a shell command or edit a file, the response it sends back isn't just text for you. It contains a structured request: "please run `ls -la`." The harness intercepts that request, executes the command on your machine, feeds the output back to the model as another message, and runs the loop again.

The loop keeps turning — without waiting for you — as long as the model keeps asking for actions. When the model finally produces a plain-text answer with no action request, the loop pauses and waits for you. That self-sustaining loop is what makes the thing agentic.

## Tool calls are how the model acts

The mechanism that makes this work is called a tool call. The harness's system prompt lists the tools available — `Bash`, `Read`, `Edit`, `Write`, `WebFetch`, and so on — each with a schema describing its parameters. The model is taught to emit a structured block whenever it wants to use one.

Pedagogically you'll often see this written as XML tags — `<bash>ls -la</bash>` — because that shape is easier to reason about. The real Anthropic API uses structured JSON `tool_use` blocks, but the idea is the same: the model produces a request in an agreed-upon format; the harness parses it, runs the command, and feeds the result back as the next message.

This is the whole extension mechanism. Everything fancy the tool does — browsing the web, running tests, editing files, calling out to Notion or Slack — is wired up via tool calls. Plugins add tools. MCP servers add tools. Hooks fire around tool calls. The concept is that central.

## Permission modes control the loop

The loop turns on its own. That's powerful, but it's also terrifying if you think about it: the model could decide to run `rm -rf /` or push to main. So the harness sits between the model's request and the actual execution of the command. Before each tool call fires, the harness checks its permission rules.

The permission mode determines how that check works:

- **default** — Claude asks before every tool call. Safe, slow, annoying.
- **acceptEdits** — File edits go through without asking; shell commands still prompt. The sweet spot when you don't yet trust your allowlist but trust the model to edit files correctly.
- **auto** — A classifier looks at each requested action: safe things auto-approve, risky things prompt. Requires Sonnet 4.6 / Opus 4.6 / Opus 4.7 and a Max, Team, or Enterprise plan.
- **dontAsk** — Auto-deny anything not explicitly allowed. The opposite of auto: paranoid by default. Useful for CI.
- **bypassPermissions** — Everything runs without asking. Launched with `--dangerously-skip-permissions`. The flag name tells you the tradeoff.

And then there's **plan mode** — the odd one out, and the most important of the bunch. Plan mode disables every action that modifies state: no edits, no `Write`, no side-effect commands. Claude can still read files and run exploratory commands (with your approval), but it can only write back to you in a plan. You review the plan, push back on the approach, and when it's right you exit plan mode and Claude executes it.

**Use plan mode aggressively whenever you start something non-trivial.** New feature, unfamiliar codebase, complex debug — plan mode first. The cost is one extra round-trip. The benefit is catching misalignment before it turns into fifty changes you have to undo. Cycle to it with `Shift+Tab` or start directly with `--permission-mode plan`.

## The context window fills up fast

Every turn through the loop appends to the message history. System prompt, user turn, tool call, tool result, assistant turn — all of it. That growing blob is the context window, and it has a hard limit (currently up to 1M tokens on Claude Code, but in practice you feel the squeeze much earlier).

Three things fill the window:

- **The system prompt.** Base instructions, tool schemas, `CLAUDE.md` files, MCP tool definitions. This is paid upfront on every turn.
- **The conversation.** Every message, every tool call, every file Claude reads — all of it stays in the window until the session ends or you compact it.
- **Large tool outputs.** Dumping a 10,000-line log into the conversation is how you waste context fastest.

When the window gets crowded, the model starts to degrade. It forgets instructions from early in the session, mixes up files, invents functions that don't exist. This is **context rot**, and once you've seen it you won't unsee it.

`/context` shows how much of the window you've used, broken down by category. `/compact` summarizes the conversation into a shorter form and continues in a fresh session with that summary. Use both liberally.

## Shaping the system prompt

The system prompt is not a fixed string. Claude Code builds it up from several sources — and the interesting ones are under your control.

### `CLAUDE.md`

A markdown file Claude reads at the start of every session. It tells Claude what this project is and how you want things done. Project structure, coding conventions, build commands, workflow constraints.

Three scopes, highest precedence first:

- **Managed policy** — system-level, set by IT. Not overridable.
- **Project** — `./CLAUDE.md` or `./.claude/CLAUDE.md`, checked into source control. Team-shared standards.
- **User** — `~/.claude/CLAUDE.md`, personal preferences across every project on your machine.

Keep each file under ~200 lines. When it grows beyond that, split with `@path/to/file` imports or move rules into `.claude/rules/`.

**Bootstrap with `/init`.** In any new repo, run `/init` — Claude scans the codebase and generates a starter `CLAUDE.md` with build commands, test instructions, and conventions it discovers. If a `CLAUDE.md` already exists, it proposes improvements rather than overwriting. Run it once, then refine with what Claude can't discover: architectural decisions, team conventions, workflow rules.

**`AGENTS.md` — the portable equivalent.** You may see an `AGENTS.md` file in repos that use Codex, Cursor, Zed, or one of 60+ other agent tools. It's an industry-standard convention for the same idea, now stewarded by the Agentic AI Foundation under the Linux Foundation. Claude Code reads `CLAUDE.md`, not `AGENTS.md` directly — but if your team already maintains an `AGENTS.md` for other tools, the recommended pattern is a one-line bridge: `@AGENTS.md` inside your `CLAUDE.md` pulls it in without duplicating content.

### Skills

A skill is a playbook — a bundle of instructions, examples, and procedural knowledge for a specific task. When Claude hits a task that matches, it pulls the skill off the shelf and follows it. Think of skills as the way you teach Claude how *you* want specific jobs done — writing tests, reviewing code, drafting release notes — without having to re-explain every session.

Mechanically, a skill is a `SKILL.md` file — YAML frontmatter plus plain-text instructions. The frontmatter tells Claude *when* to use the skill (via a `description` field); the body tells it *how*. No compiled code, no runtime. You write prose; Claude follows it.

Skills live under `.claude/skills/` (project), `~/.claude/skills/` (personal), or inside a plugin's `skills/` folder. Invoke a skill by typing `/skill-name`, or let Claude load one automatically when its description matches the task.

Full skill content only loads on invocation — the lightweight part that stays in every system prompt is just the description. This matters a lot for context budget: you can ship dozens of skills without drowning the window.

### Subagents

A subagent is a specialist persona with its own system prompt, model preference, and tool restrictions. You spawn one with the `Task` tool to delegate a focused job — code review, a long-running investigation, a research task — and the subagent runs in its own context window. Its work doesn't pollute yours; only its final summary comes back.

This is the stable, shipping version of delegation. There is also an experimental **agent teams** feature (gated by `CLAUDE_CODE_EXPERIMENTAL_AGENT_TEAMS=1`) that orchestrates multiple Claude Code sessions working in coordination on a shared task — a separate concept, and a different mechanism from `AGENTS.md` despite some online confusion. Worth knowing exists; not stable enough to build on yet.

## Extending the harness

Shaping the system prompt is one lever. The other is extending what the harness itself can do — adding new tools, new event handlers, new integrations. Three mechanisms to know.

### Hooks

Hooks are lifecycle handlers. They fire on events — `PreToolUse`, `PostToolUse`, `SessionStart`, `UserPromptSubmit`, `Stop`, `PreCompact`, and ~25 others — and can inspect, modify, or block what the harness is about to do. Four handler types: shell command, HTTP POST, LLM prompt (a yes/no decision from a model), and subagent.

Configured in `settings.json` under `hooks` with an event name, an optional regex matcher, and a handler. Canonical example: a `PreToolUse` hook with matcher `"Bash"` that runs a shell script denying `rm -rf` before the command ever reaches the OS. That is the shape. Format checks after edits, approval gates before pushes, desktop notifications on session end — hooks are the generic event system that lets you wire policy and automation around the loop.

### Plugins

A plugin bundles skills, commands, hooks, agents, and MCP servers into one installable package. Where loose `.claude/` config applies to a single project, a plugin is versioned, shareable, and publishable to a marketplace.

Plugins install with `/plugin install <name>@<marketplace>`. Anthropic hosts the official marketplace (`claude-plugins-official`); private GitHub repos also work as marketplaces. Inside a plugin you will find `.claude-plugin/plugin.json` plus folders for whatever it ships — `skills/`, `commands/`, `agents/`, `hooks/hooks.json`, `.mcp.json`. The plugin name becomes a namespace prefix on its commands (`/my-plugin:deploy`), so nothing collides.

The day-zero bundle in chapter 4 installs eight of these on first run.

### MCPs (Model Context Protocol)

MCP is an open standard for connecting AI tools to external data and services. Think USB-C for AI — Claude Code, Cursor, ChatGPT, VS Code, and others all speak it, so an MCP server built once integrates with all of them.

Mechanically, an MCP server exposes tools to the harness. A GitHub server exposes `create_issue` and `search_repos`; a Notion server exposes `fetch_page`; a Chrome DevTools server exposes browser inspection. To the model, these look like any other tool call — the harness just has more things to wire up.

Configure servers via `claude mcp add` or `.mcp.json`. Two live transports: **stdio** (local process) and **HTTP** (remote streamable HTTP). Scope determines visibility — `local` (private), `project` (team-shared in source control), `user` (all your projects).

```bash
claude mcp add --transport http stripe https://mcp.stripe.com
claude mcp add --transport stdio airtable -- npx -y airtable-mcp-server
```

Every extension in this section ties back to the constraint from earlier: each one consumes context budget. Skills ship descriptions to every turn, hooks can inject messages, MCP tools add definitions on every request (five servers with twenty tools each adds up fast), and plugins combine all of the above. Enable what you need. Disable what you do not.

## Settings and commands in practice

All of the above is driven by configuration. Two places to know:

**`settings.json`** lives at four scopes — managed, user (`~/.claude/settings.json`), project (`./.claude/settings.json`), and local override (`./.claude/settings.local.json`, gitignored). Highest precedence wins. The most useful keys:

- `permissions.defaultMode` — sets the permission mode at session start.
- `permissions.allow` / `permissions.deny` — explicit tool/command patterns to auto-approve or auto-reject.
- `env` — environment variables applied every session.

Commit `settings.json` with the project. Keep `settings.local.json` personal for machine-specific overrides.

**Slash commands** you should know cold:

- `/init` — generate a starter `CLAUDE.md` for the current repo.
- `/context` — show current context window usage.
- `/compact` — summarize the conversation and continue in a fresh window.
- `/plugin install <name>@<marketplace>` — add a plugin.
- `/plugin` — list and manage installed plugins.

## Context management is the newest core skill

Every idea in this chapter comes back to the same bottleneck: the context window. Tool calls consume tokens. Large outputs consume tokens. Your `CLAUDE.md` consumes tokens on every turn. MCP servers consume tokens on every turn. A sprawling conversation with two wrong paths taken and abandoned burns tokens you can't get back.

In the old workflow, the limit on your output was how fast you could type. In this workflow, the limit is how well you manage the model's attention. **Keeping context clean is the newest core engineering skill** — as important as knowing your language, your framework, and your tools.

In practice that looks like:

- Start new tasks in a fresh session.
- Use plan mode to avoid wasted tool calls.
- Run `/compact` when the session has drifted.
- Trim `CLAUDE.md`. Disable unused MCP servers. Turn off skills you don't reach for.
- Scope tool permissions tightly so the model doesn't have to ask constantly.

You picked the tool to go faster. Managing the context window well is how you actually do.

## References

- [Claude Code Overview](https://code.claude.com/docs/en/overview)
- [Claude Code Memory (CLAUDE.md)](https://code.claude.com/docs/en/memory)
- [Claude Code Settings](https://code.claude.com/docs/en/settings)
- [Permission Modes](https://code.claude.com/docs/en/permission-modes)
- [Skills](https://code.claude.com/docs/en/skills)
- [Subagents](https://code.claude.com/docs/en/subagents)
- [Hooks](https://code.claude.com/docs/en/hooks)
- [Plugins](https://code.claude.com/docs/en/plugins)
- [MCP in Claude Code](https://code.claude.com/docs/en/mcp)
- [Model Context Protocol](https://modelcontextprotocol.io/introduction)
- [Claude Code CLI Reference](https://code.claude.com/docs/en/cli-usage)
