# DivergentDecisions MCP Server

Reference implementation of the [Idea Museum](https://github.com/swiftiansolutions/idea-museum) protocol for Claude Desktop.

DivergentDecisions is an MCP (Model Context Protocol) server that gives Claude structured access to your idea museum — a personal repository for exploring, evaluating, and deciding on ideas systematically across sessions. It implements the Idea Museum protocol: the operational rules, catalogue card structures, and session discipline that make human-AI idea exploration recoverable and coherent.

This repository contains the server. For the methodology — the protocol, templates, and conceptual model the server implements — see [idea-museum](https://github.com/swiftiansolutions/idea-museum).

> **This is a closed beta release (v0.3.0-beta).** See [BETA.md](BETA.md) for what that means before you proceed.

---

## Prerequisites

- [Claude Desktop](https://claude.ai/download) installed and running
- Git — recommended; ExternalGit is the fully supported banking posture for this beta
- Windows 10/11 — see [docs/installation.md](docs/installation.md) for platform notes

---

## Installation

**Step 1 — Create two folders**

Choose a location and create two sibling folders. The museum name is yours — it names your idea collection, so pick something that reflects what you are exploring. If you are not sure yet, the defaults work fine:

```
IdeaMuseum\       ← your museum (your git repo lives here)
IdeaMuseumMCP\    ← the MCP server (exe lives here, kept out of git)
```

Keeping them separate ensures your git history contains only your intellectual work, not the server binary.

**Step 2 — Download and extract**

Download the latest release zip from the [Releases](../../releases) page and extract `DivergentDecisionsMCP.API.exe` into your `IdeaMuseumMCP` folder.

**Step 3 — Register with Claude Desktop**

Open your Claude Desktop config file at `%APPDATA%\Claude\claude_desktop_config.json` and add an entry to the `mcpServers` section:

```json
{
  "mcpServers": {
    "DivergentDecisions": {
      "command": "C:\\Path\\To\\IdeaMuseumMCP\\DivergentDecisionsMCP.API.exe",
      "args": [],
      "env": {
        "Museum__RepositoryPath": "C:\\Path\\To\\IdeaMuseum"
      }
    }
  }
}
```

Replace the paths with your actual folder locations. `Museum__RepositoryPath` (double underscore — .NET nested configuration convention) tells the server where your museum lives.

**Step 4 — Restart Claude Desktop**

Fully quit and relaunch Claude Desktop. The DivergentDecisions tools will appear in your session.

**Step 5 — Initialise git in your museum folder**

```bash
cd IdeaMuseum
git init
git commit --allow-empty -m "Initial museum"
```

See [docs/installation.md](docs/installation.md) for the full step-by-step guide, and [docs/banking-posture.md](docs/banking-posture.md) for why git is the recommended approach.

---

## First Session

See [docs/first-session.md](docs/first-session.md) for a walkthrough of your first bootstrap and SIP.

---

## Feedback and Bugs

Feedback is how this beta gets better.

- [Report a bug](../../issues/new?template=bug_report.md)
- [Share feedback](../../issues/new?template=feedback.md)
- [Ask a question or start a conversation](../../discussions)

---

## Licence

[PolyForm Noncommercial 1.0.0](LICENSE.md) — free for personal, non-profit, and academic use. Commercial use is not permitted.

The Idea Museum protocol this server implements is separately licensed under [CC-BY-NC-SA 4.0](https://github.com/swiftiansolutions/idea-museum/blob/main/LICENSE.md).
