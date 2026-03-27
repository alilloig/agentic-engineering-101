# Basic Claude Code Usage

## Context Window in Practice

Every prompt, tool definition, conversation turn, and file Claude reads consumes tokens from your context budget. Claude Code operates on models with up to 1M tokens, which sounds enormous until a few large files and a long conversation fill it up. This constraint shapes everything below: concise prompts leave more room for code; well-structured CLAUDE.md files deliver instructions without burning tokens on noise.

## Concise Prompting

### Why Brevity Matters

Every token in your prompt is one less token available for code context and reasoning. Shorter prompts produce better results.

### Tips for Effective Prompts

1. **Lead with intent.** "Add input validation to the signup form" beats "Open the signup form file and look at the form fields and then add some validation logic."
2. **Be specific about scope.** "Fix the failing test in `auth.test.ts`" is far better than "Fix the tests."
3. **Skip filler.** "Please kindly help me with" wastes tokens. Just state the task.
4. **One task per prompt.** Compound requests increase drift. Break them up or use plan mode first.
5. **Reference files directly.** Mention the file path rather than describing where it might be.

## CLAUDE.md

### What It Is

A markdown file that gives Claude Code persistent instructions, read at the start of every session. It tells Claude what this project is and how you want things done.

### What Goes in It

Project structure, coding conventions, build commands, architectural decisions, workflow constraints. This repository's CLAUDE.md is minimal -- project description, directory layout, content workflow. A mature global CLAUDE.md might add language conventions, documentation references, quality workflows, and plan mode rules. Keep each file under 200 lines; split with `@path` imports or `.claude/rules/` beyond that.

### User vs Project CLAUDE.md

- **Project** (`./CLAUDE.md` or `./.claude/CLAUDE.md`): Shared via source control. Project-specific standards.
- **User** (`~/.claude/CLAUDE.md`): Personal preferences across all projects on your machine.
- **Managed policy** (system-level, set by IT): Organization-wide instructions that cannot be overridden.

More specific scopes take precedence. Import external files with `@path/to/file` syntax to pull in docs without duplication.

## Settings

### User Settings vs Project Settings

Claude Code has four configuration scopes (highest to lowest precedence):

| Scope | Location | Shared? | Purpose |
|-------|----------|---------|---------|
| **Managed** | System-level policies (MDM, registry, or `managed-settings.json`) | By IT | Org-wide policies, cannot be overridden |
| **Local** | `.claude/settings.local.json` | No | Machine-specific overrides (gitignored) |
| **Project** | `.claude/settings.json` | Yes | Team-shared repo settings |
| **User** | `~/.claude/settings.json` | No | Personal defaults, all projects |

### Key Settings to Know

- **`permissions`**: Allow or deny tools/commands. E.g., `Bash(npm run test *)` in `allow`.
- **`env`**: Environment variables applied every session.
- **`effortLevel`**: `"low"`, `"medium"`, or `"high"` -- persists the effort level across sessions (supported on Opus 4.6 and Sonnet 4.6).

Use `settings.local.json` for machine-specific overrides like personal permission allowlists. It is automatically gitignored.

## Best Practices

- **Start every new task in plan mode.** This single habit prevents more wasted work than anything else.
- **Keep CLAUDE.md under 200 lines.** Split with imports or `.claude/rules/` when it grows.
- **Be explicit about boundaries.** "Do not modify files outside `src/`" beats hoping Claude infers limits.
- **Use `/compact` when context gets heavy.** It summarizes history and re-reads CLAUDE.md fresh.
- **Commit `.claude/settings.json` and CLAUDE.md.** They are team resources. Keep `settings.local.json` personal.

## The /init Command

### What It Does

Analyzes your codebase and generates a starter CLAUDE.md with build commands, test instructions, and conventions it discovers. If a CLAUDE.md exists, it suggests improvements rather than overwriting.

### When to Use It

First time in a new repo. You get a working CLAUDE.md in seconds, then refine it with what Claude cannot discover -- architectural decisions, team conventions, workflow rules. A bootstrap, not a finished product.

## Plan Mode

### What It Is

Plan mode prevents Claude from editing your source code. Claude reads files, explores the codebase, runs exploratory commands (with your approval), and proposes a plan -- but does not modify any files. You review, give feedback, adjust scope, then let Claude proceed. Cycle to it with `Shift+Tab` (which rotates through modes) or start directly with `--permission-mode plan`.

### Why You Should Always Use It for New Tasks

**Always use plan mode when doing something new.** This is the single most important workflow habit in Claude Code.

The workflow: **Plan -> Review -> Execute.**

Without it, Claude jumps straight into editing. Wrong approach means wasted tokens and changes to undo. Plan mode costs almost nothing and catches misalignment before damage is done. Use it for new features, unfamiliar code, complex debugging -- anything where you are not certain of the approach. Skip only for trivial tasks.

## Permission Modes

### Overview

Claude Code asks permission before editing files or running commands. The permission mode controls how much you get prompted. Set it with `--permission-mode` at startup or cycle through modes with `Shift+Tab`.

### bypassPermissions

Launched with `--dangerously-skip-permissions`. Skips all prompts -- Claude edits and runs commands without asking. Fast but risky: unintended file changes happen silently, destructive commands execute without confirmation. The flag name includes "dangerously" for a reason.

### acceptEdits

Auto-approves file edits but still prompts for shell commands. A solid balance: no friction on edits, but a safety net for commands with side effects.

### auto

A background classifier reviews each action and auto-approves safe operations while prompting for risky ones. Available on Team plans with Sonnet 4.6 or Opus 4.6. A middle ground between acceptEdits and bypassPermissions.

### dontAsk

Auto-denies every tool not explicitly allowed in your permission rules. Suitable for CI pipelines and locked-down environments where only pre-approved operations should run.

### Choosing Between Them

Start with **default mode** or **acceptEdits**. Default is safest while learning; acceptEdits removes edit friction once you trust the workflow. **auto** adds intelligent safety checks without manual prompting. Graduate to **bypassPermissions** only when confident in your CLAUDE.md and allowlists. Even experienced users disable it for unfamiliar repos.

The recommendation: **acceptEdits for daily work, plan mode for new tasks, auto if your plan supports it, bypass only when you know exactly what you are doing.**

---

## References

- [Claude Code Memory (CLAUDE.md)](https://code.claude.com/docs/en/memory)
- [Claude Code Settings](https://code.claude.com/docs/en/settings)
- [Claude Code Overview](https://code.claude.com/docs/en/overview)
- [Claude Code CLI Reference](https://code.claude.com/docs/en/cli-usage)
- [Permission Modes](https://code.claude.com/docs/en/permission-modes)
