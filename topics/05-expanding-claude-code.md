# Expanding and Demystifying Claude Code

## Skills

### What Are Skills

<!-- Specialized prompts that Claude Code can invoke for specific tasks -->

### How to Use Skills

<!-- Slash command invocation; skill discovery; when skills activate automatically -->

### Examples

<!-- A few concrete skill examples to illustrate the concept -->

## AGENTS.md

### What It Is

<!-- A file that defines agent roles, team compositions, and recipes -->

### How It Works

<!-- How Claude Code reads AGENTS.md to configure agent behavior -->

### When You Need It

<!-- Use cases: team-based workflows, specialized agent roles -->

## Hooks

### What Are Hooks

<!-- Event-driven scripts that run in response to Claude Code lifecycle events -->

### Hook Events

<!-- PreToolUse, PostToolUse, Stop, SessionStart, etc. -->

### How to Configure Hooks

<!-- Where hooks live; how to define them in settings -->

## Plugins

### What Are Plugins

<!-- Bundles of skills, commands, hooks, and agents distributed as packages -->

### How to Install and Manage Plugins

<!-- Plugin marketplace; installation commands; enabling/disabling -->

### Plugin Anatomy

<!-- plugin.json, skills/, commands/, hooks/, agents/ -->

## MCPs (Model Context Protocol)

### What Are MCPs

<!-- Protocol for connecting Claude Code to external tools and services -->

### How to Use MCPs

<!-- Configuration via .mcp.json; available server types -->

### Common MCP Integrations

<!-- Examples: Chrome DevTools, external APIs, databases -->

## Impact on the Context Window

<!-- How each extension mechanism (skills, hooks, plugins, MCPs) affects context consumption -->
<!-- Skills inject prompt text; hooks add lifecycle overhead; MCP tools add tool definitions -->
<!-- Practical guidance: be intentional about what you enable -->
