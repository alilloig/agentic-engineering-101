# Installation

Claude Code is available across multiple surfaces: a command-line tool, a standalone desktop application, IDE extensions, and a Chrome browser extension. This topic covers installing the three you will use most during this course: the CLI, the Desktop app, and the Chrome extension.

## Claude Code CLI

### Prerequisites

Claude Code runs on macOS 13.0+, Windows 10 1809+, and most Linux distributions (Ubuntu 20.04+, Debian 10+, Alpine 3.19+). You need at least 4 GB of RAM and an internet connection.

Your terminal must run Bash, Zsh, PowerShell, or CMD. On Windows, install [Git for Windows](https://git-scm.com/downloads/win) before proceeding -- Claude Code uses Git Bash internally.

You also need a paid Claude account (Pro, Max, Teams, or Enterprise). The free Claude.ai plan does not include Claude Code access. Alternatively, you can authenticate with an Anthropic Console API key or a third-party provider (Amazon Bedrock, Google Vertex AI, Microsoft Foundry).

> **Note on Node.js**: The old npm-based installation required Node.js 18+. The current recommended install methods (curl, Homebrew) are native binaries and have no Node.js dependency.

### Installation Steps

**Native install (recommended for macOS and Linux):**

```bash
curl -fsSL https://claude.ai/install.sh | bash
```

This downloads a self-contained binary to `~/.local/bin/claude`. Native installations auto-update in the background, so you always have the latest version.

**Homebrew (macOS and Linux alternative):**

```bash
brew install --cask claude-code
```

Homebrew installations do not auto-update. Run `brew upgrade claude-code` periodically to stay current.

**npm (deprecated):**

```bash
# Do NOT use this for new installations
npm install -g @anthropic-ai/claude-code
```

The npm method is deprecated. It is slower, requires Node.js 18+, and does not auto-update. If you previously installed via npm, migrate to the native binary:

```bash
curl -fsSL https://claude.ai/install.sh | bash
npm uninstall -g @anthropic-ai/claude-code
```

After installation, start Claude Code in any project directory:

```bash
cd your-project
claude
```

You will be prompted to authenticate in your browser on first launch.

### Verifying the Installation

Run the version check:

```bash
claude --version
```

You should see output like `2.1.85 (Claude Code)` (your version may be newer).

For a deeper health check of your installation and configuration:

```bash
claude doctor
```

This diagnoses common issues with authentication, auto-updates, and system configuration.

## Claude Desktop for macOS

### Download and Install

The Claude Desktop app provides a graphical interface for Claude Code. It lets you review diffs visually, run multiple sessions side by side, schedule recurring tasks, and kick off cloud sessions.

Download the macOS installer (supports both Intel and Apple Silicon):

- [Download Claude Desktop for macOS](https://claude.ai/api/desktop/darwin/universal/dmg/latest/redirect)

Open the `.dmg` file, drag Claude to your Applications folder, and launch it.

### Initial Configuration

On first launch, Claude prompts you to sign in with your Claude account. After authenticating, click the **Code** tab to start a coding session. The Desktop app connects to the same underlying Claude Code engine as the CLI, so your `CLAUDE.md` files, settings, and MCP servers are shared across both.

A paid subscription (Pro, Max, Teams, or Enterprise) is required.

## Chrome Plugin

### Installation from Chrome Web Store

The "Claude in Chrome" extension connects Claude Code to your browser, enabling browser automation directly from the CLI or Desktop app.

1. Open the Chrome Web Store listing: [Claude in Chrome](https://chromewebstore.google.com/detail/claude/fcoeoabgfenejglbffodgkkbkcdhcgfn)
2. Click **Add to Chrome** and confirm the permissions
3. Verify the extension appears in your browser toolbar

The extension works with Google Chrome and Microsoft Edge. It requires version 1.0.36 or higher and Claude Code 2.0.73 or higher.

### What It Enables

With the Chrome extension connected, Claude Code gains the ability to interact with your browser programmatically:

- **Live debugging** -- read console errors, inspect DOM state, and fix the code that caused them
- **Web app testing** -- submit forms, verify user flows, and check for visual regressions
- **Authenticated site access** -- interact with any site you are logged into (Google Docs, Notion, internal tools) without API connectors
- **Data extraction** -- pull structured information from web pages and save it locally
- **Task automation** -- automate repetitive browser tasks like form filling and multi-site workflows

To connect the extension to your CLI session, start Claude Code with the `--chrome` flag:

```bash
claude --chrome
```

Or run `/chrome` from within an existing session to connect on the fly.

---

## Verification Checklist

Before moving on, confirm all three surfaces are working:

1. **CLI**: Run `claude --version` and confirm you see a version number
2. **Desktop**: Open the Claude Desktop app, sign in, and verify the Code tab loads
3. **Chrome extension**: Check that the Claude icon appears in your browser toolbar. Start a `claude --chrome` session and run `/chrome` to verify the connection status

If any step fails, consult the [troubleshooting guide](https://code.claude.com/docs/en/troubleshooting) or run `claude doctor` for automated diagnostics.

## References

- [Claude Code Overview (official docs)](https://code.claude.com/docs/en/overview)
- [Advanced Setup (official docs)](https://code.claude.com/docs/en/setup)
- [Claude Code GitHub Repository](https://github.com/anthropics/claude-code)
- [Chrome Integration (official docs)](https://code.claude.com/docs/en/chrome)
- [Claude in Chrome Extension (Chrome Web Store)](https://chromewebstore.google.com/detail/claude/fcoeoabgfenejglbffodgkkbkcdhcgfn)
- [Desktop App Quickstart (official docs)](https://code.claude.com/docs/en/desktop-quickstart)
