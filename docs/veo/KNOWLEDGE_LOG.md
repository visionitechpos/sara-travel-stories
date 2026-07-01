# Veo Knowledge Log

## Purpose

This log contains validated production knowledge derived from real production experiments.

Every entry must reference the experiments that produced it. Nothing here is a hypothesis or engineering inference — only confirmed observations from actual Veo generations.

---

## How to Read This Log

### Status definitions

| Status | Meaning |
|--------|---------|
| `OBSERVATION` | Seen in one experiment — not yet validated |
| `VALIDATED` | Confirmed across 2+ experiments, or confirmed by official documentation |
| `REJECTED` | Contradicted by a subsequent experiment |
| `PROMOTED` | Elevated to a production rule — see reference |

### Confidence levels

| Level | Meaning |
|-------|---------|
| `HIGH` | Observed consistently, multiple experiments, no contradictions |
| `MEDIUM` | Observed in 2+ experiments with minor variation |
| `LOW` | Observed once, not yet repeated |

---

## Knowledge Entries

### KN-001 — Native Veo dialogue works reliably for Sara's voice

| Field | Value |
|-------|-------|
| **Status** | VALIDATED |
| **Confidence** | HIGH |
| **Source** | Real production — several vlogs already produced and successful (not a controlled EXP-VEO experiment) |
| **Date added** | 2026-07-02 |
| **Promoted to** | `docs/veo/SARA_PRODUCTION_GUIDE.md` — "Decision Resolved — Native Veo Dialogue" |

**Observation:** Sara's voice, defined natively within her Veo Character (see `SARA_VOICE_BIBLE.md` approved voice prompt), produces reliable, usable dialogue across multiple already-produced vlogs. No audio replacement pipeline is needed.

**Evidence summary:** Not derived from a designed EXP-VEO test — this is a case of production evidence directly resolving an open question (H-01) faster than the planned experiment would have. H-01 is marked REJECTED in `LIMITATIONS_AND_UNKNOWNS.md` as a result — not because the hypothesis was tested and failed, but because reality answered the question first.

---

### KN-002 — Visual and voice identity remain stable across separate Veo generations for Sara

| Field | Value |
|-------|-------|
| **Status** | VALIDATED |
| **Confidence** | HIGH |
| **Source** | Real production — multiple separately generated vlogs, per direct user confirmation ("الصوت والشكل مضبوطين") |
| **Date added** | 2026-07-02 |
| **Promoted to** | `docs/veo/LIMITATIONS_AND_UNKNOWNS.md` — resolves "Reference image identity stability" and "Voice consistency via reference images" |

---

### KN-003 — Sara's face identity persists without an attached reference image; wardrobe requires an attached reference

| Field | Value |
|-------|-------|
| **Status** | VALIDATED |
| **Confidence** | HIGH (confirmed across 2 shots: Shot 1 without wardrobe reference defaulted to base outfit; Shot 2 with Look 1 attached correctly changed the outfit) |
| **Source** | Live tests during ep001_fish-sculpture-obhur production |
| **Date added** | 2026-07-02 |
| **Promoted to** | Workflow practice for `episodes/ep001_fish-sculpture-obhur/PRODUCTION_BOARD.md` — face reference never needed; wardrobe reference required only when a non-default look is needed |

---

### KN-004 — A 10-second duration option exists but risks hallucinated dialogue if the script is too short

| Field | Value |
|-------|-------|
| **Status** | VALIDATED (existence of the option) / OBSERVATION (the hallucination risk — needs more tests) |
| **Confidence** | MEDIUM |
| **Source** | Live test during ep001_fish-sculpture-obhur production, Shot 3 — 10-second option selected, 4-word script |
| **Date added** | 2026-07-02 |
| **Promoted to** | `docs/veo/LIMITATIONS_AND_UNKNOWNS.md` — new Observed Limitation |

**Observation:** A 10-second generation option exists in the Veo interface and produced a clip successfully — this is longer than the 8-second cap in official documentation. However, the scripted dialogue (~2 seconds of natural speech) did not fill the 10-second duration, and Veo appears to have improvised additional unscripted dialogue with incorrect pronunciation to fill the remaining time.

**Evidence summary:** Single test. The 10-second option's existence is confirmed directly. The hallucination-when-underfilled pattern is a first observation — needs repetition with a dialogue line deliberately sized to fill 10 seconds before treating the "10s needs longer scripts" conclusion as fully validated.

**Observation:** When a shot was generated with only the location/sculpture reference image attached (no Sara reference image), Sara's face and identity were preserved correctly — confirming her identity is carried natively by the Veo Character, not dependent on an attached reference image per generation. However, she appeared in her default outfit (green top) rather than the approved "Look 1 — Coastal Light" wardrobe for this episode — wardrobe is not part of the auto-preserved identity and must be explicitly specified or attached when it differs from the default.

**Evidence summary:** One direct production test, not a designed multi-shot experiment. Confidence is MEDIUM rather than HIGH pending confirmation across more shots. Practical implication: attaching Sara's face reference image is unnecessary and frees a slot in the 3-image Ingredients to Video limit for location, sculpture, or wardrobe references instead.

**Observation:** Sara's face, appearance, and voice have remained consistent across multiple separately produced vlogs — not just within a single generation session. This was previously an open unknown (and, for voice, an observed limitation reported in outside research) for Veo projects generally.

**Evidence summary:** Confirmed directly by the user reviewing their own production history, not a designed EXP-VEO test. The user's own framing is the key insight: since identity and voice consistency are not the bottleneck, **script quality is the primary lever for output quality** — directly reinforcing the existing principle in `docs/NORTH_STAR.md`: "Input quality drives output quality."

---

## Entry Format

When adding a new knowledge entry:

```
### KN-[NUMBER] — [Short title]

| Field | Value |
|-------|-------|
| **Status** | OBSERVATION / VALIDATED / REJECTED / PROMOTED |
| **Confidence** | HIGH / MEDIUM / LOW |
| **Source experiments** | EXP-A01, EXP-A02 |
| **Date added** | YYYY-MM-DD |
| **Promoted to** | [production rule reference, or —] |

**Observation:**
[Exactly what was observed. Written in plain, specific language.
No inference. No interpretation. No "this suggests." Just what happened.]

**Evidence summary:**
[Brief note on what each source experiment contributed to this finding.]
```

---

## Promotion Checklist

Before adding an entry, confirm:

- [ ] The observation appears in 2+ separate experiments, OR is confirmed in official documentation
- [ ] The entry contains only observed facts — no inference or speculation
- [ ] All source experiments are referenced by ID
- [ ] The confidence level is justified by the evidence
- [ ] If status is PROMOTED: the production rule reference is included
