# Story Fact-Checking

## Purpose

This document defines how factual claims in Sara's scripts are verified before production.

Fact-checking is not the same as research. Research finds the story. Fact-checking verifies that the story, as written, is accurate.

The distinction matters because errors enter scripts in ways that research cannot always prevent: paraphrasing that drifts from the source, dates that get transposed, names that get conflated, details that are technically correct but misleading in context.

Fact-checking is the final defense against putting false information in Sara's voice.

---

## The Stakes

Sara is a character built on authenticity.

The moment Sara states something confidently that turns out to be wrong — and a viewer knows it — trust is broken. Not just in that episode. In Sara.

A single confident error damages the character more than acknowledged uncertainty. Sara saying "ما أدري بالضبط" loses nothing. Sara saying something definitively wrong loses everything.

This is why fact-checking exists as a separate, mandatory step — not folded into script review or production polish.

---

## What Requires Fact-Checking

Every factual claim in a Sara script requires verification before production. No exceptions.

A factual claim is any statement that can be verified or falsified:

* Dates: founding years, historical periods, when something changed
* Names: people, places, dynasties, guilds, families
* Quantities: heights, distances, durations, counts
* Attributions: who built this, who decided this, who lived here
* Causal claims: why something happened, what caused something to change
* Status claims: this is the oldest, this is the only, this no longer exists

**What does not require fact-checking in the same way:**
* Sara's personal observations ("I noticed...", "it felt like...")
* Sara's emotional reactions ("ما توقعت هذا")
* Stated uncertainty ("there are accounts that suggest...")
* Sara's questions (rhetorical or genuine)

Observations, reactions, and uncertainty are by definition not presented as verified fact. The fact-checking requirement applies to what Sara presents as true.

---

## The Fact-Check Workflow

### Step 1 — Extract All Claims

Read the finalized script and extract every factual claim into a list.

This step must be done on the final script, not an early draft. Claims change between drafts.

Format:

```
Claim: [exact claim as written in script]
Source: [where this came from during research]
Tier: [1 / 2 / 3 — from STORY_RESEARCH_RULES.md source hierarchy]
Status: [Verified / Unverified / Uncertain / Unknown]
```

---

### Step 2 — Verify Each Claim

For each claim in the list:

**If the source is Tier 1 or Tier 2:**
Cross-check the specific claim against the source. Confirm the script matches what the source actually says — not what was remembered or paraphrased from the source.

**If the source is Tier 3:**
The claim is unverified. Find a Tier 1 or Tier 2 source that confirms it before the script proceeds to production.

**If no source exists:**
The claim was not researched. Either find a source, or the claim must be removed from the script or rewritten as stated uncertainty.

---

### Step 3 — Handle Each Unverified Claim

Every unverified claim after Step 2 has exactly three options:

**Option A — Find verification.**
Locate a Tier 1 or Tier 2 source before production begins. If found: verify, update status, proceed.

**Option B — Rewrite as acknowledged uncertainty.**
The claim stays in the script but is rewritten to reflect its actual status.

Before: `هذا البيت بُني في القرن الخامس عشر`
After: `ما أعرف متى بالضبط بُني هذا البيت — بعض المصادر تقول القرن الخامس عشر، بس ما أجد تأكيد واضح`

The rewrite must be honest about the level of uncertainty. "Some say" is only acceptable if someone actually says it in a named source.

**Option C — Remove the claim.**
If neither verification nor honest rewriting is possible, the claim is removed from the script entirely.

There is no Option D. A claim that cannot be verified and cannot be honestly reframed cannot remain in the script as stated fact.

---

### Step 4 — Review Special Claim Types

After the general verification pass, check these specific categories:

**Superlatives and absolutes**
Any claim using "the oldest," "the only," "the tallest," "the most," "the first," "the last" requires special scrutiny. These are high-confidence-sounding claims and are frequently wrong or more complicated than they appear.

Before accepting a superlative, ask: according to whom? Within what defined scope? Is this claim contested anywhere?

**Causal claims**
"This happened because..." is one of the hardest categories to verify. Causation is an interpretation, not a documented fact. Unless a source explicitly makes the causal claim, Sara should present causation as interpretation: "يعني اللي حصل كان..." rather than "هذا بالضبط اللي سبّب..."

**Living practice vs. historical practice**
A practice that was documented in historical sources may not still exist. Confirm that "this still exists" claims are verified against current, not just historical, sources.

**Named individuals**
Historical figures must be traceable. A person's name appearing in only one source, with no corroboration, should be presented as "according to one account" rather than as documented fact.

---

### Step 5 — Document the Results

After fact-checking is complete, record the following in the episode's production notes:

* Total number of factual claims reviewed
* Number verified at Tier 1 or Tier 2
* Number that required rewriting to acknowledged uncertainty
* Number removed
* Any claims that remain at Tier 3 with the decision rationale

This record is part of the episode's production documentation and is filed with the episode log.

---

## Saying "I Don't Know" in Script

Acknowledged uncertainty is not a weakness in Sara's voice. It is a feature.

Sara is a storyteller, not an authority. Her audience follows her because she is honest — including honest about the limits of what she knows.

These phrases are fully acceptable in Sara's scripts, and should be used whenever the research supports them:

```
ما أعرف بالضبط
بعض المصادر تقول... بس ما في إجماع
السالفة ما اتضحت لي كاملاً
هذا ما وجدته — وبعدين اكتشفت إن في ناس يختلفون
إيش يعني هذا بالضبط؟ صراحة، ما أدري
```

Uncertainty presented honestly, in Sara's voice, strengthens the character. It does not undermine it.

---

## Errors Discovered After Publication

If a factual error is discovered after an episode is published:

1. Log the error in `PRODUCTION_DECISIONS_LOG.md` immediately.
2. Assess severity:
   * **Minor** (a date is off by a decade, a name has alternate spellings): note in the log, no immediate action required
   * **Significant** (a central claim is wrong, a person is misidentified, a historical event is misdescribed): produce a correction
3. For significant errors: produce a correction episode note or replacement content as appropriate.

Sara is not infallible. The response to an error is honest acknowledgment — not concealment, not minimization.

---

## Fact-Checking Responsibilities

Fact-checking is a production-phase requirement, not an optional polish step.

No script proceeds to voice production without a completed fact-check record.

The standard is not perfection. The standard is: every claim in the script is either verified against a named source, or honestly framed as uncertain.

That standard is achievable on every episode. It is not negotiable.
