# Experiment Workflow

## The Pipeline

Every production finding follows this exact path — no shortcuts:

```
Documentation → Experiment → Observation → Validation → Knowledge → Production Rule → Production Prompt
```

---

## Step 1 — Start with a Documented Hypothesis

Before designing any experiment, locate the item that justifies it:

- Veo behavior questions → `docs/veo/LIMITATIONS_AND_UNKNOWNS.md`
- Language Engine behavior → `docs/language_engine/`

Every experiment must trace back to a `[HYPOTHESIS]` or `[UNKNOWN]` entry.  
If the hypothesis is not documented, document it first. Then design the experiment.

---

## Step 2 — Design the Experiment

Copy `TEMPLATE.md` into this folder.

Name the file using this convention:

```
EXP-[NAMESPACE]-[NUMBER].md
```

Namespace assignments:
- **EXP-VEO** — Veo generation behavior (audio, video, character, prompts)
- **EXP-TTS** — Text-to-speech and voice generation
- **EXP-STORY** — Story structure and narrative testing
- **EXP-CAMERA** — Camera direction and cinematography
- **EXP-EDIT** — Post-production and assembly

Number sequentially within each namespace: `EXP-VEO-001`, `EXP-VEO-002`, etc.

Fill every field in the template before running. A half-designed experiment produces unusable observations.

One variable per experiment. If you are tempted to test two things at once, split it into two experiments.

---

## Step 3 — Run the Experiment

Execute prompts exactly as written. Do not adjust mid-experiment.

If a prompt needs changing, close the current experiment and open a new one with the revised prompt. Document why the change was made.

Record the exact parameters used: model ID, duration, resolution, reference images used (yes/no).

Download every clip immediately. Server retention is 48 hours.

---

## Step 4 — Record Observations

Fill in Results and Observations in the experiment file.

Write only what was observed. No interpretation. No inference. No "this suggests that."

Mark experiment status as `COMPLETE` or `INCOMPLETE`.

---

## Step 5 — Validate

A single experiment produces an **observation**, not knowledge.

Validation is an engineering decision based on the weight of evidence — not a fixed count of experiments.

Some findings may be validated by one decisive experiment with a clear, unambiguous result. Others may require several experiments across different conditions before the evidence is sufficient. The question to ask is: *Is the evidence strong enough to act on this in production?*

Factors that increase confidence:
- The observation appears consistently across repeated experiments
- The observation holds under varying conditions
- The observation is explicitly confirmed in official documentation
- No contradicting evidence exists

If an observation from one experiment is contradicted by a later experiment, both must be noted and the validation status updated. Contradictions are data — they prevent premature promotion to knowledge.

---

## Step 6 — Promote to Knowledge Log

When validation criteria are met, add an entry to `docs/veo/KNOWLEDGE_LOG.md`.

Each knowledge entry must:
- State only what was observed — no inference, no speculation
- Reference every experiment that supports it
- Carry a confidence level: `HIGH / MEDIUM / LOW`

Do not move a single-experiment observation into the knowledge log. It belongs in the experiment file only until validated.

---

## Step 7 — Promote to Production Rule

When knowledge is sufficient to change production behavior, update:

- `episodes/PRODUCTION_DECISIONS_LOG.md` — record the decision
- `docs/veo/SARA_PRODUCTION_GUIDE.md` — update Sara-specific guidance
- `prompts/` — update production prompt files

Each production rule update must reference the knowledge log entry that supports it (e.g., `KN-002`).

---

## Status Definitions

### Experiment Status

| Status | Meaning |
|--------|---------|
| `PLANNED` | Designed, not yet run |
| `IN_PROGRESS` | Currently running |
| `COMPLETE` | All clips generated, observations recorded |
| `INCOMPLETE` | Partially run — must be completed or formally closed |
| `REJECTED` | Experiment design was flawed; observations are not usable |

### Knowledge Status

| Status | Meaning |
|--------|---------|
| `OBSERVATION` | Seen in this experiment — not yet validated |
| `VALIDATED` | Sufficient experimental evidence to act on in production |
| `REJECTED` | Contradicted by a subsequent experiment |
| `PROMOTED` | Elevated to a production rule (see reference in knowledge log) |

---

## Hard Rules

**Never skip steps.** Observation is not knowledge. Knowledge is not a production rule.

**Never modify a prompt mid-experiment.** Close and open a new one.

**Never add knowledge without experimental evidence.** If it has not been tested, it belongs in `LIMITATIONS_AND_UNKNOWNS.md` as a `[HYPOTHESIS]`.

**Always download clips before 48 hours.** They cannot be recovered after deletion.
