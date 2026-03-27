# Day 0 Setup

Before writing any code, spend ten minutes installing plugins that will shape how Claude works for you throughout the course. The marketplace has over a hundred entries; choosing the right starting set matters more than installing everything. Here is what we recommend and why.

## Recommended Plugins

These three plugins are complementary. Install all of them.

### Superpowers

**Install this first.** Superpowers (233k+ installs) is a composable skills framework by Jesse Vincent that teaches Claude structured development methodologies. It covers planning, code review, test-driven development, systematic debugging, brainstorming, subagent-driven development, and skill authoring -- all through slash commands like `/brainstorming`, `/execute-plan`, and `/writing-plans`.

What makes it valuable is the discipline it imposes. TDD follows strict red-green-refactor cycles where tests must fail before implementation. Debugging requires root cause investigation before any fix is attempted. Brainstorming runs Socratic sessions that refine requirements before coding starts -- and enforces a hard gate preventing implementation until the design is approved.

Because Superpowers covers so much ground, it substantially replaces several standalone plugins. We list those below so you know they exist, but installing them separately is not necessary.

### Claude Code Setup

Claude Code Setup (55k+ installs, by Anthropic) analyzes your codebase and recommends Claude Code automations -- hooks, skills, MCP servers, subagents, and slash commands -- tailored to your specific tech stack. It works in read-only mode, examining your project structure and dependencies to surface the one or two highest-value recommendations per category.

This is useful because Claude is surprisingly weak at configuring itself without guidance. Left to its own judgment, it will underuse hooks and miss obvious MCP integrations. Independent of Superpowers; provides value nothing else covers.

### Claude MD Management

Claude MD Management (92k+ installs, by Anthropic) provides tools for auditing and improving CLAUDE.md files -- the project memory documents that tell Claude about your codebase. Its `/revise-claude-md` command captures session learnings (discovered commands, code patterns, environment quirks) and proposes updates to your CLAUDE.md or `.claude.local.md` files as reviewable diffs.

Run it at the end of any productive session to prevent knowledge loss. This is independent of Superpowers and addresses a problem nothing else solves: keeping project memory current.

## Plugins Covered by Superpowers

These plugins provide functionality that Superpowers partially or fully covers. Installing them separately is usually not necessary, but they are listed here so you know what each does.

| Plugin | Installs | Superpowers Overlap |
|---|---|---|
| Commit Commands | 86k+ | `finishing-a-development-branch` skill covers commit/push/PR workflow |
| Code Review | 169k+ | `requesting-code-review` provides single-agent review (the standalone plugin runs 5 parallel agents -- more thorough) |
| Code Simplifier | 140k+ | No direct equivalent in Superpowers |
| Security Guidance | 87k+ | No direct equivalent in Superpowers |
| Explanatory Output Style | 35k+ | Largely superseded by Learning Output Style |
| Learning Output Style | 23k+ | `brainstorming` partially overlaps with its interactive approach |

### Commit Commands

Automates git commit, push, and PR workflows with AI-generated messages that match your repository's conventions. Requires the GitHub CLI (`gh`) installed and authenticated for PR creation.

### Code Review

Launches five independent review agents analyzing PR changes from different angles (bug detection, git history context, CLAUDE.md compliance, and more). Each finding gets a confidence score; only high-confidence issues are posted.

### Code Simplifier

An autonomous agent that refines recently modified code for clarity and maintainability -- reducing nesting, improving naming, eliminating redundancy.

### Security Guidance

A pre-tool hook that scans for dangerous patterns (command injection, unsafe dynamic code execution, XSS vectors, unsafe deserialization) and warns before edits proceed.

### Explanatory Output Style

Adds 2-3 educational insight points about implementation choices during code generation. Largely superseded by Learning Output Style.

### Learning Output Style

Transforms sessions into interactive learning by pausing at decision points and asking you to write 5-10 lines yourself rather than receiving complete solutions.

## References

- [Superpowers](https://claude.com/plugins/superpowers) -- composable skills framework (233k+ installs)
- [Claude Code Setup](https://claude.com/plugins/claude-code-setup) -- codebase analysis for automation recommendations (55k+ installs)
- [Claude MD Management](https://claude.com/plugins/claude-md-management) -- CLAUDE.md auditing and improvement (92k+ installs)
- [Commit Commands](https://claude.com/plugins/commit-commands) -- git workflow automation (86k+ installs)
- [Code Review](https://claude.com/plugins/code-review) -- parallel-agent PR review (169k+ installs)
- [Code Simplifier](https://claude.com/plugins/code-simplifier) -- autonomous code refinement (140k+ installs)
- [Security Guidance](https://claude.com/plugins/security-guidance) -- vulnerability pattern detection (87k+ installs)
- [Explanatory Output Style](https://claude.com/plugins/explanatory-output-style) -- educational insights during coding (35k+ installs)
- [Learning Output Style](https://claude.com/plugins/learning-output-style) -- interactive learning mode (23k+ installs)
