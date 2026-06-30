# Audio and Dialogue

## How Veo Audio Works

`[OFFICIAL]`

Veo 3 and 3.1 generate audio natively alongside video. Audio is not added in post-production — it is generated as part of the same process.

Audio includes:
- Dialogue (synchronized to lip movement)
- Sound effects (SFX)
- Ambient environmental noise
- Music / score

`[OFFICIAL]`

Audio cannot be disabled via API. The `generate_audio` parameter is not supported. Audio generation is built into the model as a multi-modal feature with no off switch.

---

## Audio Hallucination

`[OFFICIAL]`

If the audio environment is not defined in the prompt, Veo will hallucinate audio — inventing background sounds, studio laughter, generic music, or ambient noise that was not requested.

`[INFERENCE]`

This means every Veo prompt for Sara must explicitly define the audio environment. Silence must be specified, not assumed. Even in a quiet scene, state: "ambient: quiet street ambience, gentle distant sounds of the city waking."

---

## How to Specify Audio in Prompts

`[OFFICIAL]`

Use separate labelled sentences for each audio type:

**Dialogue:**
```
Sara says, "وصلت الكورنيش الساعة ستة الصبح."
```
Quotation marks trigger synchronized dialogue generation and lip movement.

**Sound Effects:**
```
SFX: Gentle waves against the waterfront walkway.
```

**Ambient:**
```
Ambient: Quiet early morning, distant sound of the city waking, light breeze.
```

**Music / Score:**
```
Score: Soft, sparse ambient melody, low volume, warm tones.
```

---

## Dialogue and Lip Sync

`[OFFICIAL]`

Dialogue is triggered by quotation marks with a speaking lead-in verb:

```
A character says, "Exact words here."
```

Veo attempts to synchronize mouth movement to the words inside the quotation marks.

`[OFFICIAL]`

Dialogue generation for shorter speech segments is an active development area. Incoherent speech instances occur occasionally. Audio synchronization is being refined.

---

## Dialogue Best Practices

`[OFFICIAL + INFERENCE]`

**Keep dialogue to one sentence per clip.**
The model struggles with more than approximately 8 seconds of continuous speech. One sentence at a moderate pace fits within a 6–8 second clip reliably.

**Frame shots to show the mouth clearly.**
Medium shot or close-up showing the lower face improves lip-sync detection. Wide shots where the face is small produce worse synchronization.

**Specify pacing explicitly.**
Add instructions like "speaks calmly, moderate pace" or "brief pause before starting." The model uses these cues to calibrate rhythm.

**Eliminate competing audio during dialogue clips.**
Do not add music or complex ambient sounds when dialogue must be synchronized. Competing audio masks vocal articulation cues and degrades sync quality.

**Enunciation instructions:**
Adding "clearly enunciates" and "natural mouth openings visible" to the prompt measurably improves articulation.

**Clean audio specification:**
```
Audio: Clean dialogue only. No background music. Minimal room tone.
```

---

## Dialogue Prompt Template

`[OFFICIAL — adapted]`

```
[Camera]: Medium close-up of Sara, face clearly visible.
[Setting]: [Location description], [time of day], [lighting].
[Action]: Sara pauses, turns toward camera, speaks one sentence.
[Dialogue]: Sara says, "[exact line in Hejazi Arabic]"
[Pacing]: Speaks at natural pace, approximately [X] seconds. Small pause before beginning.
[Audio]: Clean dialogue only. No background music. [ambient sound description].
```

---

## Arabic Language and Dialogue

`[OFFICIAL]`

Veo 3.1 supports dialogue in multiple languages. To generate dialogue in a language other than English, write the dialogue inside quotation marks in the target language.

Example cited in official guidance: French dialogue written directly in the prompt was generated with correct lip-sync and accent.

`[INFERENCE]`

Arabic dialogue follows the same mechanism — write the exact Arabic text inside the quotation marks. The model will attempt lip-sync and audio generation.

`[HYPOTHESIS — requires experimentation]`

Several open questions specific to Arabic:

1. **Hejazi dialect accuracy.** Will Veo generate standard MSA pronunciation or Hejazi pronunciation when Arabic dialogue is provided? The Language Engine pre-processes dialogue into Hejazi — but Veo's output voice quality and dialect accuracy are unknown.

2. **RTL and Arabic character rendering.** When Arabic text is written in the prompt in quotation marks, does Veo correctly handle right-to-left text in its internal processing? Or does it transliterate?

3. **Accent and voice quality in Arabic.** The model is known to perform best on English. Arabic voice quality and naturalness are unknown without direct testing.

4. **Subtitle generation in Arabic.** The subtitles problem (see below) affects all dialogue. Will Arabic subtitles appear? Will they be right-to-left? Will they be garbled?

These hypotheses require experimentation as the first production priority.

---

## The Subtitles Problem

`[OFFICIAL]`

Veo 3 frequently generates garbled, nonsensical subtitles in the lower portion of the frame when dialogue is present. This is a known and documented issue.

**Root cause:** The model was trained on subtitle-bearing video (YouTube, TikTok, vlogs). It learned that dialogue and subtitles often appear together.

**Why it matters for Sara:** Subtitles that appear in the wrong language, with errors, or with inconsistent formatting break the frame and undermine authenticity.

**The subtitles are baked into the video.** Since Veo generates a single-layer video file, there is no subtitle toggle or layer to remove.

### Workarounds (in order of reliability)

`[OFFICIAL + INFERENCE]`

**1. Explicitly state "no subtitles" multiple times.**
"No subtitles. No captions. No text overlays. No burned-in text."
This is not reliable on its own but reduces frequency when combined with other techniques.

**2. Avoid quotation marks when possible.**
Quotation marks trigger dialogue generation, which triggers subtitle generation. If dialogue is not needed in a specific clip, do not use quotation marks.

**3. Fill the prompt with dense scene description.**
The "top to bottom" technique: when the prompt is extremely detailed about every visual element, the model has less room to improvise and subtitle generation decreases.

**4. Crop the bottom 10–15% of the frame.**
Subtitles appear in the lower portion of the frame. Generating at 1080p and cropping in post removes them. This requires accounting for crop in shot composition.

**5. Generate without dialogue, replace audio in post.**
Generate the clip as a visual-only or ambient-audio clip, then add processed audio in post-production. This eliminates subtitle generation entirely at the cost of native lip-sync.

---

## Audio Replacement Strategy

`[INFERENCE]`

For Sara production, the audio replacement strategy may be the most reliable path:

1. Generate Sara's clips with Veo using character reference images but **without dialogue in the prompt** (or with minimal ambient audio)
2. Process Sara's script through the Language Engine to produce optimized Hejazi audio
3. Generate that audio using an approved voice source
4. Align audio to Sara's lip movement in post-production

**The tradeoff:** No native lip-sync. Lip movement will not perfectly match the audio. This is the same tradeoff accepted by traditional animation and many language-dubbed productions.

**The benefit:** Full control over Sara's voice quality, dialect accuracy, and audio consistency across all episodes.

`[HYPOTHESIS]`

Whether the audio replacement approach or native Veo dialogue approach produces better results for Sara requires direct experimentation. Both approaches should be tested in Experiment 1.

---

## Video Extension and Audio

`[OFFICIAL]`

Video extension (extending an existing Veo clip by 7 seconds) maintains audio and visual consistency with the source clip.

When extending a clip that contains dialogue, the extended section continues in the same audio environment.

`[INFERENCE]`

Video extension is the primary mechanism for building clips longer than 8 seconds while maintaining consistency. A 30-second Sara story beat could be built by chaining: initial clip (8s) → extend (8s) → extend (8s) → extend (8s) = approximately 30 seconds with maintained character continuity.
