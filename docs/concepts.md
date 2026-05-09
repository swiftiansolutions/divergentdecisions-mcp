# Museum Concepts — Quick Reference

The DivergentDecisions museum is a structured way to explore, test, and decide on ideas in collaboration with Claude. The "museum" is not decoration — it is the operating metaphor. Just as a real museum collects, curates, and preserves artefacts for study, your idea museum collects your thinking, curates it through structured examination, and preserves it across sessions so nothing is lost to forgetting.

There are two roles. **You are the Operator** — the person with the ideas. You direct the work, decide what to explore next, review what gets written, and commit it. **Claude is the Curator** — at the start of every session it opens the museum: reading the protocols, walking the galleries, taking in everything that has been built and documented so far. From that standing start it knows the topics you have been working on, the decisions already made, the questions still open. Then you work together — investigating, building, deciding — adding to what is already there. When the session ends the museum structure remains in the repository, ready for the next Curator to walk in and pick up exactly where you left off.

Your museum holds the collective thinking around one coherent subject. You might have a museum for a product you are building, a research area you are investigating, or a career decision you are working through. The name you give it is the name of that collection.

Instead of a pile of notes and half-remembered conversations, you end up with something you can walk through — an exhibition of your thinking that shows what you explored, what you found, and what you decided.

This page explains the key terms. For the full picture, see the [Idea Museum conceptual model](https://github.com/swiftiansolutions/idea-museum/blob/main/conceptual-model/museum-conceptual-model.md).

---

## Topics

A topic is a numbered container for one idea you are exploring. All the cards produced while examining that idea share the same topic number. Topic 029 might be "Productization Strategy" — every DRIP, Evaluation, Decision, and Next-Actions card produced while working on that idea carries the 029 label.

The topic number is the thread that keeps everything connected.

---

## Catalogue Cards

Catalogue cards are the documents that record your thinking. There are four types, used in sequence as an idea matures.

---

### DRIP — Where You Start

**DRIP** stands for Discussion, Research, Investigation Protocol. It is the opening card for a topic — the place where you unpack the idea, describe what you know, name what you don't know, and set up the questions that need answering.

A DRIP does not reach conclusions. It frames the exploration. Think of it as the brief that opens the case.

*Example: "I have an idea for a new feature. What are the open questions? What do I need to test? What would a good outcome look like?"*

---

### Evaluation — Where You Test

An **Evaluation** is a structured examination of a specific question raised by the DRIP. You might have several Evaluations under one topic, each testing a different aspect of the idea.

Evaluations produce findings — evidence, comparisons, feasibility assessments — but they are not yet decisions. They feed the decision.

*Example: "Does the local LLM pathway work in practice? Here is what we tested, what we found, and what it means."*

---

### Decision — Where You Land

A **Decision** is the committed position that emerges from the evaluations. It records what was decided, why, what alternatives were considered and rejected, and what the consequences are.

Once accepted, a Decision does not get quietly revised. If thinking changes, a new Decision supersedes it. The history stays intact.

*Example: "We will use ExternalGit as the banking posture for the closed beta. Here is the rationale and what this forecloses."*

---

### Next-Actions — What Happens Next

A **Next-Actions** card is a task list tied to a topic. It tracks what needs to be done to implement or advance the idea — in groups, with conditions, completion states, and recent updates.

Unlike a generic to-do list, Next-Actions cards are linked to the decision record that created them. You always know why the work exists.

*Example: "Group 1: create the repo. Group 2: write the documentation. Group 3: package the binary."*

---

## Tangents

A tangent is an idea that surfaces unexpectedly during work on something else. The protocol treats tangents as first-class occurrences — they are not ignored, but they are also not allowed to derail the current work.

When a tangent appears, the Curator names it, you decide how to handle it (return to current work immediately, capture it for later, or make it the new focus), and the session continues cleanly.

---

## Crates

A crate is where tangents are stored when you want to come back to them. Raw material — conversation notes, observations, links — goes into the crate without being processed immediately. Crates sit in the museum basement until you are ready to unpack them in a dedicated session.

Crates prevent good ideas from being lost while keeping the current work uncluttered.

*Example: A conversation about whether a local LLM can run the protocol gets crated mid-session. The active SIP continues. The crate gets unpacked in a later session when there is time to examine it properly.*

---

## SIP — The Work Discipline

**SIP** stands for Stable Increment Protocol. It is the bounded unit of work within a session. Before doing anything, the Curator declares what is in scope, what is out of scope, and what will be committed at the end. Work happens. The result is committed to git (banked). The SIP closes.

A session typically contains several SIP cycles. SIPs are checkpoints, not session endings.

The discipline exists for two reasons: it prevents scope creep mid-session, and it ensures work is committed frequently so nothing is lost if the session ends unexpectedly.

---

## Banking

Banking is committing your work to git. The protocol's core rule is: **if it's not banked, it didn't happen.**

Claude has no memory between chat sessions. Your git repository is the only continuity. When you start a new session, the Curator bootstraps from your committed history — and only from that. Anything not committed before the session closed is gone.

Review the diff, commit with the message Claude provides, tell Claude it's done. That is the full banking cycle.