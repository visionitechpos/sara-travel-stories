# Change Report — Language Bible Targeted Improvements

**Date:** 2026-06-21
**File modified:** `docs/SARA_LANGUAGE_BIBLE.md`
**Scope:** Four targeted changes only. No other modifications made.

---

## Change 1 — "هذا اللي يضرب" Moved to Unverified Expressions

**Reason given:** This phrase was not discovered during Sara testing and is not yet considered part of Sara's voice.

**Actions taken:**

1. Removed from **Characteristic Expressions > Observation:**
   ```
   Before: * هذا اللي يضرب — "this is what strikes you"
   After:  [removed]
   ```

2. Removed from **Preferred Phrases table:**
   ```
   Before: | هذا اللي يضرب | Landing an important point |
   After:  [removed]
   ```

3. Added to new **Unverified Expressions** section:
   ```
   | هذا اللي يضرب | Unverified | Not observed during Sara testing. May feel
   too literary for natural conversational speech. Pending production review
   before promotion. |
   ```

**What was not done:** The phrase was not deleted from the document. It is preserved in Unverified Expressions so it can be reviewed and promoted if confirmed through future testing.

---

## Change 2 — "تساءلت" Moved to Occasional Storytelling Language

**Reason given:** It feels more literary than conversational.

**Actions taken:**

1. Removed from **Characteristic Expressions > Curiosity:**
   ```
   Before: * تساءلت — "I wondered"
   After:  [removed from this section]
   ```

2. Added to new **Occasional Storytelling Language** subsection under Sara's Vocabulary Guide:
   ```
   * تساءلت — "I wondered." Has a literary quality. Reserve for moments of
   genuine deliberate reflection, not casual curiosity. Using it too frequently
   makes Sara sound like a narrator, not a person.
   ```

**What was not done:** The word تساءلت was not removed from the document. It was not removed from the Rhetorical Questions section example (line ~290) — that example illustrates question structure, not vocabulary classification.

---

## Change 3 — Verified Expressions Added

**Reason given:** Expressions discovered during production testing, confirmed as part of Sara's natural voice.

**Action taken:** Added new **Verified from Testing** subsection under Sara's Vocabulary Guide, after Occasional Storytelling Language.

| Expression | Meaning | Usage Notes |
|-----------|---------|-------------|
| والله | Honestly / I swear | Genuine exclamation of truth or emphasis. Natural and frequent. |
| ما كنت أدري | I didn't know / I had no idea | Used when a discovery is genuinely unexpected. |
| تخيلوا | Imagine / Can you imagine | Invites the viewer directly into the moment. |
| السالفة | The story / The matter / The thing | Hejazi word for the specific situation at hand. |
| تعجبني مرة | I really like it / It genuinely impresses me | Combines تعجبني with the Hejazi intensifier مرة. |

All five expressions are marked as verified from production testing.

---

## Change 4 — وش Rule Loosened

**Reason given:** Previous rule was too strict. وش should be acceptable occasionally, not prohibited.

**Actions taken:**

1. Updated **Core Vocabulary table** — إيش row:
   ```
   Before: | إيش | What | ماذا / وش (وش is Najdi) |
   After:  | إيش | What | ماذا (too formal) |
   ```

2. Removed **وش from Dialect-Breaking Words table:**
   ```
   Before: | وش | Najdi form of "what" — Sara uses إيش |
   After:  [removed]
   ```

3. Added **Dialect Usage Note** after the Core Vocabulary table:
   ```
   Preferred:  إيش — Sara's natural default for "what"
   Acceptable: وش — may appear occasionally; not a prohibited word
   Avoid:      using وش as Sara's consistent or default style
   ```

---

## Sections Added

| Section | Location | Content |
|---------|----------|---------|
| Occasional Storytelling Language | Under Sara's Vocabulary Guide, after Reflection | Literary expressions used rarely and with intention |
| Verified from Testing | Under Sara's Vocabulary Guide, after Occasional Storytelling Language | 5 testing-confirmed expressions |
| Unverified Expressions | Between Preferred Phrases and Prohibited Phrases | Expressions pending testing confirmation |
| Dialect Usage Note (إيش/وش) | After Core Vocabulary table | Nuanced guidance on both forms |

---

## What Was Not Changed

* All other vocabulary, expressions, and rules in SARA_LANGUAGE_BIBLE.md are unchanged.
* The Rhetorical Questions section example using تساءلت was not modified.
* No expressions were invented or added without a stated testing basis.
* README.md was not modified.
* No other files were modified.
