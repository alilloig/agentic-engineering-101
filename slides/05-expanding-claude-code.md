---
marp: true
paginate: true
footer: "![w:16](assets/images/sui-logo.svg) Sui"
---

<style>
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap');

/* === BASE — DARK THEME (default) === */
section {
  background: #000000;
  color: #8B8B8B;
  font-family: 'Inter', 'SF Pro Display', -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;
  font-size: 22px;
  font-weight: 400;
  line-height: 1.5;
  padding: 60px;
  width: 1280px;
  height: 720px;
  position: relative;
}

section h1 { color: #FFFFFF; font-size: 42px; font-weight: 700; line-height: 1.15; margin: 0 0 16px 0; letter-spacing: -0.02em; }
section h2 { color: #FFFFFF; font-size: 32px; font-weight: 600; line-height: 1.25; margin: 0 0 12px 0; }
section h3 { color: #FFFFFF; font-size: 24px; font-weight: 600; line-height: 1.3; margin: 0 0 8px 0; }
section h4 { color: #8B8B8B; font-size: 20px; font-weight: 500; line-height: 1.4; margin: 0 0 8px 0; }
section p { margin: 0 0 12px 0; }
section strong { color: #FFFFFF; font-weight: 600; }
section em { color: #4DA2FF; font-style: normal; }
section a { color: #4DA2FF; text-decoration: none; }
section code { background: #1A1A1A; color: #4DA2FF; padding: 2px 6px; border-radius: 4px; font-size: 0.9em; }
section pre { background: #0A0A0A; border: 1px solid #3A3A3A; border-radius: 8px; padding: 20px; margin: 12px 0; }
section pre code { background: transparent; padding: 0; }
section ul, section ol { margin: 0 0 12px 0; padding-left: 24px; }
section li { margin-bottom: 6px; }
section li::marker { color: #4DA2FF; }
section blockquote { border-left: 3px solid #4DA2FF; padding-left: 16px; margin: 12px 0; color: #AAAAAA; }
section table { width: 100%; border-collapse: collapse; margin: 12px 0; }
section th { color: #FFFFFF; background: #000000; font-weight: 600; text-align: left; padding: 10px 16px; border-bottom: 2px solid #4DA2FF; }
section td { padding: 8px 16px; border-bottom: 1px solid #1A1A1A; background: #000000; }
section hr { border: none; border-top: 1px dashed #3A3A3A; margin: 24px 0; }

/* Pagination */
section::after { color: #4DA2FF; font-size: 14px; font-weight: 600; background: rgba(77,162,255,0.1); border-radius: 12px; padding: 2px 10px; }

/* Footer & Header */
section footer { color: #8B8B8B; font-size: 14px; position: absolute; bottom: 24px; left: 60px; }
section header { color: #4DA2FF; font-size: 14px; font-weight: 500; position: absolute; top: 24px; right: 60px; }

/* === GRID SYSTEM === */
section .grid { display: grid; gap: 24px; width: 100%; height: auto; }
section .col { display: flex; flex-direction: column; border-top: 1px dashed #3A3A3A; padding-top: 16px; }
section .col h3 { margin-bottom: 8px; }
section .col p { font-size: 18px; margin: 0; }

/* Category label */
section .category { display: inline-flex; align-items: center; gap: 6px; font-size: 11px; font-weight: 600; letter-spacing: 0.08em; text-transform: uppercase; color: #8B8B8B; font-family: 'Inter', monospace; margin-bottom: 8px; }
section .category::before { content: ''; display: inline-block; width: 8px; height: 8px; background: #4DA2FF; flex-shrink: 0; }

/* Column heading markers — blue square */
section .col h3::before { content: ''; display: inline-block; width: 8px; height: 8px; background: #4DA2FF; margin-right: 10px; vertical-align: middle; }

/* Droplet icon marker variant */
section .col.icon-marker h3::before { content: ''; width: 20px; height: 20px; background: none; margin-right: 8px; background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 24 24' fill='none'%3E%3Cpath d='M12 2C12 2 5 10 5 14.5C5 18.09 8.13 21 12 21C15.87 21 19 18.09 19 14.5C19 10 12 2 12 2Z' stroke='%234DA2FF' stroke-width='1.5' fill='none'/%3E%3Cpath d='M12 18C14.21 18 16 16.21 16 14C16 11 12 6 12 6C12 6 8 11 8 14C8 16.21 9.79 18 12 18Z' stroke='%234DA2FF' stroke-width='1' fill='none'/%3E%3C/svg%3E"); background-size: contain; background-repeat: no-repeat; }

/* Stats */
section .stat { color: #FFFFFF; font-size: 48px; font-weight: 700; line-height: 1; margin-bottom: 4px; }
section .stat-label { color: #8B8B8B; font-size: 16px; }

/* Cards */
section .card { background: #0A0A0A; border: 1px solid #1A1A1A; border-radius: 8px; padding: 16px 20px; margin-bottom: 8px; }
section .card h4 { color: #FFFFFF; margin: 0 0 4px 0; }
section .card p { margin: 0; font-size: 16px; }

/* Icon container */
section .icon { width: 48px; height: 48px; margin-bottom: 12px; }
section .icon img { width: 100%; height: 100%; object-fit: contain; }

/* === LAYOUT: lead === */
section.lead { display: flex; flex-direction: column; justify-content: flex-end; padding-bottom: 80px; }
section.lead h1 { font-size: 64px; font-weight: 700; margin-bottom: 16px; letter-spacing: -0.03em; }
section.lead p { font-size: 24px; color: #8B8B8B; max-width: 70%; }

/* === LAYOUT: cover-gradient === */
section.cover-gradient { display: flex; flex-direction: column; justify-content: flex-start; padding-top: 60px; color: #FFFFFF; }
section.cover-gradient h1 { font-size: 56px; font-weight: 700; color: #FFFFFF; letter-spacing: -0.03em; margin-bottom: 16px; position: relative; z-index: 1; }
section.cover-gradient p { font-size: 22px; color: rgba(255,255,255,0.85); max-width: 60%; position: relative; z-index: 1; }
section.cover-gradient footer, section.cover-gradient::after { display: none; }

/* === LAYOUT: section-break === */
section.section-break { display: flex; flex-direction: column; justify-content: center; align-items: center; text-align: center; }
section.section-break h1 { font-size: 48px; font-weight: 700; letter-spacing: -0.02em; }
section.section-break footer, section.section-break::after { display: none; }

/* === LAYOUT: quote === */
section.quote { display: flex; flex-direction: column; justify-content: center; align-items: center; text-align: center; padding: 80px 120px; }
section.quote p { font-size: 36px; font-weight: 500; color: #FFFFFF; line-height: 1.4; max-width: 900px; position: relative; z-index: 1; }
section.quote footer, section.quote::after { display: none; }

/* === LAYOUT: toc === */
section.toc { display: grid; grid-template-columns: 1fr 1fr; gap: 0; padding: 0; }
section.toc .toc-left { display: flex; flex-direction: column; justify-content: center; align-items: center; padding: 60px; position: relative; overflow: hidden; }
section.toc .toc-left h1 { font-size: 56px; font-weight: 700; color: #FFFFFF; position: relative; z-index: 1; }
section.toc .toc-right { display: flex; flex-direction: column; justify-content: center; padding: 60px; }
section.toc .toc-item { display: flex; align-items: baseline; gap: 16px; padding: 12px 0; font-size: 22px; font-weight: 600; }
section.toc .toc-item .toc-num { font-size: 18px; font-weight: 700; color: #8B8B8B; min-width: 30px; }
section.toc .toc-item .toc-label { color: #FFFFFF; font-weight: 600; }

/* === COLUMN LAYOUTS === */
section.cols-4 .grid { grid-template-columns: repeat(4, 1fr); margin-top: 24px; }
section.cols-3 .grid { grid-template-columns: repeat(3, 1fr); margin-top: 24px; }
section.cols-2-center { text-align: center; }
section.cols-2-center h1 { text-align: center; width: 100%; }
section.cols-2-center .grid { grid-template-columns: repeat(2, 1fr); margin-top: 24px; text-align: center; }
section.cols-2-center .col { align-items: center; }

section.cols-4-icon .grid { grid-template-columns: repeat(4, 1fr); margin-top: 24px; }
section.cols-4-icon .col h3::before { display: none; }

/* === SPLIT/LIST LAYOUTS === */
section.list-right { display: grid; grid-template-columns: 1fr 1fr; gap: 40px; align-items: start; }
section.list-right .content { display: flex; flex-direction: column; justify-content: center; height: 100%; }
section.list-right .cards { display: flex; flex-direction: column; gap: 8px; }

/* Utility */
section .accent { color: #4DA2FF; }
</style>

<!-- _class: cover-gradient -->
<!-- _paginate: false -->

![bg](assets/images/sui-cover.png)

# Expanding Claude Code

Skills, agents, hooks, plugins, and MCPs

---

<!-- _class: toc -->
<!-- _paginate: false -->

<div class="toc-left" style="background: url('assets/images/sui-cover.png') center/cover;">

# Topics

</div>

<div class="toc-right">

<div class="toc-item"><span class="toc-num">01</span><span class="toc-label">Skills</span></div>
<div class="toc-item"><span class="toc-num">02</span><span class="toc-label">AGENTS.md</span></div>
<div class="toc-item"><span class="toc-num">03</span><span class="toc-label">Hooks</span></div>
<div class="toc-item"><span class="toc-num">04</span><span class="toc-label">Plugins</span></div>
<div class="toc-item"><span class="toc-num">05</span><span class="toc-label">MCPs</span></div>
<div class="toc-item"><span class="toc-num">06</span><span class="toc-label">Context Impact</span></div>

</div>

---

<!-- _class: section-break -->
<!-- _paginate: false -->

![bg](assets/images/sui-cover.png)

# Skills

---

# What Are Skills

- A `SKILL.md` file -- YAML frontmatter + plain-text instructions
- Frontmatter `description` tells Claude **when** to use it
- Markdown body tells Claude **how**
- No compiled code, no runtime -- *just prose Claude follows*
- Live under `.claude/skills/`, `~/.claude/skills/`, or inside plugins

---

# Using Skills

- Invoke manually with `/skill-name`
- Or let Claude **auto-load** when description matches your task
- Full content loads only on invocation -- keeps context lean
- `disable-model-invocation: true` restricts to manual use
- `user-invocable: false` hides from `/` menu, allows auto-invocation

---

<!-- _class: list-right -->

<div class="content">

# Skill Examples

Built-in and plugin skills available out of the box.

</div>

<div class="cards">
<div class="card">

#### /batch

Parallel large-scale changes across worktrees.

</div>
<div class="card">

#### /claude-api

Building apps with the Anthropic SDK.

</div>
<div class="card">

#### /loop

Recurring prompt execution on an interval.

</div>
<div class="card">

#### /simplify

Three agents review changes for reuse, quality, and efficiency.

</div>
</div>

---

<!-- _class: section-break -->
<!-- _paginate: false -->

![bg](assets/images/sui-cover.png)

# AGENTS.md

---

<!-- _class: cols-2-center -->

# AGENTS.md

<div class="grid">
<div class="col">

<span class="category">WHAT IT IS</span>

### Role Catalog

A convention for cataloging reusable agent roles. Each role: system prompt, model preference, behavioral constraints.

</div>
<div class="col">

<span class="category">WHEN YOU NEED IT</span>

### Parallel Specialists

Frontend + contract agents simultaneously. Docs agent + code agent in parallel. Requires `AGENT_TEAMS` flag.

</div>
</div>

---

<!-- _class: section-break -->
<!-- _paginate: false -->

![bg](assets/images/sui-cover.png)

# Hooks

---

# What Are Hooks

- Event-driven handlers at specific **lifecycle points**
- Validate commands before execution
- Auto-format after edits
- Block dangerous operations
- JSON context passed to your handler on each event

---

<!-- _class: cols-4 -->

# Hook Handlers

<div class="grid">
<div class="col">

<span class="category">SHELL</span>

### Command

Run a shell script. Simplest handler type.

</div>
<div class="col">

<span class="category">NETWORK</span>

### HTTP

POST to a URL. For external service integration.

</div>
<div class="col">

<span class="category">AI DECISION</span>

### Prompt

LLM yes/no decision. Intelligent filtering.

</div>
<div class="col">

<span class="category">AUTONOMOUS</span>

### Agent

Subagent with tool access. Most powerful handler.

</div>
</div>

---

# Configuring Hooks

Define in `settings.json` under the `hooks` key:

- Specify an **event** (e.g. `PreToolUse`)
- Optional **matcher** regex (e.g. `"Bash"`)
- One or more **handlers**

**Key events:** SessionStart, UserPromptSubmit, PreToolUse, PostToolUse, Stop, PreCompact, Notification, SessionEnd *(25+ total)*

---

<!-- _class: section-break -->
<!-- _paginate: false -->

![bg](assets/images/sui-cover.png)

# Plugins

---

# What Are Plugins

- Bundle skills, commands, hooks, agents, and MCP servers
- **Installable, shareable, versioned** independently
- Published to marketplaces (Anthropic official or private GitHub repos)
- Namespace prevents conflicts: `/my-plugin:deploy`

---

# Plugin Anatomy

```
my-plugin/
  .claude-plugin/plugin.json   <- manifest
  skills/                      <- skill files
  commands/                    <- slash commands
  agents/                      <- agent definitions
  hooks/hooks.json             <- hook configurations
  .mcp.json                    <- MCP server configs
```

During development: `/reload-plugins` picks up changes without restarting.

---

<!-- _class: section-break -->
<!-- _paginate: false -->

![bg](assets/images/sui-cover.png)

# MCPs

---

# What Are MCPs

- *Model Context Protocol* -- an open standard for AI tool integration
- Think **USB-C for AI**
- Supported by Claude Code, ChatGPT, VS Code, Cursor, and more
- Build a server once, integrate everywhere
- Two transports: **stdio** (local) and **HTTP** (remote)

---

# Using MCPs

```bash
# Remote HTTP server
claude mcp add --transport http stripe https://mcp.stripe.com

# Local stdio server
claude mcp add --transport stdio airtable -- npx -y airtable-mcp-server
```

**Scopes:** local (private), project (shared in VCS), user (all projects)

Common: Chrome DevTools, Linear, Notion, custom API wrappers.

---

<!-- _class: cols-4 -->

# Context Window Impact

<div class="grid">
<div class="col">

<span class="category">SKILLS</span>

### ~2% Window

Descriptions loaded at start. Full content only on invocation.

</div>
<div class="col">

<span class="category">HOOKS</span>

### Minimal

Run externally. Low impact unless injecting messages.

</div>
<div class="col">

<span class="category">MCP TOOLS</span>

### Adds Up

Definitions added every turn. 5 servers x 20 tools = significant.

</div>
<div class="col">

<span class="category">PLUGINS</span>

### All Layers

Combine skills, hooks, MCPs simultaneously. Be intentional.

</div>
</div>

---

<!-- _class: quote -->
<!-- _paginate: false -->

![bg](assets/images/sui-cover.png)

Enable what you need, disable what you do not. The system is powerful because every piece is optional and modular.
