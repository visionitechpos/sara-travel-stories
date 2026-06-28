# Engine Pipeline

## Overview

The pipeline defines how content moves through the Language Engine — from story concept to engine-processed output ready for Veo prompt generation.

The pipeline has five stages. Each stage has a clear input, a clear output, and a gate condition. No stage begins until the previous stage passes its gate.

---

## Pipeline Diagram

```
[ Story Concept ]
       │
       ▼
┌─────────────────┐
│  Stage 1        │  Intake & Validation
│                 │  Verify the story is ready for the engine
└────────┬────────┘
         │ GATE: story concept passes all five readiness checks
         ▼
┌─────────────────┐
│  Stage 2        │  Foundation Pass
│                 │  Modules 1, 2, 3 — Identity, Dialect, Human Behavior
└────────┬────────┘
         │ GATE: output reads as Sara, in Hejazi Arabic, like a real person
         ▼
┌─────────────────┐
│  Stage 3        │  Context & Speech Pass
│                 │  Modules 4, 5 — Context Awareness, Speech Optimization
└────────┬────────┘
         │ GATE: output is location-specific and voice-delivery ready
         ▼
┌─────────────────┐
│  Stage 4        │  Rhythm & Story Pass
│                 │  Modules 6, 7 — Rhythm, Storytelling
└────────┬────────┘
         │ GATE: episode breathes correctly and moves like a discovery
         ▼
┌─────────────────┐
│  Stage 5        │  AI Optimization Pass
│                 │  Module 8 — AI Optimization
└────────┬────────┘
         │ GATE: output is structured for consistent AI generation
         ▼
[ Engine Output — Veo Prompt Generation Ready ]
```

---

## Stage Definitions

---

### Stage 1 — Intake and Validation

**Purpose:** Confirm the story concept is ready before the engine processes it.

The engine does not fix unprepared input. If the story is not ready, it returns to the Content System — not to Stage 2.

**Required inputs:**

| Input | Source |
|-------|--------|
| Narrative question | Defined before production (STORY_FRAMEWORK.md) |
| Story type | Identified from STORY_TYPES.md |
| Research foundation | Stages 1–4 complete (STORY_RESEARCH_RULES.md) |
| Fact-check record | All claims verified or framed (STORY_FACT_CHECKING.md) |
| Gap map | Unknowns identified and handling decisions made |

**Gate — five conditions, all required:**

- [ ] Narrative question is clear and stated in one sentence
- [ ] Story type is identified
- [ ] All factual claims in the concept are verified or marked as uncertain
- [ ] The unexpected element is present — at least one discovery
- [ ] The human dimension is present — at least one specific person

If any condition fails: return to Content System. Do not enter Stage 2.

---

### Stage 2 — Foundation Pass

**Modules:** 1 (Character Identity), 2 (Saudi Hejazi Dialect), 3 (Human Behavior)

**Purpose:** Establish Sara's voice at its most fundamental level. By the end of this stage, the content sounds like Sara — in her dialect, as a real person.

**What happens:**

* Module 1 reviews the concept against Sara's personality, behavioral rules, and knowledge boundaries. Any content that contradicts Sara's character is flagged and rewritten.
* Module 2 transforms all language into accurate Hejazi Arabic. MSA constructions are replaced. Dialect-breaking words are removed. Prohibited phrases are caught.
* Module 3 checks that reactions, transitions, and expressions feel genuinely human — not narrated, not performed.

**Gate:**

- [ ] Content is free of character contradictions
- [ ] All language is Hejazi Arabic — no MSA constructions, no prohibited phrases
- [ ] Reactions and transitions read as natural speech, not scripted delivery

---

### Stage 3 — Context and Speech Pass

**Modules:** 4 (Context Awareness), 5 (Speech Optimization)

**Purpose:** Ground the content in its specific location and time, and optimize every sentence for voice delivery.

**What happens:**

* Module 4 checks that the language reflects the specific place, time of day, and emotional register of the episode. Generic descriptions are replaced with specific, sensory detail appropriate to the location. Context drift — where the language stops feeling like this place and starts feeling like any place — is corrected.
* Module 5 reviews sentence structure for voice delivery. Sentences that are too long for one breath are broken. Tanween endings on key lines are removed. Numbers are confirmed as written words. Tashkeel is reviewed — present where it aids delivery, absent from all colloquial words.

**Gate:**

- [ ] Output is location-specific — it could not be any other place
- [ ] Every sentence is deliverable in one natural breath
- [ ] No tanween on emotionally weighted lines
- [ ] No numerals — all numbers written as words
- [ ] No tashkeel on colloquial vocabulary

---

### Stage 4 — Rhythm and Story Pass

**Modules:** 6 (Rhythm), 7 (Storytelling)

**Purpose:** Shape the episode into a story that moves like a discovery and breathes at the right moments.

**What happens:**

* Module 7 reviews the narrative arc against STORY_FRAMEWORK.md. Does the episode begin in a specific moment? Does context arrive when the thread requires it — not before? Is the unexpected element present and unforced? Does the closing open something rather than conclude? If the arc is wrong at this stage, content is restructured.
* Module 6 places pause markers and controls pacing. Silence is placed deliberately — before discoveries, at significant moments, at the close. Word pace is checked against the 100–120 Arabic words per minute target.

**Note:** Module 7 runs before Module 6. The structure must be correct before the rhythm is set.

**Gate:**

- [ ] Episode begins in a specific moment — no introductory background
- [ ] Context is delivered inside the story, not before it
- [ ] The unexpected element is present and lands with weight
- [ ] The closing opens rather than concludes
- [ ] Pause markers are placed at discovery moments and the close
- [ ] Estimated pace falls within 100–120 Arabic words per minute

---

### Stage 5 — AI Optimization Pass

**Module:** 8 (AI Optimization)

**Purpose:** Package the engine output into the format that Veo prompt generation expects — structured, unambiguous, consistent.

**What happens:**

* All voice direction markers are confirmed in correct syntax.
* Scene markers and transitions are structured for AI interpretation.
* Ambiguities that would produce inconsistent AI generation are resolved.
* The output is packaged in the format defined for downstream Veo prompt construction.

**The specific format and conventions for this stage are defined in Sprint 002.**

**Gate:**

- [ ] All markers are in correct syntax
- [ ] No ambiguities remain in the output
- [ ] Output matches the format expected by Veo prompt generation

---

## Return Conditions

At any stage, content may be returned to an earlier stage or back to the Content System.

| Return to | Reason |
|-----------|--------|
| Stage 1 (Intake) | A foundational issue was discovered in a later stage — wrong story type, missing research, unverified claim |
| Stage 2 (Foundation) | Context or speech pass reveals a character or dialect issue |
| Stage 3 (Context/Speech) | Rhythm pass reveals structural problems that affect sentence-level work |
| Content System | The story itself is not ready — the question is not real, the research is incomplete, or the unexpected element is absent |

Returning is not failure. It is the pipeline functioning correctly.

---

## Engine Output

The output of Stage 5 is a single structured document per episode containing:

* The processed script — in Sara's voice, Hejazi dialect, with all markers
* The story type and narrative question (for reference)
* Context notes — location, time, emotional register
* Any acknowledged uncertainties carried through from fact-checking

This document is the input to Veo prompt generation. Nothing else enters Veo.
