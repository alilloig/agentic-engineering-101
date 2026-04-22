# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Agentic Engineering 101 is a collection of educational resources for learning agentic development with Claude Code. It is a content-only project (no build system or runtime code).

## Structure

- `topics/` — Markdown files with long-form coverage of course topics. The source of truth for the talk.
  - `01-intro.md` — the shift, the goal, the price
  - `02-ml.md` — ML basics (evolution of AI, Transformer, attention, tokens, context window, training)
  - `03-the-harness.md` — the agent loop, tool calls, permissions, context window, CLAUDE.md, skills
  - `04-setup.md` — install the three surfaces and the `.claude.example` bundle
  - `99-future-topics.md` — parking lot for a follow-up session (hooks, plugins, MCPs)
- `.claude.example/` — working starter bundle for `~/.claude/` used live in chapter 04. Prototype of a standalone `claudefiles` repo to be split out later.

Slides for the talk live in Google Slides, not in this repo. The topic files are the source of truth; slide content is extracted from them.

## Content Workflow

1. Draft or edit topic content in `topics/` as markdown
2. Iterate on ideas and prose until the topic reads well as a standalone document
3. Extract punch lines and short-form text from the topic files into the Google Slides deck
