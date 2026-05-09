# Banking Posture

Banking is how your work survives session boundaries. The Idea Museum protocol's core axiom is: *if it's not banked, it didn't happen.* This document explains what that means in practice and which postures are available in v0.3.0-beta.

---

## What Banking Means

When Claude (acting as Curator) makes changes to your museum — creating or editing catalogue cards, updating the topic registry — those changes are written to files in your museum folder. "Banking" is the act of committing those changes to your version control or sync history, so they persist and are recoverable.

The Idea Museum protocol enforces a discipline: at the end of every SIP (Stable Increment Protocol — one bounded unit of work), you review what was written and commit it. This gives you a clear record of what changed and why.

---

## BankingMode

**BankingMode** is derived from your museum configuration. It describes how the server handles writes and what verification mechanism is available to you.

Four modes are defined in the architecture:

| Mode | How it works | Suited for |
|---|---|---|
| **ExternalGit** | Server writes directly; git tracks history | Git users — recommended for this beta |
| **Direct** | Server writes directly; no safety net | Advanced users who accept implicit trust |
| **Protected** | Server auto-snapshots before writes | Sync users (OneDrive, Dropbox) |
| **Reviewed** | Server creates drafts; you approve before writes land; incomplete in current beta | Maximum human control |

---

## ExternalGit — Recommended for v0.3.0-beta

ExternalGit is the fully operational and recommended posture for this beta release.

**How it works:** The server writes catalogue cards directly to your museum folder. Git tracks every change. Before committing, you review the diff — `git diff` or your preferred git tool (GitHub Desktop, VS Code source control, etc.) — to confirm the changes match what Claude declared it would do. You commit. The SIP closes.

**Why git diff matters:** It is your verification signal. You can see exactly what was written, line by line, before it becomes permanent history. This is the Two-Eyes Principle in practice — Claude writes, you verify before committing.

**Setup:** See [installation.md](installation.md) Step 6. One `git init` and an initial commit is all you need.

**Your config for ExternalGit** (in `.museum/config.json`, created automatically on first run):

```json
{
  "mcp_edits_drafts": false,
  "mcp_maintained_prior_versions": 0
}
```

This is the default. You do not need to create or edit this file manually — the server initialises it correctly for ExternalGit posture when it detects a git repository.

---

## Other Modes — Status in v0.3.0-beta

**Direct** — defined in the architecture but not recommended. No verification mechanism. Use only if you understand the implications and accept implicit trust in the Curator's writes.

**Protected** (auto-snapshot) — defined in the architecture; not all code paths fully operational in v0.3.0-beta. Intended for users who prefer OneDrive or Dropbox over git. Will be available in a future release.

**Reviewed** (draft approval) — defined in the architecture; not all code paths fully operational in v0.3.0-beta. Intended for users who want explicit approval before any write lands. Will be available in a future release.

If you are evaluating the tool without git and the ExternalGit posture does not suit your workflow, please [file feedback](https://github.com/swiftiansolutions/divergentdecisions-mcp/issues/new?template=feedback.md) describing your setup — this directly informs which mode to prioritise next.

---

## Commit Message Convention

The server provides a commit message at the end of each SIP. Use it — it carries the declared intent and a summary of what changed. Example:

```
Topic 029 tidy-up — session 2026-05-09

- Upgrade Next-Actions-029b and 029d to canonical schema
- Add May 2026 status note to 029b
- Remove accidental operator note from 029d
```

Your commit history becomes a readable log of your museum's intellectual development.
