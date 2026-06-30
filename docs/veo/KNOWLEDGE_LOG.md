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

*Empty — awaiting first experiment results.*

*First entry will be added after Sprint 1 experiments are run and observations are recorded.*

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
