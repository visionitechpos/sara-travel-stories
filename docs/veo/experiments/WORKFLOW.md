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
EXP-[SERIES][NUMBER].md
```

Series assignments:
- **A** — Native audio and speech
- **B** — Character and visual consistency
- **C** — Subtitle and text behavior
- **D** — Dialect and language accuracy
- **E** — Prompt structure and optimization

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

An observation becomes **validated** when:

- It appears consistently in 2 or more separate experiments, OR
- It is explicitly confirmed in official documentation

If an observation from one experiment is contradicted by a later experiment, both entries must be noted and the validation status updated.

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
| `OBSERVATION` | Seen in this experiment only — not yet validated |
| `VALIDATED` | Confirmed across 2+ experiments or official documentation |
| `REJECTED` | Contradicted by a subsequent experiment |
| `PROMOTED` | Elevated to a production rule (see reference in knowledge log) |

---

## Hard Rules

**Never skip steps.** Observation is not knowledge. Knowledge is not a production rule.

**Never modify a prompt mid-experiment.** Close and open a new one.

**Never add knowledge without experimental evidence.** If it has not been tested, it belongs in `LIMITATIONS_AND_UNKNOWNS.md` as a `[HYPOTHESIS]`.

**Always download clips before 48 hours.** They cannot be recovered after deletion.
