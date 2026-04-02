# Day 0 Setup

Before writing any code, spend ten minutes installing plugins that will shape how Claude works for you throughout the course. The marketplace has over a hundred entries; choosing the right starting set matters more than installing everything. The plugins below are organized by function so you can install what you need and skip what you do not.

## Project Setup

### Claude Code Setup

Claude Code Setup (55k+ installs, by Anthropic) analyzes your codebase and recommends Claude Code automations -- hooks, skills, MCP servers, subagents, and slash commands -- tailored to your specific tech stack. It works in read-only mode, examining your project structure and dependencies to surface the one or two highest-value recommendations per category.

This is useful because Claude is surprisingly weak at configuring itself without guidance. Left to its own judgment, it will underuse hooks and miss obvious MCP integrations. Provides value nothing else covers.

### Claude MD Management

Claude MD Management (92k+ installs, by Anthropic) provides tools for auditing and improving CLAUDE.md files -- the project memory documents that tell Claude about your codebase. Its `/revise-claude-md` command captures session learnings (discovered commands, code patterns, environment quirks) and proposes updates to your CLAUDE.md or `.claude.local.md` files as reviewable diffs.

Run it at the end of any productive session to prevent knowledge loss. Addresses a problem nothing else solves: keeping project memory current.

## Code Quality

### Code Review

Code Review (169k+ installs) launches five independent review agents analyzing PR changes from different angles (bug detection, git history context, CLAUDE.md compliance, and more). Each finding gets a confidence score; only high-confidence issues are posted.

### Code Simplifier

Code Simplifier (140k+ installs) is an autonomous agent that refines recently modified code for clarity and maintainability -- reducing nesting, improving naming, eliminating redundancy.

### Security Guidance

Security Guidance (87k+ installs) is a pre-tool hook that scans for dangerous patterns (command injection, unsafe dynamic code execution, XSS vectors, unsafe deserialization) and warns before edits proceed.

## Git Workflow

### Commit Commands

Commit Commands (86k+ installs) automates git commit, push, and PR workflows with AI-generated messages that match your repository's conventions. Requires the GitHub CLI (`gh`) installed and authenticated for PR creation.

## Output Styles

### Explanatory Output Style

Explanatory Output Style (35k+ installs) adds 2-3 educational insight points about implementation choices during code generation. Useful when learning a new codebase or technology.

### Learning Output Style

Learning Output Style (23k+ installs) transforms sessions into interactive learning by pausing at decision points and asking you to write 5-10 lines yourself rather than receiving complete solutions.

## References

- [Claude Code Setup](https://claude.com/plugins/claude-code-setup) -- codebase analysis for automation recommendations (55k+ installs)
- [Claude MD Management](https://claude.com/plugins/claude-md-management) -- CLAUDE.md auditing and improvement (92k+ installs)
- [Commit Commands](https://claude.com/plugins/commit-commands) -- git workflow automation (86k+ installs)
- [Code Review](https://claude.com/plugins/code-review) -- parallel-agent PR review (169k+ installs)
- [Code Simplifier](https://claude.com/plugins/code-simplifier) -- autonomous code refinement (140k+ installs)
- [Security Guidance](https://claude.com/plugins/security-guidance) -- vulnerability pattern detection (87k+ installs)
- [Explanatory Output Style](https://claude.com/plugins/explanatory-output-style) -- educational insights during coding (35k+ installs)
- [Learning Output Style](https://claude.com/plugins/learning-output-style) -- interactive learning mode (23k+ installs)
