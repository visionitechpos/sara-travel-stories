# Minimum Working Language Engine — Pipeline

## Purpose

This document defines the first practical pipeline of the Sara Language Engine.

The goal is one thing: transform a draft script into a Sara-ready script that can be tested in production.

This is Version 1. It is designed to work, not to be complete. Every stage is as simple as it needs to be — no more.

---

## Pipeline

```
[ Draft Script ]
       │
       ▼
┌─────────────────────────┐
│  Stage 1                │
│  Pre-Transform Check    │
└──────────┬──────────────┘
           │ PASS or STOP
           ▼
┌─────────────────────────┐
│  Stage 2                │
│  Dialect Transformation │  ← Google AI
└──────────┬──────────────┘
           │
           ▼
┌─────────────────────────┐
│  Stage 3                │
│  Sara Validation        │
└──────────┬──────────────┘
           │ PASS or RETURN to Stage 2
           ▼
┌─────────────────────────┐
│  Stage 4                │
│  Voice Optimization     │
└──────────┬──────────────┘
           │
           ▼
[ Final Script ]
```

---

## Stage 1 — Pre-Transform Check

**Input:** Draft script in any Arabic register (MSA, mixed, or informal)

**Output:** Approved draft ready for transformation — OR — rejection with specific reasons listed

**Responsibility:**

Confirm the script is ready before transformation begins. This stage does not fix problems. It catches them early, before Google AI runs, so that transformation is not wasted on a script that will fail later.

**Minimum checks for V1:**

- [ ] A narrative question exists — the story has a clear direction
- [ ] Story type is identified (from STORY_TYPES.md)
- [ ] The script has an opening that begins in a moment — no greeting, no self-introduction
- [ ] No prohibited phrases are already present (from SARA_LANGUAGE_BIBLE.md)
- [ ] No factual claims are presented as certain without a source

**If any check fails:** Stop. Return the script to the writer with the specific failure noted. Do not proceed to Stage 2.

**Source of truth:** `docs/STORY_FRAMEWORK.md`, `docs/STORY_TYPES.md`, `docs/SARA_LANGUAGE_BIBLE.md` — Prohibited Phrases section

---

## Stage 2 — Dialect Transformation

**Input:** Draft script that has passed Stage 1

**Output:** The same script rewritten in Sara's natural Hejazi Arabic

**Responsibility:**

Transform the script's language register into Sara's dialect. This is the only stage where Google AI is used. Its job is linguistic transformation — not content judgment.

**What transformation covers:**

- MSA vocabulary → Hejazi equivalents (إيش، بس، يعني، وبعدين، etc.)
- Formal sentence structures → natural spoken constructions
- Over-articulated forms → natural contractions (هذا الـ → هالـ)
- Formal transitions → Hejazi conversational transitions

**What transformation does not do:**

- Does not restructure the story
- Does not add or remove facts
- Does not fix a weak script
- Does not validate the result — that is Stage 3

**Context given to Google AI:**

Sara's core vocabulary and dialect profile from `docs/SARA_LANGUAGE_BIBLE.md`. The transformation instruction must specify: Hejazi Arabic, dialect of Jeddah, natural spoken register, not MSA, not Najdi, not Egyptian.

**Source of truth:** `docs/SARA_LANGUAGE_BIBLE.md` — Core Vocabulary, Sentence Structure, Language Register sections

---

## Stage 3 — Sara Validation

**Input:** Transformed Hejazi script from Stage 2

**Output:** Validated script ready for Stage 4 — OR — flagged script returned to Stage 2 with specific issues listed

**Responsibility:**

Verify that the transformed script actually sounds like Sara and passes all Rules Layer constraints. Google AI transformation is not perfect. This stage catches what it misses.

**Minimum checks for V1:**

**Identity checks:**
- [ ] No prohibited phrases survived transformation
- [ ] No dialect-breaking words (شلون، إيه، أيوه، هيك، قديش)
- [ ] No MSA constructions survived (حيث، إذ، بيد أن، نظراً لـ)
- [ ] No presenter-style opening (أهلاً وسهلاً، أنا سارة، في هذا الفيديو)
- [ ] No channel mechanics (لا تنسوا الاشتراك، تابعوني)

**Dialect checks:**
- [ ] Core Sara vocabulary is present (إيش، بس، يعني appear naturally)
- [ ] Numbers are written as words, not numerals
- [ ] No tashkeel on colloquial words (بس، يعني، صراحة)

**If validation fails:** Return to Stage 2 with the specific issues listed. The transformation instruction is adjusted and Stage 2 runs again. Maximum two retries before escalating to manual correction.

**Source of truth:** `docs/SARA_LANGUAGE_BIBLE.md` — all sections

---

## Stage 4 — Voice Optimization

**Input:** Validated script from Stage 3

**Output:** Final script with voice markers, optimized sentence structure, and delivery directions

**Responsibility:**

Prepare the script for voice generation. Every sentence must be deliverable in one natural breath. Pauses must be placed where the story needs them. The output of this stage is what goes into production.

**What this stage does:**

**Sentence optimization:**
- Break any sentence longer than one natural breath into two
- Remove tanween endings on emotionally weighted lines
- Confirm all numbers are written as full Arabic words

**Pause markers:**
- `[pause]` — brief beat between thoughts
- `[long pause]` — significant moment, discovery, or emotional weight
- `[slow]` — deliberate pacing for important lines
- Place a `[long pause]` before the closing line of every episode

**Pace check:**
- Estimate word count against 100–120 Arabic words per minute target
- Flag if the script runs significantly over or under

**Tashkeel review:**
- Add tashkeel only where pronunciation is genuinely ambiguous
- Remove any tashkeel from colloquial words

**Source of truth:** `docs/SARA_VOICE_BIBLE.md`, `docs/SARA_LANGUAGE_BIBLE.md` — Pronunciation Notes section

---

## Final Script

The output of Stage 4 is the Final Script.

**What it contains:**

- The complete script in Sara's Hejazi Arabic
- All voice markers in place
- A header with: story type, narrative question, location, estimated duration
- Any acknowledged uncertainties carried from fact-checking

**What it does not contain:**

- Veo scene descriptions — those are built from the Final Script in a separate process
- Production notes — those go in the episode log

---

## Iteration Protocol

After each test run of the pipeline, document the following:

**What to log (in `KNOWLEDGE_LOG.md` — Sprint 003):**

- Which stage produced the most issues
- What the Google AI transformation got wrong consistently
- What the validation caught that should have been caught earlier
- Any expression or pattern that appeared naturally and sounded right

**What to improve next:**

Start with Stage 2. The quality of the transformation instruction given to Google AI is the highest-leverage improvement in V1.

If the same validation failure appears in two consecutive scripts, promote it to a Stage 1 check. Catch it before transformation, not after.

---

## What This Pipeline Is Not

This pipeline does not replace the Content System. Research, fact-checking, and story structure happen before Stage 1. If the story is not ready, the pipeline cannot fix it.

This pipeline does not guarantee perfect output on the first run. It guarantees a consistent, improvable process. Version 1 is designed to be tested, not to be final.
