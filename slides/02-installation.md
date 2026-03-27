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

# Installation

CLI, Desktop app, and Chrome extension

---

<!-- _class: cols-3 -->

# Three Surfaces

<div class="grid">
<div class="col">

<span class="category">TERMINAL</span>

### CLI

Command-line tool for any terminal. Primary interface for agentic workflows.

</div>
<div class="col">

<span class="category">VISUAL</span>

### Desktop App

Visual diffs, side-by-side sessions, cloud sessions, scheduled tasks.

</div>
<div class="col">

<span class="category">BROWSER</span>

### Chrome Extension

Browser automation from within Claude Code sessions.

</div>
</div>

---

# CLI Prerequisites

- **macOS** 13.0+, **Windows** 10 1809+, **Linux** Ubuntu 20.04+
- 4 GB RAM minimum, internet connection
- Terminal: Bash, Zsh, PowerShell, or CMD
- Windows: install *Git for Windows* first
- **Paid Claude account** required (Pro, Max, Teams, or Enterprise)

---

# Installing the CLI

**Native install (recommended):**

```bash
curl -fsSL https://claude.ai/install.sh | bash
```

- Self-contained binary to `~/.local/bin/claude`
- **Auto-updates** in the background
- No Node.js dependency

---

<!-- _class: cols-2-center -->

# Alternative Install Methods

<div class="grid">
<div class="col">

<span class="category">HOMEBREW</span>

### macOS & Linux

```bash
brew install --cask claude-code
```

Does not auto-update. Run `brew upgrade claude-code` periodically.

</div>
<div class="col">

<span class="category">DEPRECATED</span>

### npm

```bash
npm install -g @anthropic-ai/claude-code
```

Slower, requires Node.js 18+, no auto-update. **Do not use for new installs.**

</div>
</div>

---

# Verifying the CLI

```bash
claude --version
# → 2.1.85 (Claude Code)

claude doctor
# → Diagnoses auth, auto-updates, system config
```

Start Claude Code in any project:

```bash
cd your-project
claude
```

Authenticate in browser on first launch.

---

# Claude Desktop for macOS

- Download from *claude.ai* -- supports Intel and Apple Silicon
- Drag to Applications, launch, sign in
- Click the **Code** tab for coding sessions
- Shares CLAUDE.md, settings, and MCP servers with the CLI
- Paid subscription required (Pro, Max, Teams, or Enterprise)

---

# Chrome Extension

1. Open *Claude in Chrome* on the Chrome Web Store
2. Click **Add to Chrome**, confirm permissions
3. Verify the icon appears in your toolbar

Works with Chrome and Edge. Requires extension *v1.0.36+* and Claude Code *v2.0.73+*.

---

<!-- _class: list-right -->

<div class="content">

# What Chrome Enables

Connect with `claude --chrome` or `/chrome` in a session.

</div>

<div class="cards">
<div class="card">

#### Live Debugging

Read console errors, inspect DOM, fix the code that caused them.

</div>
<div class="card">

#### Web App Testing

Submit forms, verify user flows, check for visual regressions.

</div>
<div class="card">

#### Authenticated Access

Interact with any site you are logged into -- no API connectors needed.

</div>
<div class="card">

#### Task Automation

Automate repetitive browser workflows and data extraction.

</div>
</div>

---

# Verification Checklist

1. **CLI**: `claude --version` shows a version number
2. **Desktop**: Claude app opens, sign in works, Code tab loads
3. **Chrome**: Claude icon in toolbar, `claude --chrome` connects

If anything fails: run `claude doctor` for automated diagnostics.
