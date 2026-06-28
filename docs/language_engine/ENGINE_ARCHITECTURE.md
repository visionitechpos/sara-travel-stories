# Engine Architecture

## Overview

The Language Engine is composed of eight modules. Each module owns exactly one responsibility. No module duplicates the work of another.

Modules are ordered by processing layer — from identity foundation through AI-ready output. Each layer depends on the layers below it.

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
│  2. Saudi Hejazi Dialect        │
├─────────────────────────────────┤
│  1. Character Identity          │  ← Foundation layer
└─────────────────────────────────┘
```

Processing flows upward. The foundation must be stable before higher layers run.

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

**Source of truth:** `docs/SARA_PERSONA_BIBLE.md`

**Validation question:** Does the output feel like Sara — specifically, authentically, consistently?

---

### Module 2 — Saudi Hejazi Dialect

**Responsibility:** Ensure all language output is accurate Hejazi Arabic — the dialect of Jeddah.

**Owns:**
* Core vocabulary and preferred expressions
* Prohibited phrases and dialect-breaking words
* Grammatical constructions natural to Hejazi speech
* Dialect transformation when input arrives in MSA or another register

**Does not own:**
* Voice delivery or pronunciation (Module 5)
* Rhythm and pacing (Module 6)

**Source of truth:** `docs/SARA_LANGUAGE_BIBLE.md`

**Technology:** Google AI is used at this module for dialect transformation — converting content that arrives in MSA or non-Hejazi registers into accurate Hejazi Arabic. This is an implementation detail of this module, not an engine dependency.

**Validation question:** Does every sentence read as natural Jeddawi speech?

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

**Source of truth:** Defined in Sprint 002 and beyond.

**Validation question:** Is the output structured so that AI generation produces consistent, predictable results?

---

## Module Interaction Rules

1. **Foundation before superstructure.** Module 1 must be stable before Module 2 runs. Module 2 before 3, and so on. Higher modules may send content back to a lower module for correction — they do not bypass it.

2. **One owner per concern.** If a question about output belongs to two modules, one of them is wrong. Resolve ownership before implementation.

3. **Bibles are read-only inputs.** Modules read from the bibles. They do not modify them. If a bible needs updating, that is a Content System change — not an engine change.

4. **External tools are module-level.** Google AI for dialect transformation is used inside Module 2. No other module depends on it. If Module 2's implementation changes, no other module is affected.
