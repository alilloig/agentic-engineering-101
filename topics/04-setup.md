# Setup

You've seen what Claude Code is and how its loop works. This chapter is purely logistical: install the three surfaces, drop in the `.claude.example` bundle, start using it. No further theory.

> The `.claude.example/` folder in this repo is a working prototype of a configuration bundle that will eventually live in its own repo. For now, point your fresh install at it.

## Install the three surfaces

### CLI

Native binary, auto-updates, no Node.js dependency:

```bash
curl -fsSL https://claude.ai/install.sh | bash
```

Homebrew also works (`brew install --cask claude-code`) but doesn't auto-update. If you previously installed via `npm install -g @anthropic-ai/claude-code`, uninstall and migrate — that path is deprecated.

Verify with `claude --version` and `claude doctor`.

### Desktop app

macOS installer (Intel + Apple Silicon): [download](https://claude.ai/api/desktop/darwin/universal/dmg/latest/redirect). Open the `.dmg`, drag Claude to Applications, launch it. Sign in with your Claude account and click the **Code** tab.

The Desktop app and the CLI share the same engine, the same CLAUDE.md, and the same settings.

### Chrome extension

Browser automation, live debugging, authenticated site access. Install from the [Chrome Web Store](https://chromewebstore.google.com/detail/claude/fcoeoabgfenejglbffodgkkbkcdhcgfn). To connect it to your CLI session, launch with `claude --chrome` or run `/chrome` in an existing session.

Requires Claude Code 2.0.73+ and extension version 1.0.36+.

## Drop in the `.claude` bundle

Prerequisite: a paid Claude account on the **Max**, **Team**, or **Enterprise** plan. The bundle uses `auto` permission mode, which is gated to those tiers.

### Fresh install (no existing `~/.claude/` yet)

Copy `.claude.example/` straight into your home directory:

```bash
cp -r /path/to/agentic-engineering-101/.claude.example ~/.claude
```

Start any session. `autoInstallEnabledPlugins: true` picks up the `enabledPlugins` list on first launch and installs all eight day-zero plugins automatically.

### Existing install (you already have a `~/.claude/`)

Don't overwrite — cherry-pick:

- **`settings.json`** — merge the additions into your existing `~/.claude/settings.json`. Pay particular attention to `permissions.defaultMode`, `permissions.allow`, `permissions.deny`, `autoInstallEnabledPlugins`, and `enabledPlugins`.
- **`CLAUDE.md`** — append the template sections you want into your existing user-level CLAUDE.md, uncommenting the ones you want active.
- **`skills/`** — copy anything you don't already have.

Restart `claude` and the plugins auto-install on the next session.

### What's inside

- **`settings.json`** — `auto` permission mode, sensible `allow`/`deny` lists, `autoInstallEnabledPlugins: true` plus the day-zero plugin list.
- **`CLAUDE.md`** — user-level memory template with commented sections for language preferences, workflow habits, and communication style.
- **`skills/`** — where your personal skills live. Starts empty with a README.

Full docs in `.claude.example/README.md`.

## References

- [Claude Code Installation](https://code.claude.com/docs/en/setup)
- [Chrome Integration](https://code.claude.com/docs/en/chrome)
- [Desktop Quickstart](https://code.claude.com/docs/en/desktop-quickstart)
- [Plugins](https://code.claude.com/docs/en/plugins)
