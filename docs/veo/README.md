# Veo Knowledge Base

## Purpose

This knowledge base documents what is known about Google's Veo video generation model from an engineering and production perspective.

Every finding is labeled:
- `[OFFICIAL]` — stated in official Google documentation
- `[INFERENCE]` — derived from official sources through engineering reasoning
- `[HYPOTHESIS]` — requires experimentation to confirm

This is a living document. Update it when production experiments produce new findings.

---

## The Veo Model Family

`[OFFICIAL]`

| Model | Status | Key Capability |
|-------|--------|---------------|
| Veo 2 | Legacy | Still used internally for object add/remove tools only |
| Veo 3.0 (`veo-3.0-generate-001`) | **Deprecated** | Replaced by Veo 3.1 family |
| Veo 3.1 | Active (Preview) | Improved consistency; 4K; reference images; better audio |
| Veo 3.1 Fast | Active (Preview) | Faster generation; same features as 3.1 including reference images |
| Veo 3.1 Lite | Active (Preview) | Limited to 720p; no 4K; no reference images |

**Model IDs (Gemini API):**
- `veo-3.1-generate-preview`
- `veo-3.1-fast-generate-preview`
- `veo-3.1-lite-generate-preview`

---

## What Veo Is

`[OFFICIAL]`

Veo is Google DeepMind's video generation model. It takes text prompts and/or reference images and generates short video clips with natively synchronized audio.

Veo does not generate long-form video. It generates clips of 4, 6, or 8 seconds. Long-form episodes are assembled from multiple clips.

---

## Generation Modes

`[OFFICIAL]`

| Mode | Description |
|------|-------------|
| Text-to-Video | Generate from text prompt only |
| Image-to-Video | Animate from a first reference frame |
| First + Last Frame | Generate the transition between two provided images |
| Ingredients to Video | Use up to 3 reference images for character/scene consistency |
| Video Extension | Extend a Veo-generated clip (3.1 and 3.1 Fast only) |
| Object Insertion | Add an object to existing video (uses Veo 2, no audio) |
| Object Removal | Remove an object from existing video (uses Veo 2, no audio) |

---

## Output Specifications

`[OFFICIAL]`

| Parameter | Options |
|-----------|---------|
| Resolution | 720p, 1080p (8s only), 4K (8s only, not Lite) |
| Duration | 4, 6, or 8 seconds |
| Aspect Ratio | 16:9 (landscape) or 9:16 (portrait) |
| Frame Rate | 24 fps |
| Output per request | 1 video |
| Server retention | 2 days — download required |
| Generation latency | 11 seconds minimum; up to 6 minutes at peak |

---

## Integration Points

`[OFFICIAL]`

- Gemini API (developer access)
- Vertex AI / Gemini Enterprise Agent Platform (enterprise)
- Google AI Studio (experimentation)
- Google Flow (filmmaking tool)
- SynthID watermark applied to all outputs

---

## What Veo Is Not

`[INFERENCE]`

Veo is not a long-form video generator. It is a clip generator.

A Sara episode is not one Veo generation. It is an assembly of multiple clips, each 4–8 seconds, edited together in post-production.

This is not a limitation unique to Sara — it is the production model for any serious use of Veo.

---

## Document Map

| Document | Contents |
|----------|---------|
| `PROMPT_ENGINEERING.md` | Prompt structure, camera language, what works, what fails |
| `CHARACTER_CONSISTENCY.md` | Ingredients to Video, reference images, consistency techniques |
| `AUDIO_AND_DIALOGUE.md` | Audio generation, dialogue, lip sync, language support, subtitles |
| `LIMITATIONS_AND_UNKNOWNS.md` | Known limitations, unknowns, hypotheses for experimentation |
| `SARA_PRODUCTION_GUIDE.md` | Sara-specific implications and production recommendations |
