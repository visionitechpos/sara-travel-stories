# Transformation Provider

## What This Document Covers

Sprint 004 established that Sara Language Engine will not perform dialect transformation itself. Instead, it delegates transformation to an external Transformation Provider.

This document defines:
1. The Transformation Provider architecture
2. Mantooq analysis — reusable concepts and boundaries
3. Provider-agnostic integration design
4. Research recommendations

---

## Part 1 — Transformation Provider Architecture

### Responsibility

The Transformation Provider has exactly one job:

**Transform a script from its input register into Sara's natural Hejazi Arabic speaking style.**

It does not validate Sara's identity. It does not apply production rules. It does not know who Sara is. It receives a script and a transformation specification, and returns a transformed script.

Everything else is Sara Language Engine's responsibility.

---

### Input Contract

What the engine sends to the provider:

```
{
  script:        The draft script — in any Arabic register (MSA, mixed, informal)
  dialect_spec:  Sara's dialect profile — vocabulary, patterns, register
  rules:         Transformation constraints — what to preserve, what to change
  examples:      Reference input/output pairs demonstrating correct transformation
}
```

**script** — The raw draft. No pre-processing required. The provider handles any input register.

**dialect_spec** — Extracted from SARA_LANGUAGE_BIBLE.md. Core vocabulary, preferred expressions, prohibited constructions. This is what makes the transformation Sara-specific rather than generic Hejazi.

**rules** — Constraints the transformation must respect:
- Preserve factual content — do not add, remove, or alter facts
- Preserve sentence count — do not merge or split sentences
- Preserve narrative order — do not reorder content
- Do not add expressions not found in dialect_spec

**examples** — A small set of before/after pairs showing correct transformation. These anchor the provider to Sara's specific voice rather than generic Hejazi.

---

### Output Contract

What the engine receives back:

```
{
  transformed_script:  The script rewritten in Sara's Hejazi Arabic
  change_log:          List of what was changed and why
  flags:               Anything the provider was uncertain about
}
```

**transformed_script** — Ready for Sara Validation (Stage 3). Not yet validated — validation is the engine's job.

**change_log** — Every substitution documented. This feeds the Knowledge Layer over time. Each entry: original → replacement → reason.

**flags** — Sentences or words the provider was uncertain about. These are passed to validation for human review rather than silently guessed.

---

### What Sara Expects from a Provider

Sara's engine makes no assumptions about how the provider works internally. It only requires:

1. **The output is in Hejazi Arabic** — not MSA, not Najdi, not Gulf, not Egyptian
2. **Facts are preserved exactly** — no additions, deletions, or alterations
3. **The change log is complete** — every substitution is documented
4. **Uncertainty is flagged** — the provider does not hide what it does not know

A provider that silently guesses on uncertain words is not acceptable. A provider that flags uncertainty and lets the engine decide is.

---

## Part 2 — Mantooq Analysis

### Note on Access

Direct analysis of the Mantooq codebase was not possible in this sprint — the repository was not accessible. The analysis below is based on:
- Project context established in Sara documentation
- The known outcome: a proven dialect transformation approach using Google AI
- General knowledge of what effective Arabic dialect transformation requires

When Mantooq repository access is available, apply the framework below to extract specific values.

---

### What to Extract from Mantooq

**System prompt structure**
- How is the target dialect specified to the AI?
- Is it described in Arabic or English?
- What level of detail is used to describe Hejazi vs other dialects?

**Vocabulary handling**
- Is vocabulary provided as a table? A list? Inline examples?
- How many examples does the prompt include?
- Are prohibited words listed explicitly?

**Transformation instruction format**
- Is it a direct instruction ("rewrite this in...") or a role-based instruction ("you are a...")?
- Does it use few-shot examples? How many?
- What constraints are explicitly stated?

**Output format**
- Does Mantooq request structured output or free-form?
- Is a change log requested or implicit?
- How are uncertain substitutions handled?

**Workflow**
- Is transformation one call or multiple passes?
- Is there a review step built into the Mantooq workflow?
- What triggers a retry?

---

### What Is Reusable (inferred from context)

| Concept | Reusable in Sara | Notes |
|---------|-----------------|-------|
| Google AI as transformation engine | Yes | Already in Sara's architecture |
| Dialect specification format | Yes | Adapt to Sara's specific profile |
| Few-shot example approach | Yes | Replace with Sara-specific examples |
| Transformation instruction structure | Yes | With Sara-specific constraints added |
| Single-pass transformation call | Likely yes | Simple is better for V1 |

---

### What Must Stay Inside Mantooq

| Item | Reason |
|------|--------|
| Mantooq's character profile | Different character, different rules |
| Mantooq's vocabulary list | Different dialect target or style |
| Mantooq's specific prompt text | Copyrighted and character-specific |
| Any Mantooq production data | Not transferable |

Sara extracts the **strategy**, not the **content**. The strategy is: how to structure a transformation request to Google AI to produce reliable dialect output. The content — vocabulary, rules, examples — is Sara's own.

---

## Part 3 — Provider-Agnostic Integration

### Design Principle

Sara Language Engine calls the Transformation Provider through a defined interface. The engine does not know or care whether the provider is Google AI, a future model, or a manual human translator. It sends the input contract and expects the output contract.

This is the only coupling between the engine and the provider.

---

### Integration Interface

```
TransformationProvider.transform(request) → response

request: {
  script,
  dialect_spec,
  rules,
  examples
}

response: {
  transformed_script,
  change_log,
  flags
}
```

The engine calls `transform()`. The provider implements `transform()`. Neither knows how the other works internally.

---

### Provider Registry

Sara maintains a simple provider configuration:

```
active_provider: google_ai_v1
fallback:        manual_review
```

**active_provider** — The current implementation. For V1: Google AI with Sara's transformation prompt.

**fallback** — When the active provider fails, flags too many uncertainties, or is unavailable: route to manual review rather than failing silently.

**Switching providers:** Change `active_provider`. The engine contract does not change. Sara's validation, rules, and knowledge are unaffected.

---

### Stage 2 in MWLE — Updated

The Stage 2 block in MWLE_PIPELINE.md was described as "Google AI Dialect Transformation." With the provider abstraction in place, it is now more precisely:

**Stage 2 — Transformation Provider Call**

- Assemble the request: script + dialect_spec from SARA_LANGUAGE_BIBLE.md + rules + examples
- Call the active provider
- Receive transformed_script + change_log + flags
- Pass flags to Stage 3 for prioritized review
- If provider fails or returns more than 3 uncertainty flags: route to fallback

No other change to MWLE_PIPELINE.md is required.

---

### Dialect Spec Package

The dialect_spec sent to the provider is assembled from SARA_LANGUAGE_BIBLE.md at each call. It is not hardcoded. If the bible is updated, the next transformation call automatically uses the updated spec.

**Contents of dialect_spec (V1):**
- Core vocabulary table (17 entries from SARA_LANGUAGE_BIBLE.md)
- Dialect usage note (إيش vs وش)
- Verified from Testing expressions (5 entries)
- Prohibited phrases (all categories)
- Three example transformations (input/output pairs)

**Size constraint:** Keep dialect_spec concise. A provider prompt that is too long degrades transformation quality. V1 target: under 600 tokens for dialect_spec.

---

## Part 4 — Research Recommendations

### Priority Order

These experiments should be run in order. Each one informs the next.

---

### Experiment 1 — Baseline Transformation Quality

**Question:** How well does Google AI transform MSA to Hejazi Arabic with Sara's dialect_spec alone — no examples?

**Method:**
- Run 3 short scripts through the provider with dialect_spec only
- No few-shot examples
- Measure: how many Stage 3 validation checks fail?

**What it tells us:** Whether the dialect_spec alone is sufficient, or whether examples are required.

**Expected outcome:** Some failures. The question is how many and which type.

---

### Experiment 2 — Few-Shot Example Impact

**Question:** Does adding 2–3 transformation examples to the request reduce Stage 3 failures?

**Method:**
- Take the same 3 scripts from Experiment 1
- Add Sara-specific before/after examples to the request
- Measure: how does Stage 3 failure rate change?

**What it tells us:** The value of few-shot examples for this specific transformation task. If the improvement is significant, examples become a permanent part of the request. If not, they add cost without benefit.

---

### Experiment 3 — Mantooq Prompt Strategy Applied to Sara

**Requires:** Access to Mantooq's transformation prompt structure.

**Question:** Does applying Mantooq's prompt strategy (with Sara's content) outperform the naive approach?

**Method:**
- Extract Mantooq's prompt structure (format only, not content)
- Rebuild Stage 2 request using that structure with Sara's dialect_spec
- Run the same 3 scripts
- Compare Stage 3 failure rates across all three experiments

**What it tells us:** Whether Mantooq's proven approach transfers, and by how much.

---

### Experiment 4 — Change Log Usefulness

**Question:** Is the change_log output useful enough to justify the added complexity of requesting it?

**Method:**
- After Experiments 1–3, review the change logs produced
- Assess: are the logs accurate? Are they actionable for the Knowledge Layer?
- If the provider's change log is unreliable, consider generating it in Stage 3 instead

**What it tells us:** Whether change log generation belongs inside the provider or in the engine.

---

### Minimum Viable Research — If Time Is Limited

If only one experiment is possible before Sprint 005, run **Experiment 2**.

It answers the highest-leverage question: do examples help? If yes, include them in V1. If no, simplify the request. Either answer directly improves the pipeline.

---

## Summary

| Deliverable | Status |
|-------------|--------|
| Transformation Provider Architecture | Complete |
| Mantooq Analysis | Framework complete — direct analysis requires repo access |
| Provider-Agnostic Integration | Complete |
| Research Recommendations | Complete — 4 experiments in priority order |
