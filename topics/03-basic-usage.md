# Basic Claude Code Usage

## Context Window in Practice

<!-- Link back to topic 01: ML Basics -->
<!-- How prompts, tool configurations, and conversation history consume context -->
<!-- Why this understanding shapes everything below -->

## Concise Prompting

### Why Brevity Matters

<!-- Shorter prompts = more room for useful context and tool output -->

### Tips for Effective Prompts

<!-- Lead with intent; avoid filler; be specific about scope -->

## CLAUDE.md

### What It Is

<!-- Project-level instructions that Claude Code reads automatically -->

### What Goes in It

<!-- Project structure, conventions, build commands, constraints -->

### User vs Project CLAUDE.md

<!-- ~/.claude/CLAUDE.md (global) vs ./CLAUDE.md (project) -->

## Settings

### User Settings vs Project Settings

<!-- Where each lives; what each controls; precedence -->

### Key Settings to Know

<!-- The most important settings for daily use -->

## Best Practices

<!-- Collected guidance for getting the most out of Claude Code -->

## The /init Command

### What It Does

<!-- Generates a starter CLAUDE.md for a project -->

### When to Use It

<!-- First time working in a new repo; bootstrapping conventions -->

## Plan Mode

### What It Is

<!-- Read-only investigation and planning before making changes -->

### Why You Should Always Use It for New Tasks

<!-- Prevents wasted work; ensures alignment before implementation -->
<!-- Emphasize: default to plan mode when doing something unfamiliar -->

## Permission Modes

### Overview

<!-- How Claude Code handles permissions for file edits and commands -->

### bypasspermissions

<!-- What it does: skips all permission prompts -->
<!-- Risks: unintended file changes, destructive commands without confirmation -->

### acceptedits

<!-- What it does: auto-approves file edits but still prompts for commands -->
<!-- Trade-off: less friction for edits, but more prompts for shell commands -->

### Choosing Between Them

<!-- When each is appropriate; why bypasspermissions is risky for beginners -->
<!-- Recommendation: start with default or acceptedits, graduate to bypass only when confident -->
