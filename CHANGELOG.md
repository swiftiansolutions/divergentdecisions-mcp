# Changelog

## v0.3.0-beta — Closed Beta Release (2026-05-09)

Initial closed beta release of the DivergentDecisions MCP server.

### Included

- Full Section 2.2 Phase 1 bootstrap (protocol and template loading, stale crate check)
- SIP-disciplined examination workflow (Scope → Execute → Bank → Close)
- Complete catalogue card tooling: create, read, update, surgical edit, upgrade legacy cards
- Topic Registry management: create topics, register cards, transition statuses, archive topics
- Crate tooling: initialise, add objects, catalogue, create themes, record dispositions, digest
- Full-text search across catalogue cards and crate objects
- ExternalGit banking posture — fully supported and recommended for this beta

### Not yet included

- CLI (command-line interface for config, draft, and version management)
- UI (visual desktop interface)
- Protected banking mode (auto-snapshot before writes, for sync users)
- Reviewed banking mode (MCP creates drafts for human approval)

See [docs/known-limitations.md](docs/known-limitations.md) for details.

### Platform

- **Windows:** Tested and confirmed
- **Mac:** Untested — author does not own a Mac; community feedback welcome

### Methodology

Implements [Idea Museum Protocol v2.6](https://github.com/swiftiansolutions/idea-museum/blob/main/protocols/Idea_Museum_Protocol.md).
