# Sara Production Rules

## Purpose

This document defines how episodes are produced, reviewed, and improved.

Following these rules prevents quality drift and maintains consistency over time.

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
* Define the story.
* Identify the location.
* Write the core question the episode answers.
* Confirm the episode fits Sara's identity and project vision.

### Stage 2 — Script
* Write the first draft.
* Review against SARA_LANGUAGE_BIBLE.md.
* Read the script out loud.
* Revise until every sentence sounds natural.
* Finalize script.

### Stage 3 — Visual Production
* Gather reference images for the location.
* Define key shots.
* Generate visuals.
* Review visuals for environment consistency.
* Review Sara's appearance for character consistency.

### Stage 4 — Voice Production
* Generate voice from approved voice model.
* Review against SARA_VOICE_BIBLE.md.
* If issues found — fix the script or speech direction, not the voice model.
* Finalize voice.

### Stage 5 — Assembly
* Combine visuals and voice.
* Review pacing.
* Add music if applicable (see music rules below).
* Final review pass.

### Stage 6 — Review and Approval
* Watch the episode as a viewer, not as a producer.
* Check the episode review checklist.
* Document any issues found.
* Approve or return to relevant stage.

### Stage 7 — Documentation
* Update episode log with production notes.
* Document any new rules or decisions made during production.
* File reference images in the correct folder.

---

## Episode Review Checklist

Before an episode is approved for publishing:

**Character**
- [ ] Sara looks like Sara (face consistency)
- [ ] Sara's voice sounds like Sara (voice consistency)
- [ ] Sara's personality comes through in the script

**Story**
- [ ] The episode tells a clear story
- [ ] There is something interesting or unexpected in the story
- [ ] The opening creates immediate interest
- [ ] The closing is complete, not just an ending

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
* Commit message format: `type: short description`
  * `docs:` — documentation changes
  * `feat:` — new episode or template
  * `fix:` — corrections to existing content
  * `refactor:` — restructuring without content change
  * `chore:` — folder structure, file moves, non-content work

* Do not commit large unreviewed batches.
* Each commit should be understandable on its own.

---

## Decision Log

All significant production decisions must be recorded.

See `/episodes/PRODUCTION_DECISIONS_LOG.md`.

When in doubt about whether a decision should be logged — log it.

Future Sara (and future producers) will thank you.
