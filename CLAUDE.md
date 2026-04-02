# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Agentic Engineering 101 is a collection of educational resources for learning agentic development with Claude Code. It is a content-only project (no build system or runtime code).

## Structure

- `topics/` — Markdown files with introductory coverage of course topics
- `slides/` — Marp presentation decks generated from `topics/` using the `marp-slide-content` skill and styled with `sui-marp-theme`
- `claudefiles/` — Example `~/.claude/` configuration for bootstrapping concepts taught in the course

## Content Workflow

1. Write or edit topic content in `topics/` as markdown
2. Generate slide content from topics using `/marp-slide-content`
3. Apply presentation theme using `/sui-marp-theme`
4. Place finished decks in `slides/`
