# Sara Language Engine

## What This Is

Sara Language Engine is the processing layer that every episode must pass through before a Veo prompt is generated.

It is not a prompt library.
It is not a script template.
It is not a voice model.

It is the architectural system that transforms a raw story concept into output that is fully aligned with Sara's character identity, dialect, rhythm, and storytelling behavior — and that is optimized for AI generation.

---

## Why It Exists

Sara's bibles (Voice, Language, Persona, Story Framework) define the rules. The Language Engine is the system that applies them consistently at production scale.

Without the engine, every episode requires manual alignment against multiple documents, creating inconsistency over time. With the engine, alignment is built into the process — not dependent on individual judgment at each production step.

---

## Scope

The Language Engine owns exactly eight responsibilities:

| # | Responsibility | What It Controls |
|---|---------------|-----------------|
| 1 | Character Identity | Sara's consistency as a person across all output |
| 2 | Saudi Hejazi Dialect | Linguistic accuracy and dialect integrity |
| 3 | Human Behavior | Naturalness of speech patterns and reactions |
| 4 | Context Awareness | Adaptation to location, time, mood, and subject |
| 5 | Speech Optimization | Sentence structure optimized for voice delivery |
| 6 | Rhythm | Pacing, pauses, breathing room within scripts |
| 7 | Storytelling | Narrative structure aligned with Story Framework |
| 8 | AI Optimization | Output structured for reliable AI generation |

Each responsibility maps to a module in ENGINE_ARCHITECTURE.md.

---

## What Goes In — What Comes Out

**Input:** A story concept — the narrative question, story type, and research foundation from Sara Content System.

**Output:** Engine-processed content ready for Veo prompt generation.

Nothing reaches Veo without passing through all eight modules.

---

## Independence Principle

The Language Engine is completely independent.

It does not depend on any external tool, service, or platform to function. External systems — including Google AI for dialect transformation — are implementations used by specific modules, not dependencies the engine requires to exist.

The architecture is defined here. Implementation is defined per module in ENGINE_ARCHITECTURE.md.

---

## Relationship to Sara Content System

The Language Engine does not replace the Sara Content System bibles. It operationalizes them.

| Sara Content System | Language Engine |
|--------------------|----------------|
| Defines the rules | Applies the rules |
| SARA_LANGUAGE_BIBLE.md | Dialect module |
| SARA_VOICE_BIBLE.md | Speech + Rhythm modules |
| SARA_PERSONA_BIBLE.md | Character Identity module |
| STORY_FRAMEWORK.md | Storytelling module |
| STORY_RESEARCH_RULES.md + STORY_FACT_CHECKING.md | Context Awareness module |

When a bible is updated, the corresponding module is updated. They move together.

---

## What This Is Not

* Not a replacement for research or fact-checking.
* Not a creative shortcut — the story must exist before the engine runs.
* Not a Veo prompt generator — the engine prepares the input; prompt generation is downstream.
* Not dependent on Mantooq or any single external platform.
