# .claude.example

A working starter bundle for `~/.claude/` — the user-level config directory Claude Code reads on every session. This is the configuration I recommend for everyone new to the tool. Copy it, start using it, customize as you learn.

> This folder is a prototype of a standalone `claudefiles` repo that will get split out later. For now it lives inside the course repo so you can copy it during the workshop.

## What's inside

```
.claude.example/
├── settings.json      # auto permission mode + day-zero plugin auto-install
├── CLAUDE.md          # user-level memory template
└── skills/            # where your personal skills go
    └── README.md
```

### `settings.json`

- `permissions.defaultMode: "auto"` — a classifier auto-approves safe actions and prompts for risky ones. **Requires a Max, Team, or Enterprise plan.** Drop to `"acceptEdits"` if you're on Pro.
- `permissions.allow` — common safe commands pre-allowlisted (git, gh, npm/pnpm/yarn, tests, reads, the usual file-inspection Bash commands).
- `permissions.deny` — `sudo`, `rm -rf`, outbound `curl`/`wget`/`ssh`, `.env` reads, private keys.
- `autoInstallEnabledPlugins: true` plus `enabledPlugins` listing all eight day-zero plugins — first time Claude Code sees this file, it installs them all.

### `CLAUDE.md`

User-level memory applied to every project on your machine. Ships with commented sections for language preferences, workflow habits, communication style, and quality gates. Uncomment what you want; delete what you don't.

### `skills/`

Starts empty. Drop `SKILL.md` files here (each in its own subfolder, e.g. `skills/my-skill/SKILL.md`) for personal workflows that should be available across every project.

## Install

### Fresh install — no existing `~/.claude/`

```bash
cp -r .claude.example ~/.claude
```

Start a Claude Code session. On first launch the eight plugins install automatically.

### Existing install — you already have a `~/.claude/`

Cherry-pick:

1. **`settings.json`** — merge keys into your existing `~/.claude/settings.json`. Key fields: `permissions.defaultMode`, `permissions.allow`, `permissions.deny`, `autoInstallEnabledPlugins`, `enabledPlugins`.
2. **`CLAUDE.md`** — append the template sections you want into your existing `~/.claude/CLAUDE.md`.
3. **`skills/`** — copy in any skills directories you don't already have.

Restart `claude`. Plugins auto-install on the next session.

## The day-zero plugins

The bundle auto-installs these on first launch:

| Plugin | What it does |
|--------|--------------|
| `claude-code-setup` | Scans your repo and recommends Claude Code automations to add |
| `claude-md-management` | Audits and improves CLAUDE.md files |
| `commit-commands` | AI-generated commits + PR workflow (requires `gh` CLI) |
| `code-review` | Five parallel review agents for PR diffs |
| `code-simplifier` | Autonomous refactor of recent changes for clarity |
| `security-guidance` | Pre-tool hook that flags dangerous patterns before edits run |
| `explanatory-output-style` | Adds educational insights during code generation |
| `learning-output-style` | Interactive learning mode — asks you to write some of the code |

If autoinstall misbehaves on your setup, fall back to manual install inside a Claude session:

```
/plugin install claude-code-setup@claude-plugins-official
/plugin install claude-md-management@claude-plugins-official
/plugin install commit-commands@claude-plugins-official
/plugin install code-review@claude-plugins-official
/plugin install code-simplifier@claude-plugins-official
/plugin install security-guidance@claude-plugins-official
/plugin install explanatory-output-style@claude-plugins-official
/plugin install learning-output-style@claude-plugins-official
```

## Customizing

After a few sessions you'll want to adjust things. The usual edits:

- **Permissions** — add tool patterns you find yourself approving constantly to `allow`; tighten `deny` around any paths or commands that scare you.
- **CLAUDE.md** — capture preferences as you notice them. Use the `claude-md-management` plugin's `/revise-claude-md` at session end to turn session learnings into clean diffs.
- **Skills** — add a skill the first time you think "I'll need to explain this again next time."
- **Plugins** — browse the marketplace with `/plugin` once you're comfortable. Remove any day-zero defaults you don't use.

## References

- [Claude Code Settings](https://code.claude.com/docs/en/settings)
- [Plugins](https://code.claude.com/docs/en/plugins)
- [Skills](https://code.claude.com/docs/en/skills)
- [Permission Modes](https://code.claude.com/docs/en/permission-modes)
