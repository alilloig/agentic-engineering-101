---
marp: true
paginate: true
footer: "Sui"
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
section::after { color: #FFFFFF; font-size: 12px; font-weight: 600; background: #4DA2FF; border-radius: 2px; padding: 2px 8px; }

/* Footer & Header */
section footer { color: #8B8B8B; font-size: 14px; position: absolute; bottom: 24px; left: 60px; }
section footer::before { content: ''; display: inline-block; width: 14px; height: 18px; background: url("data:image/svg+xml,%3Csvg width='300' height='384' viewBox='0 0 300 384' fill='none' xmlns='http://www.w3.org/2000/svg'%3E %3Cpath fill-rule='evenodd' clip-rule='evenodd' d='M240.057 159.914C255.698 179.553 265.052 204.39 265.052 231.407C265.052 258.424 255.414 284.019 239.362 303.768L237.971 305.475L237.608 303.31C237.292 301.477 236.929 299.613 236.502 297.749C228.46 262.421 202.265 232.134 159.148 207.597C130.029 191.071 113.361 171.195 108.985 148.586C106.157 133.972 108.258 119.294 112.318 106.717C116.379 94.1569 122.414 83.6187 127.549 77.2831L144.328 56.7754C147.267 53.1731 152.781 53.1731 155.719 56.7754L240.073 159.914H240.057ZM266.584 139.422L154.155 1.96703C152.007 -0.655678 147.993 -0.655678 145.845 1.96703L33.4316 139.422L33.0683 139.881C12.3868 165.555 0 198.181 0 233.698C0 316.408 67.1635 383.461 150 383.461C232.837 383.461 300 316.408 300 233.698C300 198.181 287.613 165.555 266.932 139.896L266.568 139.438L266.584 139.422ZM60.3381 159.472L70.3866 147.164L70.6868 149.439C70.9237 151.24 71.2239 153.041 71.5715 154.858C78.0809 189.001 101.322 217.456 140.173 239.496C173.952 258.724 193.622 280.828 199.278 305.064C201.648 315.176 202.059 325.129 201.032 333.835L200.969 334.372L200.479 334.609C185.233 342.05 168.09 346.237 149.984 346.237C86.4546 346.237 34.9484 294.826 34.9484 231.391C34.9484 204.153 44.4439 179.142 60.3065 159.44L60.3381 159.472Z' fill='%234DA2FF'/%3E %3C/svg%3E") no-repeat center/contain; margin-right: 5px; vertical-align: middle; }
section header { color: #4DA2FF; font-size: 14px; font-weight: 500; position: absolute; top: 24px; right: 60px; }

/* === GRID SYSTEM === */
section .grid { display: grid; gap: 24px; width: 100%; height: auto; }
section .col { display: flex; flex-direction: column; border-top: 1px dashed #3A3A3A; padding-top: 16px; }
section .col h3 { margin-bottom: 8px; }
section .col p { font-size: 18px; margin: 0; }

/* Category label */
section .category { display: inline-flex; align-items: center; gap: 6px; font-size: 11px; font-weight: 600; letter-spacing: 0.08em; text-transform: uppercase; color: #8B8B8B; font-family: 'Inter', monospace; margin-bottom: 8px; }
section .category::before { content: ''; display: inline-block; width: 8px; height: 8px; background: #4DA2FF; flex-shrink: 0; }

/* Stats */
section .stat { color: #FFFFFF; font-size: 48px; font-weight: 700; line-height: 1; margin-bottom: 4px; }
section .stat-label { color: #8B8B8B; font-size: 16px; }
section .stat-large { color: #FFFFFF; font-size: 72px; font-weight: 700; line-height: 1; margin-bottom: 8px; }

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
section.cover-gradient footer { display: none; }
section.cover-gradient::after { display: block !important; content: '' !important; position: absolute; bottom: 40px; right: 60px; width: 140px; height: 55px; background: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 220 80'%3E%3Cg transform='translate(0,2) scale(0.19)'%3E%3Cpath fill-rule='evenodd' clip-rule='evenodd' d='M240.057 159.914C255.698 179.553 265.052 204.39 265.052 231.407C265.052 258.424 255.414 284.019 239.362 303.768L237.971 305.475L237.608 303.31C237.292 301.477 236.929 299.613 236.502 297.749C228.46 262.421 202.265 232.134 159.148 207.597C130.029 191.071 113.361 171.195 108.985 148.586C106.157 133.972 108.258 119.294 112.318 106.717C116.379 94.1569 122.414 83.6187 127.549 77.2831L144.328 56.7754C147.267 53.1731 152.781 53.1731 155.719 56.7754L240.073 159.914H240.057ZM266.584 139.422L154.155 1.96703C152.007-0.655678 147.993-0.655678 145.845 1.96703L33.4316 139.422L33.0683 139.881C12.3868 165.555 0 198.181 0 233.698C0 316.408 67.1635 383.461 150 383.461C232.837 383.461 300 316.408 300 233.698C300 198.181 287.613 165.555 266.932 139.896L266.568 139.438L266.584 139.422ZM60.3381 159.472L70.3866 147.164L70.6868 149.439C70.9237 151.24 71.2239 153.041 71.5715 154.858C78.0809 189.001 101.322 217.456 140.173 239.496C173.952 258.724 193.622 280.828 199.278 305.064C201.648 315.176 202.059 325.129 201.032 333.835L200.969 334.372L200.479 334.609C185.233 342.05 168.09 346.237 149.984 346.237C86.4546 346.237 34.9484 294.826 34.9484 231.391C34.9484 204.153 44.4439 179.142 60.3065 159.44L60.3381 159.472Z' fill='white'/%3E%3C/g%3E%3Ctext x='72' y='57' font-family='Inter,sans-serif' font-size='52' font-weight='400' fill='white'%3ESui%3C/text%3E%3C/svg%3E") no-repeat center/contain; color: transparent; font-size: 0; padding: 0; border-radius: 0; z-index: 1; }

/* === LAYOUT: section-break (decorative filler — title hidden) === */
section.section-break { display: flex; flex-direction: column; justify-content: center; align-items: center; text-align: center; }
section.section-break h1 { display: none; }
section.section-break footer, section.section-break::after { display: none; }

/* === LAYOUT: chapter — topic/section intro, title top-left === */
section.chapter { display: flex; flex-direction: column; justify-content: flex-start; align-items: flex-start; padding-top: 60px; color: #FFFFFF; }
section.chapter h1 { font-size: 48px; font-weight: 700; color: #FFFFFF; letter-spacing: -0.02em; position: relative; z-index: 1; }
section.chapter p { font-size: 22px; color: rgba(255,255,255,0.85); max-width: 60%; position: relative; z-index: 1; }
section.chapter footer, section.chapter::after { display: none; }

/* === LAYOUT: quote === */
section.quote { display: flex; flex-direction: column; justify-content: center; align-items: center; text-align: center; padding: 80px 120px; }
section.quote p { font-size: 36px; font-weight: 500; color: #FFFFFF; line-height: 1.4; max-width: 900px; position: relative; z-index: 1; }
section.quote footer, section.quote::after { display: none; }

/* === LAYOUT: content === */
section.content { display: flex; flex-direction: column; justify-content: flex-start; align-items: flex-start; }
section.content h1 { font-size: 42px; margin-bottom: 16px; }
section.content p { max-width: 45%; font-size: 20px; }

/* === COLUMN LAYOUTS === */
section.cols-4 .grid { grid-template-columns: repeat(4, 1fr); margin-top: 24px; }
section.cols-3 .grid { grid-template-columns: repeat(3, 1fr); margin-top: 24px; }
section.cols-2-center { text-align: center; }
section.cols-2-center h1 { text-align: center; width: 100%; }
section.cols-2-center .grid { grid-template-columns: repeat(2, 1fr); margin-top: 24px; text-align: center; }
section.cols-2-center .col { align-items: center; }

section.fullbleed { padding: 0; }
section.fullbleed img { width: 100%; height: 100%; object-fit: cover; }

/* === STATS LAYOUTS === */
section.cols-4-stats .grid { grid-template-columns: repeat(4, 1fr); margin-top: 24px; }
section.cols-4-stats .col { text-align: left; border-top: 1px dashed #3A3A3A; padding-top: 16px; }
section.cols-4-stats .stat { font-size: 48px; color: #FFFFFF; }

/* === SPLIT/LIST LAYOUTS === */
section.split-right { display: flex; flex-direction: column; align-items: flex-end; justify-content: flex-start; text-align: left; }
section.split-right h1, section.split-right p { max-width: 55%; }

section.list-right { display: grid; grid-template-columns: 1fr 1fr; gap: 40px; align-items: start; }
section.list-right .content { display: flex; flex-direction: column; justify-content: center; height: 100%; }
section.list-right .cards { display: flex; flex-direction: column; gap: 8px; }

/* Utility */
section .no-border { border-top: none !important; padding-top: 0 !important; }
section .accent { color: #4DA2FF; }
section .badge { display: inline-block; background: rgba(77,162,255,0.15); color: #4DA2FF; padding: 4px 12px; border-radius: 16px; font-size: 14px; font-weight: 500; }
</style>

<!-- _class: lead -->
<!-- _paginate: false -->

# Agentic Engineering 101

Build with Claude Code, not against it

---

<!-- SECTION 1: ML BASICS -->

<!-- _class: chapter -->
<!-- _paginate: false -->

![bg](assets/images/sui-cover.png)

# 01 — ML Basics

---

# Language models process tokens, not words — and every token costs you budget

Models break text into subword chunks. "unhappiness" becomes three tokens; "the" is always one. The practical heuristic:

- **1 token ≈ 4 characters** of English text, or ~0.75 words
- A 1,000-word document ≈ 1,300 tokens
- Every prompt, file read, tool response, and conversation turn is measured in tokens

You are always budgeting. Understanding tokens is step one.

---

<!-- _class: cols-2-center -->

# Self-attention lets Claude hold your entire project in focus — until it can't

<div class="grid">
<div class="col">

<span class="category">HOW IT WORKS</span>

### Attention computes relevance

When Claude encounters "it" in a sentence, self-attention determines whether "it" means "the server" or "the error" by examining relationships between all tokens in context.

This is what makes Claude useful as a coding agent — it holds your instructions, the file it read, the tool result, and your message all at once.

</div>
<div class="col">

<span class="category">THE COST</span>

### Attention is not free

The more tokens in context, the more relationships the model evaluates. As context grows, the ability to attend sharply to any single detail degrades.

This is the fundamental tension you will manage every time you work with Claude Code.

</div>
</div>

---

# The context window is working memory: what's not inside doesn't exist

The total number of tokens a model can process in a single conversation — input and output combined.

- Unlike human memory, there is no background recall
- Once the window is full, the oldest content must be dropped or summarized
- Agentic loops compound the cost: each "think, act, observe" cycle adds to the running total
- An agent that calls ten tools in a loop consumes far more context than a single-turn question

---

<!-- _class: cols-3 -->

# A 1M token window holds an entire medium-sized codebase in one conversation

<div class="grid">
<div class="col">

<span class="category">OPUS 4.6</span>

### 1M tokens

128k max output

$5 / $25 per MTok

May 2025 cutoff

</div>
<div class="col">

<span class="category">SONNET 4.6</span>

### 1M tokens

64k max output

$3 / $15 per MTok

Aug 2025 cutoff

</div>
<div class="col">

<span class="category">HAIKU 4.5</span>

### 200K tokens

64k max output

$1 / $5 per MTok

Feb 2025 cutoff

</div>
</div>

---

<!-- _class: cols-2-center -->

# Context rot degrades output quality as the window fills with noise

<div class="grid">
<div class="col">

<span class="category">SYMPTOMS</span>

### You'll recognize it

- Vague or generic outputs
- Forgets earlier instructions
- Repeats itself
- Confidently references subtly wrong details
- Blends information from a crowded context

</div>
<div class="col">

<span class="category">MITIGATION</span>

### Three strategies

- **Compaction** — auto-summarize history to reclaim space (`CLAUDE_AUTOCOMPACT_PCT_OVERRIDE`)
- **Scoping** — read only what you need, use targeted searches
- **Fresh sessions** — a clean window restores full attention budget

</div>
</div>

---

<!-- SECTION 2: INSTALLATION -->

<!-- _class: chapter -->
<!-- _paginate: false -->

![bg](assets/images/sui-cover.png)

# 02 — Installation

---

<!-- _class: cols-3 -->

# Claude Code runs across three surfaces: CLI, Desktop, and Chrome

<div class="grid">
<div class="col">

<span class="category">TERMINAL</span>

### CLI

The core tool. Runs in any terminal on macOS, Windows, or Linux. Where agentic sessions happen.

</div>
<div class="col">

<span class="category">GUI</span>

### Desktop App

Visual diffs, parallel sessions, cloud tasks, and scheduling. Same engine as the CLI.

</div>
<div class="col">

<span class="category">BROWSER</span>

### Chrome Extension

Connects Claude Code to your browser for live debugging, testing, and automation.

</div>
</div>

---

<!-- _class: cols-2-center -->

# The native binary installs in one command and auto-updates silently

<div class="grid">
<div class="col">

<span class="category">RECOMMENDED</span>

### Native install

```bash
curl -fsSL https://claude.ai/install.sh | bash
```

Self-contained binary at `~/.local/bin/claude`. Auto-updates in the background.

</div>
<div class="col">

<span class="category">ALTERNATIVE</span>

### Homebrew

```bash
brew install --cask claude-code
```

Does **not** auto-update. Run `brew upgrade claude-code` periodically.

</div>
</div>

---

# Claude Desktop provides visual diffs, parallel sessions, and cloud tasks

Download for macOS (Intel and Apple Silicon):

- Open the `.dmg`, drag to Applications, launch
- Sign in with your Claude account (Pro, Max, Teams, or Enterprise required)
- Click the **Code** tab to start a coding session
- Shares your `CLAUDE.md`, settings, and MCP servers with the CLI

---

# The Chrome extension turns your browser into a programmable testing tool

Install from the Chrome Web Store, then connect:

```bash
claude --chrome
```

- **Live debugging** — read console errors, inspect DOM, fix the code
- **Web app testing** — submit forms, verify flows, check regressions
- **Authenticated access** — interact with sites you're logged into (Google Docs, Notion, internal tools)
- **Task automation** — repetitive browser workflows handled programmatically

---

<!-- _class: cols-3 -->

# Verify all three before moving on

<div class="grid">
<div class="col">

<span class="category">CLI</span>

### Version check

```bash
claude --version
claude doctor
```

Confirms binary and auth are working.

</div>
<div class="col">

<span class="category">DESKTOP</span>

### Sign-in test

Open the app, sign in, verify the Code tab loads.

</div>
<div class="col">

<span class="category">CHROME</span>

### Toolbar check

Claude icon in toolbar. Run `/chrome` in a session to verify the connection.

</div>
</div>

---

<!-- SECTION 3: BASIC USAGE -->

<!-- _class: chapter -->
<!-- _paginate: false -->

![bg](assets/images/sui-cover.png)

# 03 — Basic Usage

---

# Every interaction consumes tokens from a finite context budget

Prompts, tool definitions, file reads, tool results, conversation history — all of it accumulates. Claude Code operates on models with up to 1M tokens, which sounds enormous until a few large files and a long conversation fill it up.

This constraint shapes everything: concise prompts leave more room for code, and well-structured CLAUDE.md files deliver instructions without burning tokens on noise.

---

<!-- _class: cols-3 -->

# Five prompting habits maximize the signal-to-token ratio

<div class="grid">
<div class="col">

<span class="category">TIPS 1-2</span>

### Lead with intent

"Add validation to the signup form" beats a long preamble.

### Be specific

"Fix the test in `auth.test.ts`" beats "fix the tests."

</div>
<div class="col">

<span class="category">TIPS 3-4</span>

### Skip filler

"Please kindly help me with" wastes tokens. State the task.

### One task per prompt

Compound requests increase drift. Break them up or use plan mode.

</div>
<div class="col">

<span class="category">TIP 5</span>

### Reference files directly

Mention the file path rather than describing where it might be.

Every token in your prompt is one less token for code and reasoning.

</div>
</div>

---

<!-- _class: cols-2-center -->

# CLAUDE.md gives Claude persistent memory that survives between sessions

<div class="grid">
<div class="col">

<span class="category">PURPOSE</span>

### Persistent instructions

A markdown file read at the start of every session. Tells Claude what this project is and how you want things done.

</div>
<div class="col">

<span class="category">CONTENTS</span>

### What goes in it

Project structure, coding conventions, build commands, architectural decisions, workflow constraints. Keep under 200 lines.

</div>
</div>

---

<!-- _class: cols-3 -->

# Three scopes control whose instructions Claude follows

<div class="grid">
<div class="col">

<span class="category">SHARED</span>

### Project

`./CLAUDE.md` or `./.claude/CLAUDE.md`

Committed to source control. Project-specific standards the whole team follows.

</div>
<div class="col">

<span class="category">PERSONAL</span>

### User

`~/.claude/CLAUDE.md`

Your preferences across all projects on your machine.

</div>
<div class="col">

<span class="category">ENFORCED</span>

### Managed

System-level, set by IT.

Organization-wide instructions that cannot be overridden. Highest precedence.

</div>
</div>

---

# Settings cascade through four levels from managed policy to personal defaults

| Scope | Location | Shared? | Purpose |
|-------|----------|---------|---------|
| **Managed** | System-level (MDM) | By IT | Org-wide policies, cannot override |
| **Local** | `.claude/settings.local.json` | No | Machine-specific overrides |
| **Project** | `.claude/settings.json` | Yes | Team-shared repo settings |
| **User** | `~/.claude/settings.json` | No | Personal defaults |

Use `settings.local.json` for machine-specific overrides — it is automatically gitignored.

---

<!-- _class: cols-3 -->

# Three settings shape most of your daily experience

<div class="grid">
<div class="col">

<span class="category">SECURITY</span>

### permissions

Allow or deny tools and commands.

`Bash(npm run test *)` in the `allow` list.

</div>
<div class="col">

<span class="category">ENVIRONMENT</span>

### env

Environment variables applied every session.

`CLAUDE_AUTOCOMPACT_PCT_OVERRIDE`.

</div>
<div class="col">

<span class="category">QUALITY</span>

### effortLevel

`"low"`, `"medium"`, or `"high"` — persists across sessions.

Supported on Opus 4.6 and Sonnet 4.6.

</div>
</div>

---

# Five best practices prevent the most common Claude Code mistakes

1. **Start every new task in plan mode** — prevents more wasted work than anything else
2. **Keep CLAUDE.md under 200 lines** — split with imports or `.claude/rules/`
3. **Be explicit about boundaries** — "Do not modify files outside `src/`"
4. **Use `/compact` when context gets heavy** — summarizes history, re-reads CLAUDE.md
5. **Commit `.claude/settings.json` and CLAUDE.md** — they are team resources

---

<!-- _class: cols-2-center -->

# /init bootstraps a starter CLAUDE.md; plan mode prevents premature editing

<div class="grid">
<div class="col">

<span class="category">BOOTSTRAP</span>

### /init

Analyzes your codebase and generates a starter CLAUDE.md. If one exists, suggests improvements. A bootstrap, not a finished product.

</div>
<div class="col">

<span class="category">WORKFLOW</span>

### Plan mode

Claude reads and proposes but does not edit. Review, give feedback, then execute. Cycle with `Shift+Tab` or start with `--permission-mode plan`.

</div>
</div>

---

# Plan mode is the single most important workflow habit in Claude Code

**Always use plan mode when doing something new.**

Without it, Claude jumps straight into editing. Wrong approach means wasted tokens and changes to undo. Plan mode costs almost nothing and catches misalignment before damage is done.

**Plan → Review → Execute.**

Use for: new features, unfamiliar code, complex debugging. Skip only for trivial tasks.

---

<!-- _class: cols-4 -->

# Four permission modes trade safety for speed — choose based on trust

<div class="grid">
<div class="col">

<span class="category">DEFAULT</span>

### default

Prompts for every edit and command. Safest while learning.

</div>
<div class="col">

<span class="category">BALANCED</span>

### acceptEdits

Auto-approves edits, prompts for shell commands. Best for daily work.

</div>
<div class="col">

<span class="category">SMART</span>

### auto

Classifier auto-approves safe ops, prompts for risky ones. Team plans only.

</div>
<div class="col">

<span class="category">LOCKED</span>

### dontAsk

Auto-denies everything not in allowlist. For CI and locked-down envs.

</div>
</div>

---

<!-- SECTION 4: DAY 0 SETUP -->

<!-- _class: chapter -->
<!-- _paginate: false -->

![bg](assets/images/sui-cover.png)

# 04 — Day 0 Setup

---

# Ten minutes of plugin setup saves hours of manual configuration later

The marketplace has 100+ entries — choosing the right starting set matters more than installing everything.

- Plugins are organized by function: project setup, code quality, git workflow, output styles
- Install what you need, skip what you don't
- Each plugin fills a specific gap that Claude cannot cover on its own

---

<!-- _class: cols-2-center -->

# Two Anthropic plugins handle project analysis and memory management

<div class="grid">
<div class="col">

<span class="category">55K+ INSTALLS</span>

### Claude Code Setup

Analyzes your codebase and recommends automations — hooks, skills, MCPs, subagents — tailored to your stack.

Claude is surprisingly weak at configuring itself without guidance. This plugin provides value nothing else covers.

</div>
<div class="col">

<span class="category">92K+ INSTALLS</span>

### Claude MD Management

Audits and improves CLAUDE.md files. `/revise-claude-md` captures session learnings as reviewable diffs.

Run at the end of any productive session to prevent knowledge loss. Addresses a problem nothing else solves.

</div>
</div>

---

<!-- _class: cols-3 -->

# Three code quality plugins catch bugs, simplify code, and block vulnerabilities

<div class="grid">
<div class="col">

<span class="category">169K+ INSTALLS</span>

### Code Review

Five independent agents analyze PR changes from different angles. Each finding gets a confidence score; only high-confidence issues are posted.

</div>
<div class="col">

<span class="category">140K+ INSTALLS</span>

### Code Simplifier

Autonomous agent that refines recently modified code for clarity and maintainability — reducing nesting, improving naming, eliminating redundancy.

</div>
<div class="col">

<span class="category">87K+ INSTALLS</span>

### Security Guidance

Pre-tool hook that scans for dangerous patterns — command injection, XSS, unsafe deserialization — and warns before edits proceed.

</div>
</div>

---

<!-- _class: cols-2-center -->

# Commit Commands automates git workflow with convention-matching messages

<div class="grid">
<div class="col">

<span class="category">86K+ INSTALLS</span>

### What it does

AI-generated commit messages that match your repo's conventions. Automates commit, push, and PR creation in a single flow.

Requires GitHub CLI (`gh`) installed and authenticated.

</div>
<div class="col">

<span class="category">OUTPUT STYLES</span>

### Learning modes

**Explanatory** (35k+) — adds 2-3 educational insights about implementation choices during code generation.

**Learning** (23k+) — pauses at decision points and asks you to write 5-10 lines yourself.

</div>
</div>

---

<!-- SECTION 5: EXPANDING CLAUDE CODE -->

<!-- _class: chapter -->
<!-- _paginate: false -->

![bg](assets/images/sui-cover.png)

# 05 — Expanding Claude Code

---

<!-- _class: cols-2-center -->

# Skills are just markdown files — no code, no runtime, no compilation

<div class="grid">
<div class="col">

<span class="category">STRUCTURE</span>

### SKILL.md files

YAML frontmatter + prose instructions. The frontmatter says *when* to use it; the body says *how*.

Lives in `.claude/skills/`, `~/.claude/skills/`, or inside plugins.

</div>
<div class="col">

<span class="category">USAGE</span>

### Invoke or auto-match

Type `/skill-name` or let Claude load automatically when the description matches.

`disable-model-invocation: true` restricts to manual-only. `user-invocable: false` hides from the `/` menu.

</div>
</div>

---

# Built-in skills cover batch operations, debugging, and code quality

- **`/batch`** — parallel large-scale changes across worktrees
- **`/claude-api`** — building apps with the Anthropic SDK
- **`/debug`** — session log analysis
- **`/loop`** — recurring prompt execution on an interval
- **`/simplify`** — three parallel agents review recent changes for reuse, quality, and efficiency

Plugins add domain-specific skills on top — a code-review plugin might check error handling, security, and test coverage on every review.

---

<!-- _class: cols-2-center -->

# AGENTS.md catalogs reusable specialist roles for parallel team workflows

<div class="grid">
<div class="col">

<span class="category">WHAT IT IS</span>

### A convention, not a feature

A cast list of specialist agents — each with a system prompt, model preference, and behavioral constraints.

Reference entries when spawning agent teams.

</div>
<div class="col">

<span class="category">WHEN TO USE IT</span>

### Parallel specialists

A frontend agent and a contract agent working simultaneously. A docs agent updating documentation while a code agent implements.

Requires `CLAUDE_CODE_EXPERIMENTAL_AGENT_TEAMS=1`.

</div>
</div>

---

# Hooks fire at lifecycle events to validate, format, and block automatically

Event-driven handlers at specific lifecycle points:

- **`PreToolUse`** — validate or block before a tool runs (e.g., deny `rm -rf`)
- **`PostToolUse`** — auto-format after edits, log results
- **`SessionStart`** / **`SessionEnd`** — setup and teardown
- **`UserPromptSubmit`** — transform or validate user input
- **`Stop`** — run checks before Claude declares it's done

Four handler types: **command** (shell), **HTTP** (POST), **prompt** (LLM yes/no), **agent** (subagent with tools).

---

<!-- _class: cols-2-center -->

# Plugins bundle skills, hooks, agents, and MCPs into shareable packages

<div class="grid">
<div class="col">

<span class="category">STRUCTURE</span>

### Plugin anatomy

`.claude-plugin/plugin.json` manifest plus directories: `skills/`, `commands/`, `agents/`, `hooks/`, `.mcp.json`.

The manifest `name` becomes the namespace prefix (e.g., `/my-plugin:deploy`).

</div>
<div class="col">

<span class="category">DISTRIBUTION</span>

### Install and manage

Plugins install from marketplaces — official Anthropic and private GitHub repos.

During development, `/reload-plugins` picks up changes without restarting.

</div>
</div>

---

# MCP connects Claude to external services through a universal protocol

MCP (Model Context Protocol) is an open standard — think USB-C for AI. Claude Code, ChatGPT, VS Code, and Cursor all support it.

```bash
claude mcp add --transport http stripe https://mcp.stripe.com
claude mcp add --transport stdio airtable -- npx -y airtable-mcp-server
```

Two transports: **stdio** (local) and **HTTP** (remote). Three scopes: `local` (private), `project` (shared), `user` (all projects).

---

# Every extension consumes context — enable what you need, disable what you don't

- **Skills** — load descriptions (~2% of window); full content on invocation
- **Hooks** — run externally with minimal context impact unless they inject messages
- **MCP tools** — add definitions to every turn (5 servers × 20 tools adds up)
- **Plugins** — combine all layers simultaneously

Use `disable-model-invocation: true` on manual skills. Disconnect unused MCP servers. Run `/context` to check budget. The system is powerful because every piece is optional and modular.

---

<!-- _class: lead -->
<!-- _paginate: false -->

# You understand the engine, the tools, and the extension points

Now go build something.
