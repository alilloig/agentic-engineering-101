# User-level CLAUDE.md

This file lives at `~/.claude/CLAUDE.md` and applies to every Claude Code session on this machine. Project-level CLAUDE.md files (in the repo root or `./.claude/CLAUDE.md`) take precedence over anything here.

Keep this file opinionated but short. When it grows past ~200 lines, split into `@~/.claude/rules/*.md` imports.

Uncomment the sections you want active. Delete the ones you don't.

<!--
## Language and framework preferences

- TypeScript: prefer strict mode. No `any`; prefer `unknown` when the type is unclear.
- Python: type-annotate everything. Prefer `pathlib` over string paths. Use `pytest` for tests.
- Go: idiomatic errors, no panics except in `main`.
- Rust: prefer `Result` over `unwrap` outside of tests.
-->

<!--
## Workflow habits

- Start every non-trivial task in plan mode. Exit plan mode only after the plan is right.
- Prefer small, focused commits with imperative-mood messages.
- Run tests before declaring a task done.
- Never commit directly to `main` — open a PR.
- Use `/compact` when the session has drifted or taken abandoned paths.
-->

<!--
## Communication style

- Be concise. No preamble, no "Here's what I'll do".
- When uncertain, ask one clarifying question before starting.
- Surface assumptions out loud when they materially affect the plan.
- Show diffs for non-trivial edits rather than explaining what changed in prose.
-->

<!--
## Quality gates

- Lint before finishing.
- No commented-out code in committed changes.
- Update CLAUDE.md when you learn something about a project that would help future sessions.
- Prefer editing existing files over creating new ones unless the new file genuinely belongs.
-->
