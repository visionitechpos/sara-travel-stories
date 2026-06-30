# EXP-[NAMESPACE]-[NUMBER] — [Short Title]

## Metadata

| Field | Value |
|-------|-------|
| **Experiment ID** | EXP-[NAMESPACE]-[NUMBER] |
| **Namespace** | [VEO / TTS / STORY / CAMERA / EDIT] |
| **Status** | `PLANNED` |
| **Date run** | — |
| **Hypothesis source** | [Link or reference to the UNKNOWN or HYPOTHESIS this tests] |
| **Depends on** | [Prior experiment ID, or `None`] |

---

## Objective

[One sentence: what this experiment is designed to discover.]

---

## Question

[The single question this experiment answers. Phrased so the answer is measurable or clearly yes/no.]

---

## Variables

| Variable | Values tested |
|----------|--------------|
| [Variable name] | [Value A] vs [Value B] |

*One variable only. If testing two things, split into two experiments.*

---

## Constants

| Constant | Value |
|----------|-------|
| Model | `veo-3.1-generate-preview` |
| Duration | |
| Resolution | |
| Aspect ratio | `16:9` |
| Prompt rewriter | `OFF` |
| Reference images | [Yes / No] |
| [Any other fixed parameter] | |

---

## Prompts

### Clip A — [Label describing what this clip tests]

```
[Exact prompt text — copy this verbatim when running]
```

### Clip B — [Label]

```
[Exact prompt text]
```

*(Add or remove clips as needed. Each clip should differ from others by the variable only.)*

---

## Expected Observations

[What the current hypothesis predicts will happen — based on LIMITATIONS_AND_UNKNOWNS.md or prior experiments. Not what we want to see. Not what would be ideal. What the hypothesis actually predicts.]

---

## Observations to Record

After running, check each item and fill in what was actually observed:

- [ ] [Specific observable thing — e.g., "Did Arabic speech generate?"]
- [ ] [Specific observable thing — e.g., "Did subtitles appear?"]
- [ ] [Specific observable thing]
- [ ] [Specific observable thing]

---

## Results

> *Fill in after running. Do not edit the sections above this line.*

### Clip A — [Label]

**Generated?** [Yes / No / Partial]

**What was observed:**
[Plain description of what the clip actually shows and sounds like]

**Checklist:**
- [ ] [Item from Observations to Record] — [what was actually seen]
- [ ] ...

---

### Clip B — [Label]

**Generated?** [Yes / No / Partial]

**What was observed:**
[Plain description]

**Checklist:**
- [ ] [Item] — [what was seen]

---

## Conclusion

> *Fill in after reviewing all clips.*

**Success criteria met?** [Yes / No / Partial]

**Summary:**
[2–4 sentences. What was learned from this experiment. State only what was observed — no speculation about what it means for future experiments.]

---

## Knowledge Promoted?

| Knowledge item | Status |
|----------------|--------|
| [KN-XXX — description] | `OBSERVATION` |

*If no knowledge was promoted from this experiment, write "None — single experiment observation only."*

---

## Repository Impact

Which repository documents should be updated based on this experiment's findings?

| Document | Update required? |
|----------|-----------------|
| `docs/veo/KNOWLEDGE_LOG.md` | Yes / No |
| `docs/veo/SARA_PRODUCTION_GUIDE.md` | Yes / No |
| `docs/veo/LIMITATIONS_AND_UNKNOWNS.md` | Yes / No |
| `docs/SARA_VOICE_BIBLE.md` | Yes / No |
| `docs/SARA_LANGUAGE_BIBLE.md` | Yes / No |
| `prompts/` | Yes / No |
| `episodes/PRODUCTION_DECISIONS_LOG.md` | Yes / No |

*Fill in after Conclusion. Update documents only after knowledge is validated, not from a single observation.*

---

## Next Experiment

[EXP-ID and why, OR "None — path eliminated" OR "None — proceed to production"]
