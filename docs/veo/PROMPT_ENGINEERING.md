# Prompt Engineering

## The Core Formula

`[OFFICIAL]`

```
[Cinematography] + [Subject] + [Action] + [Context] + [Style & Ambiance]
```

Every effective Veo prompt contains these five elements. The order matters — put cinematography first to establish the frame before describing what is in it.

**Example (official):**
```
Medium shot, a tired corporate worker, rubbing his temples in exhaustion,
in front of a bulky 1980s computer in a cluttered office late at night.
The scene is lit by harsh fluorescent overhead lights and the green glow
of the monochrome monitor. Retro aesthetic, shot as if on 1980s color
film, slightly grainy.
```

---

## Cinematography Language

`[OFFICIAL]`

Cinematography terms are the most powerful tool in a Veo prompt. Use them first.

### Camera Movement

| Term | Effect |
|------|--------|
| Dolly shot | Camera physically moves toward or away from subject |
| Tracking shot | Camera follows subject movement |
| Crane shot | Camera moves vertically, often revealing scale |
| Aerial view | Bird's-eye perspective |
| Slow pan | Horizontal camera movement |
| POV shot | First-person perspective |
| Handheld | Subtle realistic camera shake |

### Composition

| Term | Effect |
|------|--------|
| Wide shot | Full body + environment |
| Medium shot | Waist up; best for dialogue |
| Close-up | Face and expression |
| Extreme close-up | Detail — eyes, hands, object |
| Low angle | Camera below subject, creates power/scale |
| Two-shot | Two people in frame together |

### Lens and Focus

| Term | Effect |
|------|--------|
| Shallow depth of field | Subject sharp, background blurred |
| Wide-angle lens | Expands sense of space |
| Soft focus | Dreamlike, memory quality |
| Deep focus | Everything in frame is sharp |

---

## What Works

`[OFFICIAL]`

**Extreme specificity.** "A woman in her twenties with wavy brown hair and light freckles" produces better results than "a woman." The more detail, the more control.

**Sensory language.** Describe what you see, hear, and feel — not just what is present. Atmosphere and mood carry as much weight as physical description.

**Timestamp prompting for multi-beat clips.** `[00:00-00:02]`, `[00:02-00:04]`, etc. This directs timing and pacing within a single 4–8 second generation.

Example:
```
[00:00-00:02] Medium shot from behind a young woman walking along a waterfront
at dawn, city still dark behind her.
[00:02-00:04] Reverse shot of her face, expression curious, something ahead
catching her attention. SFX: Gentle waves.
[00:04-00:06] Cut to what she is looking at — a large sculpture on the
waterfront she has passed before but never examined.
[00:06-00:08] Slow zoom toward the sculpture. Ambient: early morning silence.
```

**Camera + subject + action — all three.**
A prompt with camera direction and no action produces static shots. Action without camera direction produces generic framing. All three together produce intentional cinema.

**Explicit audio cues.**
State audio as separate elements: dialogue, SFX (sound effects), and ambient noise each on their own line. Audio that is implied rather than stated tends to be hallucinated.

---

## What Fails

`[OFFICIAL + INFERENCE]`

**Negative instructions.** Do not write "no man-made structures" or "don't include music." Write what you want instead: "a desolate landscape with no buildings or roads" or "ambient natural silence only."

**Vague character description.** "A woman" produces a generic figure. "A Saudi woman in her late twenties, dark hair, warm complexion, wearing a dark abaya, standing at the edge of a waterfront at dawn" produces a specific person.

**Long monologues in a single clip.** Any dialogue over approximately 8 seconds in a single clip will cut off or lose synchronization. Keep dialogue to one sentence per clip.

**Multi-speaker single clips.** One speaker per clip. Multi-person conversations must be split into separate clips chained in post.

**Complex action in a short clip.** For fast-paced or multi-step action, map out "exact play-by-plays" in timestamp format. Vague action descriptions produce unclear movement.

**Competing audio layers.** Background music + dialogue in the same clip degrades lip-sync accuracy by masking vocal articulation cues. Specify each audio layer clearly or avoid mixing.

---

## Prompt Length

`[OFFICIAL]`

Both long and short prompts can work. The recommendation is to experiment.

`[INFERENCE]`

Short prompts work when the subject and scene are simple. Long prompts work better when character specificity, atmosphere, and audio all need to be controlled simultaneously.

For Sara — a specific character in specific locations delivering specific dialogue — longer prompts with detailed character descriptions will generally produce better consistency.

---

## Prompt Rewriter

`[OFFICIAL]`

Veo includes a built-in prompt rewriter that modifies prompts before generation. It is enabled by default and can be disabled.

`[INFERENCE]`

The prompt rewriter may alter character descriptions, dialogue, or style cues in ways that affect consistency across clips. For production use with a specific character (Sara), disabling the prompt rewriter gives more direct control.

**Recommendation:** Disable the prompt rewriter and take full ownership of prompt construction. This is more work upfront and produces more predictable results across episodes.

---

## Negative Prompting

`[OFFICIAL]`

Describe exclusions as positive descriptions of the absence:

| Do not write | Write instead |
|-------------|--------------|
| no subtitles | clean video, no text overlays, no captions |
| no background music | ambient natural sound only |
| no man-made structures | open natural landscape |

---

## Using Gemini to Expand Prompts

`[OFFICIAL]`

Google recommends using Gemini to analyze a simple prompt and expand it with more cinematic detail before sending to Veo.

`[INFERENCE]`

For Sara, this step should happen after the Language Engine has processed the script — Gemini can expand the scene description while the Language Engine controls the script content. This keeps the two workflows clean and separate.
