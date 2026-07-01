# Sara Production Guide — Veo

## Purpose

This document translates Veo's engineering knowledge into specific guidance for Sara production.

It does not repeat what is in the other Veo knowledge base documents. It applies that knowledge to Sara's specific situation.

---

## Decision Resolved — Native Veo Dialogue (2026-07-02)

**Sara speaks through Veo's native dialogue. Audio is not replaced in post-production.**

This was an open architectural question requiring experimentation (Experiment H-01, never run). It is now resolved by real production evidence instead: Sara's voice — defined natively within her Veo Character (see `SARA_VOICE_BIBLE.md`) — has already been tested successfully across several produced vlogs. H-01 is no longer needed; the question it was designed to answer has been answered by actual production, not a controlled test.

| | Native Veo Dialogue (chosen) | Audio Replacement (not used) |
|---|---|---|
| **How** | Arabic dialogue written in prompt; Veo generates voice natively as part of the Character | Generate clip visually; process audio through Language Engine; align in post |
| **Dialect quality** | Confirmed through multiple successful vlogs | Would have required a separate Language Engine audio pipeline |
| **Lip sync** | Native | N/A |
| **Subtitle risk** | Present — see `AUDIO_AND_DIALOGUE.md` workarounds, still required | N/A |
| **Voice consistency** | Confirmed in production | N/A |
| **Complexity** | Simpler workflow — voice is bundled with the Character, not a separate step | N/A |

**What this means for the Language Engine / Character Cognition Engine:** its output (the Final Script) is spoken directly by Veo — there is no downstream audio-replacement stage. The subtitle-suppression techniques in `AUDIO_AND_DIALOGUE.md` remain necessary regardless of this decision.

---

## Sara's Character Reference Package

Before any production begins, a reference package must be created and approved:

**Required:**
- 3 Sara reference images (front, three-quarter, full-body context) — approved against SARA_CHARACTER_BIBLE.md
- Sara standard character descriptor block (text, used in every prompt)
- Sara standard audio environment specification (used in every prompt)

**Where they live:** `/assets/sara/reference/`

**Rule:** Reference images, once approved, are production assets. They are not regenerated unless a character update decision is documented and approved.

---

## Sara's Standard Prompt Block

Every Sara clip prompt must include these three sections verbatim:

```
[CHARACTER]
[Sara character descriptor — defined after reference image approval]

[AUDIO ENVIRONMENT]
[Sara audio spec — defined after audio approach is chosen]

[TECHNICAL]
No subtitles. No captions. No burned-in text. No watermarks visible. 
Clean frame. 24fps.
```

These three sections are non-negotiable. They are added to every clip prompt, every time, before any scene-specific content.

---

## Episode Production Workflow

### Phase 1 — Script Foundation (Language Engine)

1. Write draft script
2. Run through MWLE pipeline (Pre-Transform → Dialect Transformation → Sara Validation → Voice Optimization)
3. Output: Final Script with pause markers, Hejazi Arabic, voice-ready

### Phase 2 — Shot Planning

1. Break Final Script into clip units (each clip = 4–8 seconds of screen time)
2. For each clip define:
   - Duration (4, 6, or 8 seconds)
   - Camera shot type
   - Sara's action (moving, standing, looking)
   - Dialogue for this clip (one sentence maximum)
   - Audio environment for this clip
   - Location / scene details
3. Output: Shot list with one entry per Veo generation

### Phase 3 — Veo Generation

For each clip in the shot list:
1. Build the Veo prompt using Sara's standard prompt block + clip-specific details
2. Generate with Veo 3.1 using reference images
3. Review clip: character appearance, audio quality, subtitle presence
4. If rejected: regenerate with adjusted prompt
5. If accepted: download and file in `/assets/episodes/[episode-id]/clips/`

### Phase 4 — Audio Processing (if using audio replacement)

1. Process Final Script audio through approved voice source
2. Apply Language Engine Voice Optimization (pause markers, rhythm)
3. Generate audio file per clip
4. Align audio to Veo clip lip movement in post-production

### Phase 5 — Assembly

1. Assemble clips in order
2. Add transitions
3. Apply final audio mix
4. Review against Episode Review Checklist (SARA_PRODUCTION_RULES.md)
5. Export

---

## Jeddah Location Guidance for Veo

`[INFERENCE based on Environment Bible + Veo prompt engineering]`

### Al-Balad — Al-Khobar Street Alley

Key elements to specify in every Al-Balad clip prompt:

**Built environment:**
- Buildings 5–7 stories tall, narrow facade profile, canyon-like alley quality
- Rawasheen (wooden latticed bay windows) on upper floors, projecting over the alley
- Walls: coral stone (madaif), weathered, aged texture
- Ground: worn stone paving, narrow width

**Signs of habitation (not ruin):**
- Satellite dishes and water tanks visible on rooftops
- Occasional laundry visible
- Active occupation — doors open, life present

**Light:**
- Early morning: warm low-angle light entering alley ends, deep shadow in the alley itself
- Late afternoon: golden from above, walls glowing

**Sample establishing clip prompt:**
```
Medium wide shot, a young Saudi woman in a dark abaya walking slowly 
through a narrow historic alley in Jeddah's Al-Balad district. The alley 
is flanked by 5-7 story traditional buildings with ornate wooden rawashin 
window screens projecting from upper floors. Weathered coral stone walls, 
worn stone paving. Morning light just beginning to enter the alley from 
one end. Visible satellite dishes and water tanks on rooftops above. 
The woman pauses and looks upward at the wooden screens. 
Ambient: quiet morning, faint distant city sounds, breeze.
No subtitles. No captions. No burned-in text.
```

### Corniche — Early Morning

**Key elements:**
- Wide waterfront promenade
- Red Sea water: clear turquoise in shallows, deep blue at distance
- City skyline behind, but not dominant
- Time: before sunrise / just after — sky transitioning, low light
- Minimal foot traffic at this hour

---

## Priority Experiments for Sara

Before the first full episode, these must be tested:

| Priority | Experiment | Decision It Unlocks |
|----------|-----------|---------------------|
| ~~1~~ | ~~Arabic Hejazi dialogue quality in Veo~~ | **Resolved by production evidence — native audio confirmed, see above. No longer needed.** |
| 1 | Subtitle behavior with Arabic dialogue | How to handle the subtitle problem |
| 2 | Reference image consistency across 10 clips | Whether reference images are stable enough for production |
| 3 | Voice consistency across separate generations — still worth confirming despite native audio being chosen | Whether drift appears across many clips in practice |
| 4 | Prompt rewriter on vs. off | Whether to disable rewriter by default |

Each experiment must be documented in `docs/language_engine/tests/` following the TEST_RUN format.

---

## Clip Review Checklist

Before any Veo clip is accepted into production:

**Character:**
- [ ] Sara's face matches reference images — same person, same features
- [ ] Clothing is consistent with the episode's established look
- [ ] No unexpected character drift from previous clips in the episode

**Scene:**
- [ ] Location matches the environment bible description
- [ ] **CRITICAL — any recognizable real landmark (e.g., the fish sculpture) is checked side-by-side against its real reference photo — exact shape, position, and proportions must match.** A local Jeddah viewer will recognize this landmark precisely; a mismatch is an instant, unrecoverable AI tell. See `LIMITATIONS_AND_UNKNOWNS.md` — "Location/object reference images do not guarantee exact spatial placement."
- [ ] Lighting is appropriate for the time of day
- [ ] No anachronistic elements in the background

**Audio:**
- [ ] If native audio: dialogue is intelligible, correctly pronounced, correct language
- [ ] If native audio: no hallucinated music or sound effects
- [ ] Audio environment matches what was specified

**Technical:**
- [ ] No visible subtitles or text overlays
- [ ] 24fps, no frame rate artifacts
- [ ] Resolution is correct for intended use

**Narrative:**
- [ ] The clip advances the story — it is not a holding shot
- [ ] Camera framing is intentional, not generic

---

## What Veo Will Do Well for Sara

`[INFERENCE]`

- **Environmental scene-setting.** Jeddah locations — Al-Balad alleys, Corniche waterfront — will generate convincingly if described in specific sensory detail.
- **Atmospheric lighting.** Veo handles cinematic lighting well. Early morning light in Al-Balad, golden afternoon on the Corniche, will produce strong visual results.
- **Slow, deliberate camera movement.** Sara's contemplative pacing suits Veo's strength with slower, directed shots.
- **Character-in-environment establishing shots.** Wide or medium shots of Sara in a location, before dialogue begins, should be highly reliable.

---

## What Veo Will Struggle With for Sara

`[CONFIRMED + INFERENCE]`

- **Arabic dialogue quality.** Untested. May require audio replacement.
- **Subtitle suppression.** Requires active prompt engineering to reduce.
- **Voice consistency across 30+ clips.** Likely to drift without audio replacement.
- **Rapid action or fast cuts.** Not aligned with Sara's storytelling style — also not Veo's strength.
- **Perfect lip-sync.** Inconsistency is documented. Not reliable for every clip.
