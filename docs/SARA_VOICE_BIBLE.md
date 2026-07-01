# Sara Voice Bible

## Status: LOCKED

Sara's voice is a core locked asset.

Do not replace the approved voice model.

Voice issues must be solved through better scripts, better wording, and better speech direction — never by switching voice models.

---

## Approved Voice Profile

### Current Status — Approved (2026-07-02)

Sara's voice is defined natively within her approved Veo Character Production — not a separate external TTS model, platform, or ID. The approved voice profile is the following prompt, used directly by Veo:

```
Native Saudi female voice from Jeddah. Natural local Jeddawi accent. 
Warm, friendly, and conversational. Sounds like a real woman from 
Jeddah speaking naturally with friends. Medium speaking pace, clear 
pronunciation, relaxed energy, approachable and authentic.

Slightly soft voice with gentle warmth and subtle expressiveness. Calm 
and confident, with natural emotional variation when sharing interesting 
stories or discoveries. Sounds intelligent, curious, and welcoming.

Avoid Modern Standard Arabic delivery, avoid news presenter style, avoid 
commercial voice-over style, avoid generic Gulf accent, avoid exaggerated 
acting, avoid influencer-style performance. Natural storytelling voice 
with realistic human speech patterns and authentic Jeddah character.
```

This matches — with no conflicts — every quality already defined below (Voice Character, Qualities to Preserve, Accent Preservation Rules) and the persona rules against presenter/influencer performance. Confirmed 2026-07-02, logged in `episodes/PRODUCTION_DECISIONS_LOG.md`.

**Still open:** the Voice Approval Criteria checklist below (phonemic accuracy, longevity test) has not yet been run against an actual Veo-generated audio sample — this prompt defines the intended voice, not a verified recording. Do this before treating pronunciation accuracy as confirmed — see Priority Experiments in `docs/veo/SARA_PRODUCTION_GUIDE.md`.

### Voice Approval Criteria

A voice is approved when it passes all of the following tests:

**Character match:**
- [ ] Sounds like a Saudi woman — not Gulf, not Egyptian, not neutral MSA
- [ ] Has natural warmth — not cold, not overly professional
- [ ] Does not sound like a virtual assistant or news reader
- [ ] The character feels personal, not performed

**Phonemic accuracy:**
- [ ] ع (ayn) — clearly and naturally rendered, not reduced to a plain vowel sound
- [ ] ح (heavy h) — distinct from هـ (light h), not merged
- [ ] ق (qaf) — soft or near-glottal, as in Hejazi speech, not heavy Najdi
- [ ] ج (jeem) — clean "j" sound, not "g" (Gulf) or hard "g" (Egyptian)
- [ ] Shaddah (ّ) — double consonants are audible and natural, not reduced to single

**Natural delivery test:**

Read this test sentence and evaluate:
```
وصلت البلد القديم الساعة ستة الصبح. ما كان فيه أحد. بس هذا اللي بغيته.
```

The voice passes if:
* Each sentence ends naturally with a slight fall in pitch
* "البلد القديم" sounds correct — not "Al-Bald" or "Al-Qadim"
* "بغيته" sounds Hejazi and natural, not formally read

**Longevity test:**
- [ ] Listen to 5 minutes of continuous output — the voice does not fatigue the ear
- [ ] Voice character is consistent from start to finish with no drift

---

## Voice Character

Sara's voice should feel like:
* A real person talking, not reading.
* A friend telling a story, not a narrator.
* Calm and warm, not excited or anchored.

### Qualities to Preserve

| Quality          | Description                                          |
|------------------|------------------------------------------------------|
| Warmth           | The voice feels close and personal                   |
| Clarity          | Words are easy to understand without effort          |
| Naturalness      | The pace and rhythm sound like real speech           |
| Calm confidence  | Not nervous, not overly enthusiastic                 |
| Hejazi softness  | The characteristic gentle flow of Jeddah Arabic      |

---

## Speech Direction

### Pace

* Moderate pace. Not rushed. Not overly slow.
* Allow natural pauses between sentences.
* Pause longer before important moments or reveals.
* Planning target: approximately 100–120 Arabic words per minute including natural pauses.
* Note: verify this rate against actual approved voice output before finalizing script length calculations.

### Rhythm

* Vary sentence length to create natural rhythm.
* Short sentence. Then a slightly longer one. Then short again.
* Avoid long unbroken stretches of identical sentence length.
* A sentence of three words can carry more weight than a sentence of fifteen.

### Tone per Context

| Context                  | Tone Direction                              |
|--------------------------|---------------------------------------------|
| Opening a new place      | Curious, slightly elevated energy           |
| Describing history       | Focused, calm, deliberate                   |
| Meeting locals / culture | Warm, engaged, genuine                      |
| Closing / reflection     | Thoughtful, grounded, personal              |
| Surprising discovery     | Natural wonder — not exaggerated            |

---

## Pronunciation Rules

### Critical Arabic Phonemes

These sounds are commonly mishandled by AI voice models in Arabic. Monitor each in every episode.

| Sound | Correct (Hejazi) | Common AI Error | Fix |
|-------|-----------------|-----------------|-----|
| ع (ayn) | Full, voiced, pharyngeal | Reduced to plain vowel | Flag for review; keep the word |
| ح (heavy h) | Breathy, distinct from هـ | Merged with هـ | Avoid pairing both sounds in the same short sentence |
| ق (qaf) | Soft / near-glottal in Hejazi | Heavy Najdi or formal "q" | If consistently wrong, rewrite to avoid the word |
| ج (jeem) | Clean "j" | "g" sound (Gulf) | Flag and keep; retrain with script marker if needed |
| شدة (shaddah) | Audible double consonant | Reduced to single | If merged, rewrite to avoid the word |
| ة (ta marbuta) | Silent at phrase-final in Hejazi | Pronounced "t" | Restructure sentence to remove ة from emphasis position |

### Place Name Pronunciation Guide

Write place names exactly as shown in all scripts. Do not vary the spelling between episodes.

| Place | Script Form | Notes |
|-------|------------|-------|
| Al-Balad (historic district) | البلد القديم | Full form on first use per episode |
| Jeddah | جدة | No tashkeel unless voice misreads |
| Rawasheen | الرواشين | Plural of روشن. Introduce with explanation on first use. |
| Red Sea | البحر الأحمر | Always full form |
| Corniche | الكورنيش | Accepted loanword — use as is |
| Al-Shallal | الشلال | |

### Numbers in Scripts

Never write numerals in scripts. Always write numbers as full Arabic words.

| Avoid | Use |
|-------|-----|
| ١٠٠٠ or 1000 | ألف |
| ١٩٢٦ or 1926 | ألف وتسعمية وستة وعشرين |
| ١٤ مليون | أربعة عشر مليون |
| ٦ صباحاً | الساعة ستة الصبح |
| الساعة ١٠ | الساعة عشرة |

For historical context, prefer relative time over specific years:
* Use: "من أكثر من ألف سنة"
* Avoid: "في عام تسعمية ميلادي"

---

## Tashkeel Guidance

Tashkeel (diacritical vowel marks) can improve AI voice pronunciation for ambiguous or unfamiliar words.

### When to Add Tashkeel

Add tashkeel only when:
* A word has two common pronunciations with different meanings and context does not resolve the ambiguity
* A proper noun or historical term is being mispronounced by the voice model
* A specific word has caused mispronunciation in a previous episode

### When Not to Add Tashkeel

Do not add tashkeel to:
* Common everyday words — the model handles these reliably
* Colloquial Hejazi words — tashkeel forces MSA pronunciation and breaks the accent
* Sentence-final positions — tanween (ً ٍ ٌ) triggers formal MSA delivery; avoid in all natural speech sentences
* Connectors and particles: بس، يعني، وبعدين، إيش — leave these unmarked always

### Tashkeel Examples

Appropriate:
```
الرَّواشين   — clarifies pronunciation of this specific architectural term
البَلَد القديم  — if the model reads البِلاد instead of البَلَد
```

Inappropriate:
```
بَس          — tashkeel causes formal MSA tone, use: بس
يَعْني        — same issue, use: يعني
صَراحةً       — tanween ending forces formal delivery, use: صراحة
```

---

## Accent Preservation Rules

Sara's accent is Hejazi Arabic — the dialect of Jeddah.

This accent is part of her identity and must be consistent across all content.

### Hejazi Characteristics to Preserve

| Feature | Description |
|---------|-------------|
| Gentle rhythm | Softer and more melodic than Najdi or Gulf Arabic |
| Jeem (ج) | Pronounced "j" — never "g" |
| Qaf (ق) | Soft or near-glottal — not the heavy Najdi "q" |
| Ta marbuta (ة) | Typically silent at the end of natural speech phrases |
| Connectors | بس، يعني، إيش، وبعدين — these carry Hejazi accent identity |
| Contractions | هالـ (this + noun), هذي (this, fem.) — Hejazi natural forms |

### What Breaks the Accent

If any of the following appear in voice output, the script needs revision before re-generation:

* Heavy formal MSA pronunciation throughout a sentence
* Gulf "g" sound for ج
* Egyptian "إيه" or "أيوه" style affirmatives in Sara's voice
* Tanween endings rendered formally in emotional key lines
* Over-precise letter-by-letter delivery as if reading classical text

### Quick Accent Test Words

Use these as a spot-check at the start of any new session with the voice model:

| Word | What to Hear | What to Reject |
|------|-------------|----------------|
| إيش | "esh" — quick, natural | Slow or formal delivery |
| بس | "bass" — light, brief | Heavy emphasis like فقط |
| يعني | natural, flowing | Slow, MSA-formal "ya'ni" |
| هالمكان | "hal-makan" — contracted | "hatha al-makan" — over-articulated |
| بغيته | natural Hejazi past | Formal "أردته" delivery |

---

## Common Voice Problems and Fixes

| Problem | Fix |
|---------|-----|
| Sounds like reading, not talking | Shorten sentences. Add connectors: يعني، بس، وبعدين. |
| Unnatural pauses | Rewrite to match natural speech rhythm. Check sentence endings. |
| Over-pronounced formal words | Replace formal word with Hejazi conversational equivalent. |
| Flat delivery on key moments | Add beat markers or pacing notes in the script. |
| Rushed ending | Add a closing reflection sentence with `[long pause]` before it. |
| Wrong ق accent | Replace the word if possible; accept and flag if not. |
| ة pronounced as "t" | Restructure sentence so ة is not in an emphasis or final position. |
| Tanween sounds formal | Rewrite to avoid tanween endings in all key script lines. |
| Shaddah reduced | Avoid the word; rewrite using a synonym or restructured phrase. |

---

## Script Markers for Voice

Use these markers in scripts to guide voice generation. Place inside square brackets immediately before the relevant word or sentence.

| Marker | Effect |
|--------|--------|
| `[pause]` | Brief natural pause |
| `[long pause]` | Longer pause for emotional weight or revelation |
| `[warm]` | Shift to warmer, closer tone |
| `[focus]` | Shift to deliberate, clear delivery |
| `[wonder]` | Natural curiosity — not exaggerated surprise |
| `[slow]` | Reduce pace for emphasis |
| `[question]` | Rising inflection for rhetorical questions |
| `[intimate]` | Very close, personal, quiet delivery |

Example:
```
وصلت هنا من غير توقع. [pause] ما كنت أعرف إن المكان راح يأثر فيّ بهالطريقة. [long pause] لكن هذا ما يصير أحياناً في السفر. [slow] الأماكن اللي ما خططت لها — هي اللي تفضل معك.
```

Use markers sparingly. One or two per paragraph is enough. Too many markers disrupt natural delivery.

---

## What to Avoid

* Do not change the voice model to fix a script problem — fix the script.
* Do not use voice effects or post-processing that changes the voice character.
* Do not allow the voice to sound artificial or robotic in any episode.
* Do not speed up or slow down the voice at the export/track level — fix pacing in the script.
* Do not add tashkeel to colloquial Hejazi words — it triggers MSA delivery.
* Do not end important lines with tanween — it forces formal pronunciation.
* Do not accept wrong ج pronunciation — flag and investigate before publishing.
