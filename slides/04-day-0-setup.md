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

# Day 0 Setup

Essential plugins before writing any code

---

# Why Plugins First

- *10 minutes* of setup shapes how Claude works for you
- The marketplace has **100+ entries**
- Choosing the right starting set matters more than installing everything
- Three complementary plugins cover the essentials

---

<!-- _class: cols-3 -->

# The Starting Three

<div class="grid">
<div class="col">

<span class="category">SKILLS FRAMEWORK</span>

### Superpowers

*233k+ installs.* Composable skills for planning, TDD, debugging, brainstorming, and code review.

</div>
<div class="col">

<span class="category">AUTOMATION</span>

### Claude Code Setup

*55k+ installs.* Analyzes your codebase and recommends automations tailored to your stack.

</div>
<div class="col">

<span class="category">MEMORY</span>

### Claude MD Management

*92k+ installs.* Audits and improves CLAUDE.md files. Captures session learnings.

</div>
</div>

---

# Superpowers

- Teaches Claude **structured development methodologies**
- TDD: strict red-green-refactor -- tests must fail before implementation
- Debugging: root cause investigation before any fix
- Brainstorming: Socratic sessions that refine requirements before coding
- **Hard gate**: no implementation until design is approved
- Substantially replaces several standalone plugins

---

# Claude Code Setup

- Analyzes codebase in **read-only mode**
- Recommends hooks, skills, MCP servers, subagents, slash commands
- Tailored to your specific tech stack
- Claude is surprisingly weak at configuring itself without guidance
- Independent of Superpowers -- *unique value nothing else covers*

---

# Claude MD Management

- `/revise-claude-md` captures session learnings
- Discovered commands, code patterns, environment quirks
- Proposes updates as **reviewable diffs**
- Run at the end of any productive session
- Prevents knowledge loss between sessions

---

# Covered by Superpowers

| Plugin | Installs | Overlap |
|--------|----------|---------|
| Commit Commands | 86k+ | `finishing-a-development-branch` skill |
| Code Review | 169k+ | `requesting-code-review` (standalone = 5 parallel agents) |
| Code Simplifier | 140k+ | No direct equivalent |
| Security Guidance | 87k+ | No direct equivalent |
| Explanatory Output | 35k+ | Superseded by Learning Output |
| Learning Output | 23k+ | `brainstorming` partially overlaps |

---

<!-- _class: cols-2-center -->

# Notable Standalone Plugins

<div class="grid">
<div class="col">

<span class="category">GIT WORKFLOW</span>

### Commit Commands

Automates git commit, push, and PR workflows. AI-generated messages matching repo conventions. Requires `gh` CLI.

</div>
<div class="col">

<span class="category">PR ANALYSIS</span>

### Code Review

Five independent agents analyze PR changes from different angles. Each finding gets a confidence score.

</div>
</div>

---

<!-- _class: cols-2-center -->

# More Standalone Plugins

<div class="grid">
<div class="col">

<span class="category">CODE QUALITY</span>

### Code Simplifier

Autonomous agent refining recently modified code. Reduces nesting, improves naming, eliminates redundancy.

</div>
<div class="col">

<span class="category">SECURITY</span>

### Security Guidance

Pre-tool hook scanning for dangerous patterns. Command injection, XSS, unsafe deserialization.

</div>
</div>

---

# Install Checklist

1. **Superpowers** -- install first, covers the most ground
2. **Claude Code Setup** -- run once per project for automation recommendations
3. **Claude MD Management** -- run `/revise-claude-md` at end of productive sessions
4. Standalone plugins only if you need functionality Superpowers does not cover
