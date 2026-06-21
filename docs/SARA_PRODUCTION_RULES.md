# Sara Production Rules

## Purpose

This document defines how episodes are produced, reviewed, and improved.

Following these rules prevents quality drift and maintains consistency over time.

This document is part of Sara Content System v1. It operates in conjunction with:
* `docs/SARA_PERSONA_BIBLE.md` — who Sara is
* `docs/STORY_FRAMEWORK.md` — how Sara discovers and tells a story
* `docs/STORY_TYPES.md` — how to classify the narrative question before writing
* `docs/STORY_RESEARCH_RULES.md` — how to research a story before production
* `docs/STORY_FACT_CHECKING.md` — how to verify factual claims before production
* `docs/SARA_LANGUAGE_BIBLE.md` — how Sara speaks
* `docs/SARA_VOICE_BIBLE.md` — how Sara sounds

---

## The Improvement Loop

Every episode follows this cycle:

```
Problem
  → Analyze
    → Fix
      → Test
        → Document
          → Repeat
```

This applies to:
* Script quality issues
* Visual inconsistencies
* Voice delivery problems
* Environment accuracy failures
* Pacing and structure improvements

---

## The Single Variable Rule

**Never change multiple major variables at once.**

If an episode has a problem:
1. Identify the one root cause.
2. Change only that one thing.
3. Test the result.
4. Document what worked.

Changing multiple variables simultaneously makes it impossible to know what fixed the problem — and what broke something new.

---

## Episode Production Stages

### Stage 1 — Concept
* Identify the subject and location.
* Complete research stages 1 and 2 from STORY_RESEARCH_RULES.md — survey and story discovery.
* Define the narrative question (the genuine question Sara wants to follow).
* Identify the story type from STORY_TYPES.md. A subject without a story type has not found its story yet.
* Confirm the episode fits Sara's identity and project vision (see SARA_PERSONA_BIBLE.md).
* **Gate:** Do not proceed without a clear narrative question and identified story type.

### Stage 2 — Research and Fact Foundation
* Complete research stages 3 and 4 from STORY_RESEARCH_RULES.md — thread research and gap identification.
* Map all known facts, uncertain facts, and gaps before writing begins.
* Identify any claims that will need Tier 1 or Tier 2 sources before the script is finalized.
* **Gate:** Do not proceed to script without the gap map complete.

### Stage 3 — Script
* Write the first draft following STORY_FRAMEWORK.md — discovery before telling, context when the thread requires it.
* Review against SARA_LANGUAGE_BIBLE.md.
* Read the script out loud.
* Revise until every sentence sounds natural in Hejazi Arabic.
* Complete the full fact-check workflow from STORY_FACT_CHECKING.md.
* Finalize script.
* **Gate:** No script proceeds to voice production without a completed fact-check record.

### Stage 4 — Visual Production
* Gather reference images for the location. File in the correct `/references/` subfolder.
* Define key shots aligned to the story's thread — not a location tour.
* Generate visuals.
* Review visuals against SARA_ENVIRONMENT_BIBLE.md for location accuracy.
* Review Sara's appearance for character consistency against locked assets.

### Stage 5 — Voice Production
* Generate voice from approved voice model.
* Review against SARA_VOICE_BIBLE.md — pronunciation, pace, accent preservation.
* If issues found — fix the script or speech direction, not the voice model.
* Finalize voice.

### Stage 6 — Assembly
* Combine visuals and voice.
* Review pacing — does the story breathe at the right moments?
* Add music if applicable (see music rules below).
* Final review pass.

### Stage 7 — Review and Approval
* Watch the episode as a viewer, not as a producer.
* Check the episode review checklist.
* Document any issues found.
* Approve or return to relevant stage.

### Stage 8 — Documentation
* Update episode log with production notes.
* Document any new rules or decisions made during production.
* File fact-check record with episode log.
* Record any significant production decisions in `PRODUCTION_DECISIONS_LOG.md`.

---

## Episode Review Checklist

Before an episode is approved for publishing:

**Character**
- [ ] Sara looks like Sara (face consistency)
- [ ] Sara's voice sounds like Sara (voice consistency)
- [ ] Sara's personality comes through in the script

**Story**
- [ ] The episode has a clear narrative question (not just a subject)
- [ ] The story type was identified before writing (from STORY_TYPES.md)
- [ ] The opening begins in a specific moment — no introductory background, no greeting
- [ ] Context is delivered when the thread requires it, not front-loaded
- [ ] The story contains something unexpected — a genuine discovery
- [ ] The human dimension is present — a specific person, historical or current
- [ ] The closing opens something rather than concluding — the viewer is still thinking
- [ ] All factual claims are verified or honestly framed as uncertain (fact-check complete)

**Language**
- [ ] All dialogue follows SARA_LANGUAGE_BIBLE.md
- [ ] No formal MSA phrasing
- [ ] Every sentence sounds natural when spoken

**Environment**
- [ ] The location is specific and recognizable
- [ ] Lighting is appropriate
- [ ] No visual inconsistencies between shots

**Overall**
- [ ] A viewer would believe this is a real person
- [ ] The episode could stand alone as content
- [ ] The episode strengthens Sara's long-term identity

---

## Music Rules

Music is supporting, not decorative.

* Music volume must be low enough that Sara's voice is always the primary element.
* Music should match the emotional tone of the scene.
* Do not use recognizable commercial tracks.
* Preferred: ambient, instrumental, culturally appropriate to location.
* Silence is a valid choice — especially in historical or contemplative moments.

---

## Asset Management Rules

* All visual assets go in `/assets/`.
* All reference images go in `/references/`.
* All scripts go in `/episodes/`.
* Nothing sits in the root folder except README.md and .gitignore.

---

## Version Control Rules

* Commit in small, reviewable steps.
* Commit message format: `type(scope): short description`
  * `docs(bible):` — changes to character, voice, language, environment, or persona bibles
  * `docs(story-engine):` — changes to story framework, types, research, or fact-checking documents
  * `docs(production):` — changes to production rules or decision log
  * `feat(episode):` — new episode, template, or prompt
  * `fix(content):` — corrections to existing scripts or episode content
  * `fix(docs):` — corrections to documentation
  * `chore:` — folder structure, file moves, non-content work

* Do not commit large unreviewed batches.
* Each commit should be understandable on its own.

---

## Decision Log

All significant production decisions must be recorded.

See `/episodes/PRODUCTION_DECISIONS_LOG.md`.

When in doubt about whether a decision should be logged — log it.

Future Sara (and future producers) will thank you.
