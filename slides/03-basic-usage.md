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

/* Stats */
section .stat { color: #FFFFFF; font-size: 48px; font-weight: 700; line-height: 1; margin-bottom: 4px; }
section .stat-label { color: #8B8B8B; font-size: 16px; }

/* Cards */
section .card { background: #0A0A0A; border: 1px solid #1A1A1A; border-radius: 8px; padding: 16px 20px; margin-bottom: 8px; }
section .card h4 { color: #FFFFFF; margin: 0 0 4px 0; }
section .card p { margin: 0; font-size: 16px; }

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

# Basic Claude Code Usage

Context, prompting, configuration, and workflow

---

<!-- _class: toc -->
<!-- _paginate: false -->

<div class="toc-left" style="background: url('assets/images/sui-cover.png') center/cover;">

# Topics

</div>

<div class="toc-right">

<div class="toc-item"><span class="toc-num">01</span><span class="toc-label">Context in Practice</span></div>
<div class="toc-item"><span class="toc-num">02</span><span class="toc-label">Concise Prompting</span></div>
<div class="toc-item"><span class="toc-num">03</span><span class="toc-label">CLAUDE.md</span></div>
<div class="toc-item"><span class="toc-num">04</span><span class="toc-label">Settings</span></div>
<div class="toc-item"><span class="toc-num">05</span><span class="toc-label">Plan Mode & Permissions</span></div>

</div>

---

# Context Window in Practice

- Every prompt, tool definition, file read = tokens from your budget
- Up to *1M tokens* sounds enormous
- A few large files + long conversation fills it up fast
- This constraint shapes **everything** below
- Concise prompts leave more room for code and reasoning

---

<!-- _class: section-break -->
<!-- _paginate: false -->

![bg](assets/images/sui-cover.png)

# Concise Prompting

---

<!-- _class: cols-2-center -->

# Effective vs Wasteful

<div class="grid">
<div class="col">

<span class="category">DO THIS</span>

### Direct and Specific

"Add input validation to the signup form"

"Fix the failing test in `auth.test.ts`"

One task per prompt. Reference file paths directly.

</div>
<div class="col">

<span class="category">NOT THIS</span>

### Verbose and Vague

"Open the signup form file and look at the fields and then add validation"

"Fix the tests"

Compound requests. "Please kindly help me with..."

</div>
</div>

---

<!-- _class: section-break -->
<!-- _paginate: false -->

![bg](assets/images/sui-cover.png)

# CLAUDE.md

---

# What Is CLAUDE.md

- A markdown file read at the **start of every session**
- Tells Claude what this project is and how you want things done
- Contains: project structure, coding conventions, build commands
- Also: architectural decisions, workflow constraints
- Keep under **200 lines** -- split with `@path` imports beyond that

---

<!-- _class: cols-3 -->

# CLAUDE.md Scopes

<div class="grid">
<div class="col">

<span class="category">PROJECT</span>

### Shared Standards

`./CLAUDE.md` or `./.claude/CLAUDE.md`

Committed to source control. Project-specific conventions.

</div>
<div class="col">

<span class="category">USER</span>

### Personal Prefs

`~/.claude/CLAUDE.md`

Your preferences across all projects on your machine.

</div>
<div class="col">

<span class="category">MANAGED</span>

### Org-Wide Policy

System-level, set by IT.

Cannot be overridden. Organization-wide instructions.

</div>
</div>

---

<!-- _class: section-break -->
<!-- _paginate: false -->

![bg](assets/images/sui-cover.png)

# Settings

---

# Settings Scopes

| Scope | Location | Shared? | Purpose |
|-------|----------|---------|---------|
| **Managed** | System-level policies | By IT | Org-wide, cannot override |
| **Local** | `.claude/settings.local.json` | No | Machine-specific overrides |
| **Project** | `.claude/settings.json` | Yes | Team-shared repo settings |
| **User** | `~/.claude/settings.json` | No | Personal defaults |

Higher scopes take precedence.

---

<!-- _class: cols-3 -->

# Key Settings

<div class="grid">
<div class="col">

<span class="category">PERMISSIONS</span>

### Allow / Deny

Control which tools and commands Claude can use. E.g. `Bash(npm run test *)` in the allow list.

</div>
<div class="col">

<span class="category">ENVIRONMENT</span>

### env Variables

Set environment variables applied every session. Useful for API keys and feature flags.

</div>
<div class="col">

<span class="category">EFFORT</span>

### effortLevel

`"low"`, `"medium"`, or `"high"`. Persists across sessions on Opus 4.6 and Sonnet 4.6.

</div>
</div>

---

<!-- _class: list-right -->

<div class="content">

# Best Practices

The habits that prevent the most wasted work.

</div>

<div class="cards">
<div class="card">

#### Start in Plan Mode

Prevents more wasted work than anything else. Always for new tasks.

</div>
<div class="card">

#### Keep CLAUDE.md Concise

Under 200 lines. Split with imports or `.claude/rules/` when it grows.

</div>
<div class="card">

#### Set Explicit Boundaries

"Do not modify files outside `src/`" beats hoping Claude infers limits.

</div>
<div class="card">

#### Use /compact

Summarizes history and re-reads CLAUDE.md fresh when context gets heavy.

</div>
</div>

---

# The /init Command

- Analyzes your codebase, generates a starter CLAUDE.md
- Discovers build commands, test instructions, conventions
- If CLAUDE.md exists, suggests improvements instead of overwriting
- **Use it**: first time in a new repo
- A bootstrap, not a finished product -- refine afterward

---

<!-- _class: section-break -->
<!-- _paginate: false -->

![bg](assets/images/sui-cover.png)

# Plan Mode & Permissions

---

# What Is Plan Mode

- Prevents Claude from **editing source code**
- Claude reads files, explores the codebase, proposes a plan
- You review, give feedback, adjust scope
- Then let Claude proceed with implementation
- Toggle with **Shift+Tab** or start with `--permission-mode plan`

---

<!-- _class: quote -->
<!-- _paginate: false -->

![bg](assets/images/sui-cover.png)

Always use plan mode when doing something new. This is the single most important workflow habit in Claude Code.

---

<!-- _class: cols-2-center -->

# Permission Modes

<div class="grid">
<div class="col">

<span class="category">MORE CONTROL</span>

### Safer Options

**default** -- prompts for everything
**acceptEdits** -- auto-approves edits, prompts for commands
**auto** -- AI classifier approves safe ops

</div>
<div class="col">

<span class="category">LESS FRICTION</span>

### Faster Options

**dontAsk** -- auto-denies unless pre-allowed
**bypassPermissions** -- skips all prompts (dangerous)

</div>
</div>

---

# Choosing a Permission Mode

- **Daily work**: *acceptEdits*
- **New tasks**: *plan mode*
- **Team plans with AI safety**: *auto*
- **CI pipelines**: *dontAsk*
- **Only when confident**: *bypassPermissions*

Start with default or acceptEdits. Graduate as trust builds.
