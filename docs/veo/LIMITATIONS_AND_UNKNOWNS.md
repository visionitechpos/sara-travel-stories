# Limitations and Unknowns

## How to Read This Document

Every item is categorized:
- `[CONFIRMED LIMITATION]` — documented by Google as a known limitation
- `[OBSERVED LIMITATION]` — observed in practice and reported by users, not officially documented
- `[UNKNOWN]` — not addressed in documentation; requires experimentation
- `[HYPOTHESIS]` — engineering inference that needs testing to confirm or deny

---

## Confirmed Limitations

### Clip duration is 4, 6, or 8 seconds

`[CONFIRMED LIMITATION]`

Veo generates individual clips, not long-form video. Maximum per generation is 8 seconds. Long-form content requires assembling multiple clips.

**Impact on Sara:** A 3-minute episode requires approximately 22–45 clips depending on duration mix. Post-production assembly is a core part of the workflow, not an afterthought.

---

### Generated videos are deleted after 2 days

`[CONFIRMED LIMITATION]`

Veo stores generated videos on Google's servers for 2 days only. After 48 hours, the video is deleted and cannot be recovered.

**Impact on Sara:** Every accepted clip must be downloaded immediately after generation. Do not rely on server storage. The production workflow must include a download step before any clip is considered secured.

---

### Generation time varies from 11 seconds to 6 minutes

`[CONFIRMED LIMITATION]`

Minimum generation time per clip is approximately 11 seconds. During peak usage hours, generation can take up to 6 minutes per clip.

**Impact on Sara:** Episode production time cannot be calculated as a fixed formula. A 30-clip episode could take 6 minutes (off-peak) to 3 hours (peak). Production sessions should be planned with buffer time.

---

### Audio cannot be disabled

`[CONFIRMED LIMITATION]`

The `generate_audio` parameter is not supported in the API. Audio is always generated. There is no silent video mode.

**Impact on Sara:** If the chosen production strategy requires silent video (visual-only, audio replaced in post), this requires workarounds: avoid dialogue triggers (quotation marks), specify "no audio elements" in the prompt, and accept that some residual audio may still be generated.

---

### Short speech segments are inconsistent

`[CONFIRMED LIMITATION]`

From official Google documentation: "Creating videos with natural and consistent spoken audio, particularly for shorter speech segments, remains an active development area. Continuous work to refine audio synchronization and eliminate instances of incoherent speech."

**Impact on Sara:** Any clip with Sara speaking may produce occasional incoherent audio. Every clip with dialogue requires manual review before assembly.

---

### Reference images require 8-second duration

`[CONFIRMED LIMITATION]`

When using Ingredients to Video with reference images, the generation must be 8 seconds. 4-second and 6-second durations are not supported with reference images.

**Impact on Sara:** All character-consistent clips will be 8 seconds minimum. Episode pacing and editing must account for this.

---

### Object add/remove uses Veo 2 and has no audio

`[CONFIRMED LIMITATION]`

The object insertion and object removal features use Veo 2 (not 3.1) and do not generate audio.

**Impact on Sara:** These features are available but require separate audio handling.

---

### Video extension restricted to 720p

`[CONFIRMED LIMITATION]`

Video extension is limited to 720p resolution, even when the source clip was generated at 1080p or 4K.

**Impact on Sara:** If video extension is used to build longer scenes, the resolution of extended segments will be downgraded. All extended content will be 720p.

---

### Video extension input maximum 141 seconds

`[CONFIRMED LIMITATION]`

Input videos for extension cannot exceed 141 seconds. This is not a practical constraint for Sara's workflow since individual clips are under 8 seconds.

---

### Veo 3.1 Lite cannot do 4K or use reference images

`[CONFIRMED LIMITATION]`

Veo 3.1 Lite is limited to 720p and does not support Ingredients to Video (reference images). It is not suitable for Sara character-consistency production.

---

### SynthID watermark on all outputs

`[CONFIRMED LIMITATION]`

All Veo-generated videos carry an embedded SynthID watermark identifying them as AI-generated. This watermark is embedded in the video data, not visible as a visible overlay.

**Impact on Sara:** The watermark does not affect visual quality. It does mean that any AI-detection tool will identify Sara's content as AI-generated.

---

### Regional person generation restrictions

`[CONFIRMED LIMITATION]`

In EU, UK, CH, and MENA regions, the `personGeneration` parameter is restricted to `allow_adult` values only.

**Impact on Sara:** Sara is an adult character. This restriction does not block production but must be accounted for in API configuration.

---

## Observed Limitations

### Subtitle hallucination during dialogue

`[OBSERVED LIMITATION]`

Veo 3 frequently generates garbled, misspelled subtitles in the lower frame when dialogue is present. This is burned into the video and cannot be removed without cropping.

Documentation from MIT Technology Review confirms this as a documented issue. Google has not publicly provided a reliable fix.

**Impact on Sara:** Any clip with Arabic dialogue risks having incorrect or garbled subtitles appearing. This is one of the highest-risk production issues.

---

### Audio hallucination when environment is unspecified

`[OBSERVED LIMITATION]`

Veo invents audio — studio laughter, generic music, crowd sounds — when the audio environment is not specified. This is not documented as a limitation but is widely observed.

**Impact on Sara:** Every prompt must specify the audio environment explicitly. Silence is not the default.

---

### Voice inconsistency across separate generations

`[OBSERVED LIMITATION]`

Even with identical reference images and character descriptions, Sara's voice may sound different across separately generated clips. This has been observed in multi-clip production workflows.

**Impact on Sara:** Voice consistency is not guaranteed by reference images alone. The audio replacement strategy may be more reliable for long-term character voice consistency.

---

## Unknowns

### Arabic Hejazi dialect — voice quality

`[UNKNOWN]`

It is not documented whether Veo 3.1 generates natural Arabic speech when Arabic text is provided in dialogue. The model's primary training language is English. Arabic voice quality, naturalness, and dialect accuracy are unknown.

**Experiment required:** Generate 3–5 clips with Hejazi Arabic dialogue in quotation marks. Evaluate: Is the voice natural? Is it MSA or Hejazi? Is the pronunciation correct? Is it intelligible?

---

### Arabic dialogue — subtitle behavior

`[UNKNOWN]`

It is unknown whether the subtitle hallucination problem produces Arabic text, romanized Arabic, garbled English, or something else when Arabic dialogue is generated.

**Experiment required:** Generate a clip with Arabic dialogue and observe what subtitles (if any) appear. Test whether "no subtitles" instructions in Arabic reduce frequency.

---

### Reference image — identity stability over many generations

`[UNKNOWN]`

It is not documented how stable Sara's appearance will remain when using the same 3 reference images across 50+ separate clip generations for a full episode. Identity drift over many generations is undocumented.

**Experiment required:** Generate 10 consecutive clips with identical reference images and character descriptions. Measure visual consistency of Sara's face, skin tone, hair, and clothing across all clips.

---

### Voice consistency via reference images

`[UNKNOWN]`

Whether the same reference images produce the same voice across separate generations is undocumented. Reference images are described as controlling visual identity, not voice.

**Experiment required:** Generate 5 clips with identical reference images and different dialogue. Evaluate whether the voice sounds like the same person across all clips.

---

### Prompt rewriter effect on Arabic text

`[UNKNOWN]`

The built-in prompt rewriter modifies prompts before generation. Its behavior when Arabic text appears in the prompt — particularly in the dialogue quotation marks — is unknown. It may modify, transliterate, or ignore Arabic text.

**Experiment required:** Generate identical clips with prompt rewriter on and off when Arabic dialogue is present. Compare outputs.

---

### Maximum number of clips per episode assembly

`[UNKNOWN]`

There is no documented limit on how many Veo clips can be assembled in post-production. However, it is unknown whether visual consistency degrades when assembling 30+ separate clips even with consistent reference images.

---

## Hypotheses for Experimentation

### H-01 — Arabic audio replacement is more reliable than native generation

`[HYPOTHESIS]`

For Sara's use case: generating clips visually and replacing Veo's native audio with Language Engine-processed Hejazi audio in post-production will produce more consistent, higher-quality results than relying on Veo's native Arabic dialogue generation.

**Test:** Produce one short Sara script twice — once with Veo native dialogue, once with audio replacement. Compare: dialect quality, pronunciation accuracy, voice consistency, lip-sync quality.

---

### H-02 — Disabling prompt rewriter improves consistency

`[HYPOTHESIS]`

Disabling the prompt rewriter and writing complete, detailed prompts manually will produce more consistent character appearance across clips than relying on the rewriter to interpret simplified prompts.

**Test:** Generate 5 clips with rewriter enabled vs. 5 clips with rewriter disabled, using identical reference images and character descriptors. Compare consistency.

---

### H-03 — 3 reference images outperforms 1

`[HYPOTHESIS]`

Using all 3 allowed reference images (front, three-quarter, full-body) will produce greater character consistency than using 1 reference image.

**Test:** Generate 5 clips with 1 reference image vs. 5 clips with 3 reference images. Compare character consistency.

---

### H-04 — Audio replacement eliminates subtitle problem

`[HYPOTHESIS]`

If Sara's clips are generated without dialogue in the prompt (and audio is replaced in post), the subtitle hallucination problem will not occur.

**Test:** Generate 5 clips with dialogue prompts vs. 5 clips without dialogue prompts. Confirm whether subtitles appear only in the dialogue clips.

---

### H-05 — Timestamp prompting improves clip-to-clip narrative flow

`[HYPOTHESIS]`

Using timestamp prompting ([00:00-00:02], [00:02-00:04]) within a single 8-second generation will produce more narratively coherent clips than single-action prompts.

**Test:** Generate the same scene beat twice — once with timestamp structure, once without. Compare narrative coherence.
