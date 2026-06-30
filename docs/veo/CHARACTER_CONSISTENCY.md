# Character Consistency

## The Problem

`[INFERENCE]`

Veo generates each clip independently. Without an explicit mechanism to enforce character appearance, Sara's face, skin tone, hair, build, and clothing will drift between clips. Episodes assembled from inconsistent clips will fail the character test in Sara's production rules.

Character consistency is not automatic. It requires deliberate engineering on every clip.

---

## Primary Mechanism — Ingredients to Video

`[OFFICIAL]`

Ingredients to Video is Veo 3.1's reference image feature. It allows up to 3 reference images per generation to anchor character appearance, scene setting, and object consistency.

**What it maintains:**
- Character facial appearance and identity
- Character's consistent look across changing scenes
- Object and background consistency when the same references are used

**What it enables:**
- The same character appearing across multiple separately generated clips
- A full narrative where characters look the same even as settings change

---

## Reference Image Specifications

`[OFFICIAL]`

- Maximum: 3 reference images per request
- When reference images are used: duration must be 8 seconds (not 4 or 6)
- Available in Veo 3.1 only (not Veo 3.1 Lite)
- Audio generation is included with Ingredients to Video

`[INFERENCE]`

The 3-image limit is per generation request. The same 3 images should be used consistently across all Sara clip generations to maintain identity.

Best reference image configuration for a character:
- Image 1: Frontal face, neutral expression, good lighting
- Image 2: Three-quarter view (shows depth and profile)
- Image 3: Full body or contextual shot in production environment

---

## Generating Reference Images

`[OFFICIAL]`

Google's recommended workflow for Ingredients to Video:

**Step 1:** Generate character reference images using Gemini 2.5 Flash Image with a detailed character description prompt.

**Step 2:** Use those generated images as the reference images in subsequent Veo Ingredients to Video requests.

`[INFERENCE]`

For Sara: reference images must be generated once, reviewed and approved against Sara's locked character assets (from SARA_CHARACTER_BIBLE.md), and then used consistently across all production.

Reference images, once approved, become production assets. They live in `/assets/sara/` and are never regenerated without an explicit character update decision.

---

## Prompt-Level Consistency

`[OFFICIAL]`

Beyond reference images, character description must be repeated verbatim across every clip prompt. Consistency in description reinforces consistency in output.

**Recommended approach:**
Define a standard character descriptor block used in every Sara prompt:

```
[Sara descriptor block — to be defined after reference image approval]
```

This block is copied into every clip prompt, every time, without variation.

---

## Scene and Setting Consistency

`[OFFICIAL]`

Ingredients to Video also maintains scene consistency across multiple clips when the same background/setting reference image is included.

**Practical use for Sara:**

For an episode that takes place in Al-Balad, a single establishing reference image of the specific alley or location can be included across all clips in that scene, keeping the environment consistent between cuts.

---

## Multi-Shot Dialogue Workflow

`[OFFICIAL]`

The recommended workflow for consistent multi-shot dialogue scenes:

**Step 1:** Generate reference images for Sara and the setting.

**Step 2:** Generate first clip with reference images:
```
Using the provided images of Sara and [location], medium shot of Sara 
standing at [specific spot]. She looks at [direction] and says 
"[first line]."
```

**Step 3:** Generate follow-up clips using the same reference images:
```
Using the provided images of Sara and [location], close-up of Sara.
She says "[second line]."
```

Each clip uses identical reference images and repeats Sara's character descriptor.

---

## Known Consistency Issues

`[OFFICIAL]`

Creating videos with consistent character appearance across multiple separately generated clips is possible but requires deliberate use of reference images.

`[INFERENCE]`

Without reference images, character appearance drifts between clips — same hair color but different styling, same face type but different bone structure, etc. For Sara, where character is the core asset, drifting appearance is a production-breaking failure.

`[HYPOTHESIS]`

Even with reference images, subtle drift may occur in:
- Skin tone under different lighting conditions
- Hair styling details
- Abaya texture and drape

This requires production testing to establish acceptable drift thresholds.

---

## Voice Consistency

`[HYPOTHESIS]`

It is unknown whether Veo maintains the same voice across multiple clips when using the same reference images. The documentation confirms visual consistency via reference images but does not specifically address voice consistency.

Experiment required: Generate 3 consecutive clips with the same reference images and the same character dialogue instruction. Evaluate whether the voice sounds like the same person across all three clips.

If voice consistency is unreliable, the production strategy shifts to:
- Generate video with dialogue via Language Engine
- Replace Veo's native audio with a consistent external voice source
- Align in post-production
