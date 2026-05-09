# Known Limitations — v0.3.0-beta

This is an honest account of what is not yet available in the closed beta. These are not defects — they are features not yet built. They are listed here so you know what to expect and can give informed feedback about what matters most to you.

---

## No CLI

There is no command-line interface yet. This means:

- Configuration is done by editing `.museum/config.json` directly (a JSON file in your museum folder, created automatically on first run)
- There is no terminal command to review or accept drafts (Draft Review mode is not yet operational anyway — see below)

**Who this affects:** Everyone. The README install guide walks around this — the config rarely needs manual editing for ExternalGit posture.

**Roadmap:** CLI is the next planned component after the beta stabilises. It will provide commands for config management, draft review, version restoration, and museum health checks.

---

## No UI

There is no visual desktop interface. All interaction is through Claude Desktop and the MCP tools.

**Who this affects:** Non-technical users expecting a standalone application. The closed beta is intentionally targeting technical users who are comfortable with Claude Desktop and git.

**Roadmap:** UI follows CLI. It will provide visual settings management, diff-style draft review, version history browsing, and a museum health dashboard — making the methodology accessible to non-technical users.

---

## Protected Banking Mode Not Fully Operational

Protected mode (auto-snapshot before writes, intended for OneDrive and Dropbox users) is defined in the architecture but not all code paths are confirmed operational in v0.3.0-beta.

**Who this affects:** Users who want to use the server without git, relying on OneDrive or Dropbox version history as their verification mechanism.

**Workaround:** Use ExternalGit posture. Git is a one-time setup and provides better verification than sync history anyway.

---

## Reviewed Banking Mode Not Fully Operational

Reviewed mode (server creates draft files for human approval before writes land) is defined in the architecture but not all code paths are confirmed operational in v0.3.0-beta.

**Who this affects:** Users who want maximum control — see every proposed write before it lands, approve or reject individually.

**Workaround:** ExternalGit posture with careful git diff review before committing achieves equivalent oversight, just after the write rather than before.

---

## Windows Only — Mac Untested

The server has been developed and tested on Windows. Mac is untested — the author does not own Mac hardware. The server is built on .NET 10 which supports Mac in principle, but installation has not been verified.

**If you are on Mac:** You are welcome to try. If it works, please share your steps in [Discussions](https://github.com/swiftiansolutions/divergentdecisions-mcp/discussions). If it does not, file a [bug report](https://github.com/swiftiansolutions/divergentdecisions-mcp/issues/new?template=bug_report.md) with what you tried and what happened.

---

## Source Code Not Yet Published

The server binary is distributed but the source code is not yet publicly available. Source publication is planned once there is demonstrated interest from the beta. The licence (PolyForm Noncommercial 1.0.0) is in place from this release; source availability under the same terms will follow.

---

## Feedback on Priorities

If any of these limitations blocks a use case you care about, say so in a [feedback issue](https://github.com/swiftiansolutions/divergentdecisions-mcp/issues/new?template=feedback.md). It directly influences what gets built next.
