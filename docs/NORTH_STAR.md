# North Star

## Mission

Build a travel storytelling character so authentic that audiences think about what she discovers — not how she was made.

---

## Current Focus

**Milestone: Produce the first production-quality Sara episode.**

- Understand Google AI behavior during dialect transformation
- Understand Veo behavior during video generation
- Understand speech generation behavior
- Produce the first production-quality Sara episode

Nothing else.

---

## Future Vision

Ideas worth preserving. Not current priorities.

- Prompt Compiler
- Prompt Language (DSL)
- Multi-Provider Architecture
- Digital Human Framework
- Saudi Dialect Platform
- AI Research Framework
- Model Capability Matrix
- Advanced Knowledge Engine
- KNOWLEDGE_LOG.md — production memory system
- Automated Knowledge Promotion Pipeline

---

## Engineering Principles

Discovered during Sprints 001–004.

**Research before implementation.**
Understand the problem before designing the solution. Architecture that precedes evidence is speculation.

**Evidence before architecture.**
The Language Engine exists because production experiments proved input quality is the highest lever. Architecture follows proof.

**Simplicity first.**
Build the Minimum Working version. The MWLE was chosen over the full engine for exactly this reason. A pipeline you can test beats a system you cannot.

**One problem at a time.**
Each sprint has one objective. Each module has one responsibility. Each document covers one concern.

**Input quality drives output quality.**
The biggest improvement in Sara's output came from transforming the script, not from changing the voice model. The lesson: fix the input before blaming the output.

**AI assists. Humans decide.**
Google AI transforms. Sara's rules validate. The Knowledge Layer only promotes with human approval. AI surfaces — humans judge.

**Great ideas are not current priorities.**
The Parking Lot exists so that good ideas do not get lost and do not become distractions. Capture it. Park it. Return when the milestone is done.

**Build only what today's milestone requires.**
Version 10 thinking produces Version 0 results. Every decision is evaluated against the current milestone, not a hypothetical future state.

**Separation of concerns.**
One responsibility per document, per module, per stage. When two things share a concern, one of them is wrong.

---

## Decision Log

**D-01 — Sara Language Engine is independent**
The engine owns Sara's identity, rules, and knowledge. No external system — including Mantooq — is a dependency. External tools are implementations of specific modules, replaceable without affecting the engine.

**D-02 — Google AI has one responsibility**
Google AI transforms language register. It does not validate Sara's identity, approve knowledge, or make decisions. Transformation and judgment are separated.

**D-03 — Two-layer system**
Rules Layer: permanent, deterministic, changes only through documented decisions.
Knowledge Layer: evolves through production discoveries, promotes through human approval.
Neither layer replaces the other.

**D-04 — Knowledge promotion requires human approval**
Nothing moves from Observation to Rule automatically. Every promotion is a documented human decision. AI may flag. Humans decide.

**D-05 — MWLE over full engine**
Sprint 002 chose the Minimum Working Language Engine over the complete 8-module system. The goal was a pipeline testable with one real script. Full implementation follows validated need.

**D-06 — Provider-agnostic integration**
Sara calls a Transformation Provider through a fixed interface. The provider is replaceable. V1 uses Google AI. The engine does not change if the provider changes.

**D-07 — Bibles are read-only**
Sara Content System bibles (Language, Voice, Persona, Story Framework) are inputs to the engine. The engine reads them. It never modifies them. Bible changes are Content System decisions, not engine decisions.

**D-08 — Production experiments drive architecture**
Architecture evolves only when production experiments prove it must. If the first episode reveals a pipeline weakness, the architecture is updated. If not, it holds.
