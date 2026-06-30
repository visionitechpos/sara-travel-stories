# Test Run 001 — MWLE Pipeline End-to-End

**Date:** 2026-06-30
**Pipeline version:** MWLE V1 (MWLE_PIPELINE.md)
**Purpose:** Validate each stage with one small travel script before production use.

---

## Draft Script — Input

A short scene. Sara arrives at the Corniche early morning and notices something she has passed before without understanding.

```
وصلت إلى الكورنيش في الساعة السادسة صباحاً.
كان المكان هادئاً جداً.
لاحظت نصباً لم أكن أعرف ما هو.
تساءلت: ماذا يعني هذا الشيء؟ ولماذا وُضع هنا بالذات؟
قررت أن أبحث عن الإجابة.
```

---

## Stage 1 — Pre-Transform Check

**Input:** Draft script above.

**Checks:**

| Check | Result | Note |
|-------|--------|------|
| Narrative question exists | ✅ PASS | "ماذا يعني هذا الشيء؟ ولماذا وُضع هنا؟" |
| Story type identified | ⚠️ FLAG | Not documented. Likely Mystery or Hidden Detail. |
| Opening begins in a moment | ✅ PASS | Begins with arrival, specific time |
| No prohibited phrases | ✅ PASS | None detected |
| No unverified facts stated as certain | ✅ PASS | No factual claims made |

**Decision: PASS**

Flag carried forward: Story type must be documented before this script moves to full episode production. For this test run, the pipeline proceeds.

---

## Stage 2 — Dialect Transformation

**Input:**
```
وصلت إلى الكورنيش في الساعة السادسة صباحاً.
كان المكان هادئاً جداً.
لاحظت نصباً لم أكن أعرف ما هو.
تساءلت: ماذا يعني هذا الشيء؟ ولماذا وُضع هنا بالذات؟
قررت أن أبحث عن الإجابة.
```

**Output:**
```
وصلت الكورنيش الساعة ستة الصبح.
المكان كان هادي مرة.
شفت نصب ما كنت أعرف إيش هو.
قلت في نفسي: إيش يعني هالشيء؟ وليش حطوه هنا بالذات؟
بدأت أدور على الجواب.
```

**What changed:**

| Before | After | Reason |
|--------|-------|--------|
| وصلت إلى الكورنيش | وصلت الكورنيش | Hejazi drops preposition in arrival constructions |
| في الساعة السادسة صباحاً | الساعة ستة الصبح | Hejazi time expression — الصبح not صباحاً |
| كان المكان هادئاً جداً | المكان كان هادي مرة | Hejazi word order + مرة as intensifier instead of جداً |
| لاحظت | شفت | Sara's vocabulary — شفت not لاحظت |
| لم أكن أعرف ما هو | ما كنت أعرف إيش هو | Hejazi negation + إيش instead of ما |
| تساءلت | قلت في نفسي | More conversational — تساءلت is literary (per SARA_LANGUAGE_BIBLE.md) |
| ماذا | إيش | Sara's core vocabulary |
| هذا الشيء | هالشيء | Hejazi contraction |
| ولماذا وُضع هنا | وليش حطوه هنا | Hejazi — ليش + active voice |
| قررت أن أبحث | بدأت أدور | More natural Hejazi — أدور means to look/search |
| الإجابة | الجواب | Hejazi preferred form |

---

## Stage 3 — Sara Validation

**Input:**
```
وصلت الكورنيش الساعة ستة الصبح.
المكان كان هادي مرة.
شفت نصب ما كنت أعرف إيش هو.
قلت في نفسي: إيش يعني هالشيء؟ وليش حطوه هنا بالذات؟
بدأت أدور على الجواب.
```

**Validation checks:**

| Check | Result | Note |
|-------|--------|------|
| No prohibited phrases | ✅ PASS | None present |
| No dialect-breaking words | ✅ PASS | None detected |
| No MSA constructions | ✅ PASS | All constructions are conversational |
| No presenter-style opening | ✅ PASS | Begins with action, not introduction |
| No channel mechanics | ✅ PASS | None present |
| Core Sara vocabulary present | ✅ PASS | إيش، ما كنت أعرف، هالشيء |
| Numbers written as words | ✅ PASS | ستة ✓ |
| No tashkeel on colloquial words | ✅ PASS | No tashkeel present |

**Output:** Script passes unchanged.

**Decision: PASS**

**Observation to log:** "بدأت أدور على الجواب" — أدور used as "to search for." Natural in Hejazi but not yet in Sara's verified vocabulary list. Worth confirming through production testing before promoting to Standard.

---

## Stage 4 — Voice Optimization

**Input:**
```
وصلت الكورنيش الساعة ستة الصبح.
المكان كان هادي مرة.
شفت نصب ما كنت أعرف إيش هو.
قلت في نفسي: إيش يعني هالشيء؟ وليش حطوه هنا بالذات؟
بدأت أدور على الجواب.
```

**Output:**
```
وصلت الكورنيش الساعة ستة الصبح. [pause]
المكان كان هادي مرة. [pause]
شفت نصب ما كنت أعرف إيش هو. [long pause]
قلت في نفسي: إيش يعني هالشيء؟ [pause] وليش حطوه هنا بالذات؟ [long pause]
بدأت أدور على الجواب.
```

**What changed:**

| Optimization | Decision | Reason |
|-------------|----------|--------|
| [pause] after sentence 1 | Added | Landing the arrival before moving to observation |
| [pause] after sentence 2 | Added | Brief beat — lets the quietness register |
| [long pause] after sentence 3 | Added | The moment of not-knowing is the hook — needs space |
| Split sentence 4 into two beats | Added [pause] between the two questions | Two questions, two beats — prevents rushing |
| [long pause] after sentence 4 | Added | The questions are the narrative core — the silence after them is the story |
| No [pause] after final sentence | Deliberate | The last line moves forward — no resolution yet |

**Sentence length check:** All sentences deliverable in one natural breath. ✅

**Pace estimate:** 30 Arabic words. At 100–120 wpm plus pause time, approximately 20–25 seconds. This is a test fragment only — a full episode would be 300–500 words.

**Tashkeel:** None present on colloquial words. ✅

**Numbers:** ستة written as word. ✅

---

## Final Script

```
وصلت الكورنيش الساعة ستة الصبح. [pause]
المكان كان هادي مرة. [pause]
شفت نصب ما كنت أعرف إيش هو. [long pause]
قلت في نفسي: إيش يعني هالشيء؟ [pause] وليش حطوه هنا بالذات؟ [long pause]
بدأت أدور على الجواب.
```

**Story type:** Mystery / Hidden Detail (to be confirmed)
**Narrative question:** What is this structure, and why is it here?
**Location:** Jeddah Corniche — early morning
**Estimated duration:** 20–25 seconds (fragment only)

---

## Pipeline Assessment

### What worked

**Stage 2 transformation was the highest-value stage.**
Five sentences of MSA became five sentences of natural Hejazi. The transformation caught every major MSA construction. This confirms the pipeline design: transformation before validation is the right order.

**Stage 3 validation was clean.**
The transformed script passed every check without requiring a return to Stage 2. This means the transformation instruction was clear enough.

**Stage 4 pause placement was the most judgment-dependent step.**
No rule told us where to put [long pause] vs [pause]. This was applied using SARA_VOICE_BIBLE.md principles, not a rule.

---

### Weaknesses discovered

**W-01 — Story type flag does not stop the pipeline**
Stage 1 flags missing story type but still passes the script. In production this could result in a script reaching Stage 4 without a confirmed narrative direction. In V1 this is acceptable for testing. For V2: story type should be a hard requirement.

**W-02 — Stage 3 cannot catch tone issues**
The checklist catches prohibited words and structural violations. It cannot detect when a sentence is technically correct but feels wrong — too flat, too formal in energy, too rushed. Example: "بدأت أدور على الجواب" passes every check but could be more specific. This is a known limitation of rule-based validation. The Knowledge Layer will address this over time.

**W-03 — Pause placement has no rules yet**
Stage 4 pause placement is currently judgment-based. Two different people running the pipeline would produce different pause patterns. V2 should define at least three placement rules: before the narrative question, before the discovery, before the closing line.

**W-04 — No retry was tested**
Stage 3 allows up to two retries before manual correction. This test passed on the first run. The retry mechanism is untested. A future test should deliberately introduce a failing transformation to validate the return path.

---

## Knowledge Log Entries (for KNOWLEDGE_LOG.md — Sprint 004)

| Expression | Status | Note |
|-----------|--------|------|
| بدأت أدور على الجواب | Observation | أدور as "to search" — natural in test but not yet in verified vocabulary |
| الصبح | Observation | Natural Hejazi time suffix — confirmed here, worth promoting to Standard |
| قلت في نفسي | Observation | More natural than تساءلت for internal thought — confirmed |
