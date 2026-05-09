# Your First Session

This guide walks you through your first museum session from a fresh install. By the end you will have completed a bootstrap, declared a SIP, done a piece of work, and banked it — the complete cycle.

**Prerequisites:** Installation complete per [installation.md](installation.md). Claude Desktop running with DivergentDecisions tools connected.

---

## What Happens in a Session

Every museum session follows the same pattern:

1. **Bootstrap** — the Curator loads foundation documents and gains museum context
2. **SIP cycles** — one bounded unit of work at a time: scope, execute, bank, close
3. **Session end** — final banking verified, chat closed

The session discipline exists because Claude has no memory between chat windows. Everything not banked vanishes. The bootstrap rebuilds context from the repository at the start of every session. Your committed git history is your continuity.

---

## Step 1 — Start a New Chat

Open Claude Desktop and start a new conversation.

---

## Step 2 — Run the Bootstrap

Paste the following prompt exactly:

```
Execute bootstrap Protocol Section 2.2 Phase 1 using the DivergentDecisions MCP tools (starting with get_curator_protocol). You will take on the responsibilities of curator. Pay attention to the normative language used in the protocol.
```

Claude will load all foundation documents via the MCP tools in sequence:

- Curator Protocol
- Protocol Landscape
- Governance Protocol
- MCP Cataloguing Instructions
- Template Registry
- Active Topic Digest
- Stale Crate Check

This takes around 30–60 seconds. When complete, Claude will confirm Phase 1 done and ask what you want to work on.

---

## Step 3 — Give Work Context (Phase 2)

Tell Claude what you want to examine. For a first session, you might say:

> "I want to start exploring an idea I have about [your topic]. Let's create a new DRIP."

Claude will ask clarifying questions, confirm scope, and then declare SIP (small increment protocol) entry before doing anything — this is the protocol working correctly. A SIP declaration will name what is included, what is excluded, and what will be banked.

---

## Step 4 — Do the Work

Claude will work within the declared SIP scope. For a first DRIP this typically means:

- Creating a new Topic in the registry
- Creating and populating a DRIP catalogue card
- Asking you questions about the artifact (your idea)

Stay within scope. If a new idea emerges mid-session, Claude should detect it as a tangent and propose how to handle it (immediate return, crate it for later, or make it the new work).

---

## Step 5 — Bank the Work

At the end of the SIP, Claude will provide a commit message. Open your git tool of choice (GitHub Desktop, VS Code, command line) and:

1. Review the diff — confirm the changes match what Claude declared it would do
2. Commit using the message Claude provided
3. Tell Claude: "Committed and synced"

Claude will then close the SIP.

---

## Step 6 — Continue or Close

Claude will suggest the next increment or recommend closing the session if the work is complete or context is getting long. You can continue with another SIP or end the chat.

When you end the chat, you will typically stop the conversation there. Your next session starts with a fresh chat and bootstrap from the repository — and because you banked your work, the next Curator will find your DRIP and continue from where you left off.

The reasons to stop are that long conversation are compressed and focus becomes diluted, the AI reverts to helpful chat rather than idea partner. Keeping the chat focused and banked allows you to save where you got to and start afresh. Exactly when to do this is something you will have to learn as an AI can only offer opinion on its context window state not facts.

---

## Tips for Your First Session

**Keep your first SIP small.** A single DRIP creation is a good first increment. You are learning the rhythm — scope, execute, bank, close — as much as doing the work.

**Read the diff before committing.** This is not optional overhead — it is the verification step. You will quickly develop a feel for what a clean diff looks like.

**Trust the protocol.** If Claude asks you to confirm scope before starting, or refuses to proceed without a SIP declaration, that is the protocol working as designed. It will feel like overhead at first and natural very quickly.

**For the bootstrap prompt:** On Windows, `Ctrl+V` pastes plain text. If your text editor adds formatting, use `Ctrl+Shift+V` to paste as plain text into Claude Desktop as sometime Claude will reject a markdown formatted paste to bootstrap from (or at least confirm you meant for it open the MCP and use it as imput to follow)

---

## Further Reading

- [Idea Museum Protocol](https://github.com/swiftiansolutions/idea-museum/blob/main/protocols/Idea_Museum_Protocol.md) — the full operating charter
- [Museum Conceptual Model](https://github.com/swiftiansolutions/idea-museum/blob/main/conceptual-model/museum-conceptual-model.md) — the metaphor and architecture explained
- [banking-posture.md](banking-posture.md) — the verification and commit discipline in detail
