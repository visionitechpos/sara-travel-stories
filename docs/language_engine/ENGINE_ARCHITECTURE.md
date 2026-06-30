# Engine Architecture

## Overview

The Language Engine is composed of two complementary layers and eight processing modules.

The two layers define who owns the knowledge and who makes decisions.
The eight modules define what work is done and in what order.

---

## Architecture Principles

### Google AI has one responsibility

Google AI transforms the script into Sara's natural Hejazi speaking style.

That is its only job.

It does not decide what is correct for Sara. It does not validate identity. It does not approve knowledge. It transforms language — and the project validates the result.

### Sara makes the decisions

Sara's identity, rules, and knowledge belong to this project — not to any AI provider.

If Google AI is replaced tomorrow, Sara's knowledge remains intact. The engine is independent. External tools are implementations, not dependencies.

### AI discovers. Humans approve.

The AI may surface patterns, suggest improvements, or flag inconsistencies. None of that becomes permanent project knowledge until a human reviews it and documents the decision.

Nothing is promoted automatically.

---

## Two-Layer System

The engine operates on two complementary layers that work together.

---

### Rules Layer

Contains permanent, explicit rules derived from Sara's bibles and project decisions.

Rules are deterministic. Same input, same outcome. No ambiguity.

**What the Rules Layer contains:**
- Forbidden words and phrases
- Character identity constraints
- Voice and speech constraints
- Non-negotiable project decisions from README.md

**How rules change:**

Rules do not drift. They change only through an explicit project decision documented in `PRODUCTION_DECISIONS_LOG.md`. A rule that changes without documentation is not a rule — it is inconsistency.

---

### Knowledge Layer

Contains evolving production knowledge — discoveries made during episode production that improve Sara's output over time.

**Knowledge lifecycle:**

```
Discovery
    ↓
Observation       ← Noticed during production. Documented, not yet confirmed.
    ↓
Validated         ← Observed consistently across 2+ episodes.
    ↓
Standard          ← Established as Sara's natural pattern. Applied by default.
    ↓
Rule              ← Only after explicit human approval and documentation.
```

**Critical constraint:**

Nothing moves up this lifecycle automatically. Every promotion requires a human decision. The step from Standard to Rule is especially protected — it requires explicit approval and a log entry.

**Where knowledge lives:**

Knowledge at every stage is documented in `KNOWLEDGE_LOG.md` (defined in Sprint 002). This file is the project's production memory.

---

### How the two layers interact

The Rules Layer protects Sara's identity. It is the floor — content that violates a rule does not pass, regardless of how natural it sounds.

The Knowledge Layer improves Sara's voice. It is the ceiling that rises over time — the more the project learns, the better the transformation becomes.

Rules constrain. Knowledge refines.

Neither layer replaces the other.

---

## Module Stack

```
┌─────────────────────────────────┐
│  8. AI Optimization             │  ← Output layer
├─────────────────────────────────┤
│  7. Storytelling                │
├─────────────────────────────────┤
│  6. Rhythm                      │
├─────────────────────────────────┤
│  5. Speech Optimization         │
├─────────────────────────────────┤
│  4. Context Awareness           │
├─────────────────────────────────┤
│  3. Human Behavior              │
├─────────────────────────────────┤
│  2. Saudi Hejazi Dialect        │  ← Google AI transformation lives here
├─────────────────────────────────┤
│  1. Character Identity          │  ← Foundation layer
└─────────────────────────────────┘
```

Processing flows upward. The foundation must be stable before higher modules run.

Every module reads from both layers: it checks against the Rules Layer first, then applies current Knowledge Layer standards.

---

## Module Definitions

---

### Module 1 — Character Identity

**Responsibility:** Enforce Sara's character consistency across all output.

**Owns:**
* Sara's personality traits as defined in SARA_PERSONA_BIBLE.md
* Sara's behavioral rules — what she does and does not do
* Her knowledge boundaries — what she claims to know and does not claim
* Her relationship with the viewer

**Does not own:**
* Dialect (Module 2)
* Storytelling structure (Module 7)

**Layer relationship:** This module is almost entirely Rules Layer. Character identity does not evolve through observation — it is protected.

**Source of truth:** `docs/SARA_PERSONA_BIBLE.md`

**Validation question:** Does the output feel like Sara — specifically, authentically, consistently?

---

### Module 2 — Saudi Hejazi Dialect

**Responsibility:** Ensure all language output is accurate Hejazi Arabic — the dialect of Jeddah.

**Owns:**
* Dialect transformation — the Google AI call that converts input into Hejazi Arabic
* Core vocabulary and preferred expressions
* Prohibited phrases and dialect-breaking words
* Grammatical constructions natural to Hejazi speech

**Does not own:**
* Voice delivery or pronunciation (Module 5)
* Rhythm and pacing (Module 6)

**Google AI — scope and boundary:**

Google AI is called once inside this module. Its job is transformation: converting content that arrives in MSA or any other register into natural Hejazi Arabic aligned with Sara's voice.

Google AI does not validate the result. Validation is the module's responsibility, applied using the Rules Layer (prohibited words, forbidden constructions) and the Knowledge Layer (verified expressions, Standard patterns).

If Google AI produces output that violates a rule, the module rejects it and requests a revised transformation. The AI serves the module — not the other way around.

**Layer relationship:** Rules Layer defines what is forbidden. Knowledge Layer defines what is preferred and natural. Both are applied after transformation.

**Source of truth:** `docs/SARA_LANGUAGE_BIBLE.md`

**Validation question:** Does every sentence read as natural Jeddawi speech — and does it pass all Rules Layer constraints?

---

### Module 3 — Human Behavior

**Responsibility:** Ensure Sara's responses, reactions, and transitions feel like a real person — not a narrator, presenter, or AI system.

**Owns:**
* Natural hesitation and self-correction patterns
* Authentic reaction language (wonder, uncertainty, discovery)
* Conversational transitions rather than structured segues
* The difference between performed and genuine response

**Does not own:**
* Specific vocabulary (Module 2)
* Pacing and pause placement (Module 6)

**Layer relationship:** Rules Layer defines what Sara never does (performed emotions, presenter patterns). Knowledge Layer accumulates what natural human behavior looks like in Sara's voice across episodes.

**Source of truth:** `docs/SARA_PERSONA_BIBLE.md` — Behavioral Rules section

**Validation question:** Would a viewer believe this was said by a real person in a real moment?

---

### Module 4 — Context Awareness

**Responsibility:** Adapt output to the specific conditions of each episode — location, time of day, emotional register, and subject matter.

**Owns:**
* Location-specific language and sensory detail
* Temporal context — when Sara is there, what that means for the scene
* Emotional register appropriate to the story type
* Consistency of context throughout an episode

**Does not own:**
* Character identity (Module 1)
* Research verification — fact-checking is upstream of the engine

**Layer relationship:** Primarily Knowledge Layer — context patterns are discovered through production and accumulate over time. Rules Layer contributes environment constraints from SARA_ENVIRONMENT_BIBLE.md.

**Source of truth:** `docs/SARA_ENVIRONMENT_BIBLE.md`, `docs/STORY_TYPES.md`

**Validation question:** Does the output reflect the specific place, time, and story — or is it generic?

---

### Module 5 — Speech Optimization

**Responsibility:** Structure sentences for natural voice delivery — not for reading.

**Owns:**
* Sentence length — one breath, one idea
* Elimination of tanween endings on key lines
* Number formatting — always words, never numerals
* Tashkeel rules — applied where needed, never on colloquial words
* Removal of constructions that read well but sound wrong aloud

**Does not own:**
* Vocabulary choices (Module 2)
* Pause placement (Module 6)

**Layer relationship:** Mostly Rules Layer — these constraints are deterministic and do not change through observation.

**Source of truth:** `docs/SARA_VOICE_BIBLE.md`, `docs/SARA_LANGUAGE_BIBLE.md` — Pronunciation Notes section

**Validation question:** Can every sentence be read aloud naturally in one breath?

---

### Module 6 — Rhythm

**Responsibility:** Control the pacing, breathing, and silence of the episode.

**Owns:**
* Placement of `[pause]` and `[long pause]` markers
* Sentence grouping — when to let a thought land before continuing
* Pace targets: 100–120 Arabic words per minute
* Silence as a deliberate choice at significant moments

**Does not own:**
* What the sentences say (Modules 1–5)
* Narrative structure (Module 7)

**Layer relationship:** Rules Layer provides pace targets and marker syntax. Knowledge Layer accumulates where pauses land most effectively — this improves with each episode.

**Source of truth:** `docs/SARA_VOICE_BIBLE.md` — Pace and Rhythm section

**Validation question:** Does the episode breathe? Do the right moments have space?

---

### Module 7 — Storytelling

**Responsibility:** Ensure the episode follows Sara's storytelling framework — discovery before telling, context when the thread requires it, a closing that opens rather than concludes.

**Owns:**
* Story arc alignment — hook, question, thread, unexpected, discovery, close
* Context delivery — placed when needed, never front-loaded
* Closing structure — not a summary, not a lesson
* Narrative question integrity — the question must be real and must drive the arc

**Does not own:**
* Character voice (Modules 1–3)
* Story type classification — defined upstream before the engine runs

**Layer relationship:** Rules Layer enforces structure requirements from STORY_FRAMEWORK.md. Knowledge Layer accumulates what makes closings, discoveries, and openings land most powerfully in Sara's specific context.

**Source of truth:** `docs/STORY_FRAMEWORK.md`, `docs/STORY_TYPES.md`

**Validation question:** Does the story move like a discovery — or like a presentation?

---

### Module 8 — AI Optimization

**Responsibility:** Structure the final output for reliable, consistent AI generation — optimized for Veo prompt construction.

**Owns:**
* Output formatting conventions for downstream AI tools
* Marker syntax — voice direction markers, scene markers, pause markers
* Removing ambiguity that would produce inconsistent AI output
* Packaging the engine output into the format Veo prompt generation expects

**Does not own:**
* The content or language of the output (Modules 1–7)
* Veo prompt generation itself — that is downstream

**Layer relationship:** Entirely Rules Layer. Output format is deterministic — defined once, applied consistently.

**Source of truth:** Defined in Sprint 002 and beyond.

**Validation question:** Is the output structured so that AI generation produces consistent, predictable results?

---

## Module Interaction Rules

1. **Foundation before superstructure.** Module 1 must be stable before Module 2 runs. Higher modules may return content to a lower module for correction — they do not bypass it.

2. **Rules Layer checked first.** In every module, Rules Layer constraints are applied before Knowledge Layer standards. A rule violation stops processing. Knowledge standards refine what passes.

3. **One owner per concern.** If a question about output belongs to two modules, one of them is wrong. Resolve ownership before implementation.

4. **Bibles are read-only inputs.** Modules read from the bibles. They do not modify them. Bible updates are Content System changes — not engine changes.

5. **Google AI is scoped to Module 2.** No other module calls an external AI. If Module 2's implementation changes, no other module is affected.

6. **Knowledge promotion requires human approval.** A module may flag a pattern for potential promotion. The promotion decision is made outside the engine — by a human, documented in `PRODUCTION_DECISIONS_LOG.md`.
