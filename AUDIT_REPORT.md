# Documentation Audit Report

**Date:** 2026-06-21
**Auditor:** Claude Sonnet 4.6
**Scope:** All files created during bootstrap process
**Authority:** README.md (highest authority — not modified)

---

## Audit Summary

| Severity  | Count | Status          |
|-----------|-------|-----------------|
| Critical  | 1     | Must fix before any publishing |
| Major     | 12    | Must fix before first episode  |
| Minor     | 10    | Address over time              |

---

## Critical Issues

---

### C-01 — Direct Contradiction in Social Media Bible

**File:** `docs/SARA_SOCIAL_MEDIA_BIBLE.md`
**Lines:** 69 vs 130

The same document says two opposite things.

Under Instagram content types (line 69):
```
* Behind-the-scenes moments
```

Under "Never Break the Frame" (line 130):
```
Do not post:
* Behind-the-scenes of the AI production process
```

The first entry permits behind-the-scenes content. The second explicitly prohibits it.

This is not a nuance issue — it is a direct contradiction that will cause consistent publishing mistakes.

**Recommendation:** Remove "Behind-the-scenes moments" from Instagram content types. Replace with "Travel moments and still frames from episodes."

---

## Major Issues

---

### M-01 — Invented Backstory Added to Locked Character

**File:** `docs/SARA_CHARACTER_BIBLE.md`
**Section:** Backstory

The Backstory section contains details that do not appear in README.md and were never approved:

* "family road trips across Saudi Arabia"
* "her first video was about Al-Balad"
* "she has since traveled across the Gulf, Egypt, Morocco, and Turkey"

README.md defines Sara's identity as locked. Adding canonical backstory facts without approval contradicts the locked status. If these invented facts are treated as truth in future production, they create constraints that were never sanctioned.

The character bible should describe who Sara is as a storyteller. It should not invent biographical history.

**Recommendation:** Remove the Backstory section entirely, or replace it with a clearly labeled "Suggested Backstory — Pending Approval" section with an explicit note that none of it is canonical until approved.

---

### M-02 — Sara's Age Invented Without Authorization

**File:** `docs/SARA_CHARACTER_BIBLE.md`
**Section:** Identity table

README.md states that Sara's age is a locked asset. It does not state what the age is.

The Character Bible assigns "Late 20s" without any authorization from README.md. Age is locked — meaning it cannot be changed once set — which makes choosing it an act requiring explicit approval.

**Recommendation:** Replace "Late 20s" in the identity table with `[Pending Approval]` and add a note that the age must be formally approved and recorded in PRODUCTION_DECISIONS_LOG.md before being entered here.

---

### M-03 — Voice Bible Has No Pronunciation Guidance

**File:** `docs/SARA_VOICE_BIBLE.md`

README.md states:
> "Improve pronunciation through better scripts, better wording, better speech direction."

The Voice Bible has no pronunciation guidance at all. It covers pacing and tone but nothing about:

* Arabic phonemes that AI voice models frequently mispronounce (ق، ع، غ، ح، خ)
* How to write place names in scripts to improve pronunciation (e.g., writing "البلد القديم" vs writing it phonetically for a voice model)
* How to write numbers in scripts — never as numerals, always as words, with specific forms
* How to handle foreign words or proper nouns (Rawasheen, Corniche, UNESCO)
* How to indicate word stress or emphasis in a script
* How to avoid the "reading" quality in AI-generated Arabic by restructuring specific sentence types

Pronunciation guidance is mentioned as a key tool in README.md. The current document ignores it.

**Recommendation:** Add a dedicated Pronunciation section covering the above points with concrete before/after examples in Arabic.

---

### M-04 — Approved Voice Section Is Empty

**File:** `docs/SARA_VOICE_BIBLE.md`
**Section:** Approved Voice

The section currently says:
> "The approved voice is documented in the assets folder once finalized."

This is a placeholder, not a bible entry. The Voice Bible must define:

* What criteria a voice must meet to be approved (not just where to document it once it is)
* What the approval process looks like
* Minimum quality benchmarks (e.g., naturalness score, specific sound test words)
* What a "sample reference file" should contain

**Recommendation:** Add a "Voice Approval Criteria" section that defines what makes a voice acceptable, even before a specific voice is chosen.

---

### M-05 — Sara's Dialect Is Never Specified

**File:** `docs/SARA_LANGUAGE_BIBLE.md`
**Section:** Primary Language

The Language Bible says Sara "speaks the way a real Saudi person would speak to a friend" and her language "sits between natural conversational Arabic and broadly accessible spoken Arabic."

This is vague enough to produce inconsistency.

The examples in the same document use Hejazi Arabic — the dialect of Jeddah:
* "هادي" (instead of MSA "هادئ")
* "إيش" (instead of "ماذا" or "وش")
* "هالتاريخ" (Hejazi contraction)

But the stated register ("broadly accessible spoken Arabic") would suggest something more neutral.

These two positions contradict each other internally. A writer following the stated rule would write differently than a writer following the examples.

Sara is from Jeddah. She speaks Hejazi Arabic. This should be stated explicitly.

**Recommendation:** State clearly that Sara speaks Hejazi Arabic — the dialect of Jeddah — with the understanding that Hejazi Arabic is broadly understood across the Arab world due to Saudi media reach. Remove the vague "broadly accessible" framing.

---

### M-06 — Missing Vocabulary Guide for Sara's Characteristic Language

**File:** `docs/SARA_LANGUAGE_BIBLE.md`

The Language Bible defines structure rules and examples, but never defines Sara's characteristic vocabulary — the specific words and expressions that mark her as Sara.

A script writer who doesn't know Hejazi Arabic might write generic Gulf Arabic or MSA. Without a vocabulary anchor, Sara could sound like she's from Dubai one episode and Cairo the next.

Missing:
* Sara's natural connectors: "بس" (but/only), "يعني" (I mean), "صراحة" (honestly), "وبعدين" (and then)
* Her characteristic question forms: "إيش" not "ماذا/وش"
* Her affirmatives/negatives in natural speech
* Common Jeddah-specific expressions or references she would naturally use
* Words to avoid because they belong to other dialects

**Recommendation:** Add a "Sara's Vocabulary" section with a small reference table of characteristic words and expressions, contrasted against alternatives she would not use.

---

### M-07 — Missing Transition Language Guide

**File:** `docs/SARA_LANGUAGE_BIBLE.md`

Related to M-06 but distinct. The Language Bible defines how Sara opens and closes episodes, but nothing about how she moves between ideas within a script.

Natural spoken Arabic uses specific transitional expressions. If scripts don't use Sara's consistent transition style, the voice will feel like it comes from different people across episodes.

Examples of missing guidance:
* How Sara moves from observation to explanation ("يعني...")
* How she introduces a surprising fact ("اللي ما توقعته...")
* How she transitions from historical context to personal reaction
* How she uses silence/pause as a transition (already in voice markers but not in language context)

**Recommendation:** Add a "Transitions and Flow" section with specific examples of how Sara bridges story beats.

---

### M-08 — Reference Subfolders Mentioned in Environment Bible Do Not Exist

**File:** `docs/SARA_ENVIRONMENT_BIBLE.md`
**Section:** Jeddah

The Environment Bible references these paths:
* `/references/jeddah/al-balad/`
* `/references/jeddah/corniche/`
* `/references/jeddah/north/`

The current repository structure contains only `/references/jeddah/` with a `.gitkeep`. None of the three subfolders exist.

The Al-Balad scene prompts also reference `/references/jeddah/al-balad/`.

Any producer following these documents will find broken paths.

**Recommendation:** Create the three subfolders: `references/jeddah/al-balad/`, `references/jeddah/corniche/`, `references/jeddah/north/`. Add a README or index file to each explaining what reference images are needed and what to look for.

---

### M-09 — Al-Balad Building Height Is Factually Wrong

**Files:** `docs/SARA_ENVIRONMENT_BIBLE.md`, `prompts/scenes/jeddah_al-balad.md`

Both documents describe Al-Balad buildings as "3-4 stories tall."

Al-Balad buildings are famously among the tallest traditional buildings in the Arabian Peninsula. The historic merchant houses (called Hejazi houses) typically rise 5-7 stories, sometimes more. Their tall, narrow profile rising from narrow alleys is one of the most distinctive visual features of the district — it creates a canyon-like feeling in the alleys that is very different from a 3-4 story environment.

Using "3-4 stories" in visual prompts will generate buildings that look like generic Middle Eastern architecture, not Al-Balad.

**Recommendation:** Correct to "5-7 stories tall, narrow profile" in both documents. Add a note about the canyon-like quality of the alleys created by the building height ratio.

---

### M-10 — Character Base Prompt Invents Physical Features Without Placeholder Warning

**File:** `prompts/character/sara_base_prompt.md`
**Section:** Base Character Description

The base prompt states:
```
She has a warm, natural appearance. Dark hair, brown eyes.
```

README.md does not describe Sara's physical features beyond stating her face is locked. Dark hair and brown eyes were invented during bootstrap. This is understandable as a starting point, but the prompt carries no warning that these are placeholders pending approval of actual reference images.

If a visual is generated from this text prompt and used as production content, it creates a face that was never formally approved — violating the locked face rule.

**Recommendation:** Add a prominent warning: "These physical feature descriptions are working placeholders only. Once actual reference images are approved and stored in `/assets/sara/`, this text description is superseded. Never generate Sara's face without approved reference images available."

---

### M-11 — No Subtitle Policy Anywhere in Documentation

**Files:** All docs

No document mentions subtitles. For Arabic-language video content:

* Arabic subtitles are standard on YouTube and increase accessibility
* TikTok content without subtitles performs significantly worse
* Social Media Bible mentions "Subtitles always on for TikTok" but this is the only mention anywhere

Missing across all documents:
* What subtitle language(s) to use
* Whether subtitles are generated automatically or manually reviewed
* How to review AI-generated Arabic subtitles for accuracy
* Whether subtitles should appear on-screen during production or only on the platform

**Recommendation:** Add a Subtitles section to either SARA_PRODUCTION_RULES.md or SARA_SOCIAL_MEDIA_BIBLE.md defining the subtitle policy across all platforms.

---

### M-12 — Missing Jeddah Context: Al-Balad as a Living Neighborhood

**File:** `docs/SARA_ENVIRONMENT_BIBLE.md`, `prompts/scenes/jeddah_al-balad.md`

The Environment Bible and Al-Balad scene prompts describe Al-Balad in architectural terms but miss a critical fact that directly affects how environments should be generated and described:

Al-Balad is not a museum or a ruin. It is a living, inhabited neighborhood. People live in many of the historic buildings. There are families, markets, small shops, craftsmen, cats, laundry on lines, parked motorcycles, everyday life.

Scene C in the Al-Balad prompts describes a "low stone parapet, crumbling at edges" — this pushes toward a "ruin" aesthetic. Environments that look abandoned or crumbling do not represent Al-Balad accurately and create the wrong impression about the place.

The most important story about Al-Balad is precisely that it is still alive despite its age.

**Recommendation:** Add a "Living vs. Ruin" note to the Al-Balad environment documentation explicitly stating that Al-Balad is inhabited and active, and that environments should show signs of life — not a dead or ruined aesthetic. Adjust Scene C prompt accordingly.

---

## Minor Issues

---

### m-01 — Feminine Address Form Unexplained

**File:** `docs/SARA_LANGUAGE_BIBLE.md`
**Section:** Language Register

The Language Register table shows `"أنتِ"` (feminine form) as the preferred direct address. The choice of feminine form is not explained. Does Sara address all viewers using feminine Arabic forms? This would be unusual. Does she use feminine forms because she's speaking as a woman? Or is this a specific stylistic choice?

**Recommendation:** Add one sentence clarifying why the feminine form is shown here, or correct to an explanation of how Sara addresses different viewer genders (likely she uses neutral/masculine default as is standard in Arabic media).

---

### m-02 — Voice Script Markers Are Incomplete

**File:** `docs/SARA_VOICE_BIBLE.md`
**Section:** Script Markers for Voice

Current markers: `[pause]`, `[long pause]`, `[warm]`, `[focus]`, `[wonder]`

Missing markers that would be useful in practice:
* `[slow]` — for moments where pacing needs to slow dramatically
* `[question]` — rising inflection for rhetorical questions
* `[intimate]` — very close, personal, quiet delivery

**Recommendation:** Add the missing markers with usage examples.

---

### m-03 — Production Rules Has Duplicate Checklists

**Files:** `docs/SARA_PRODUCTION_RULES.md`, `episodes/_TEMPLATE/REVIEW.md`

The Episode Review Checklist in PRODUCTION_RULES.md (lines 94-123) and the REVIEW.md template are nearly identical. Maintaining two copies creates risk of them drifting apart over time.

**Recommendation:** PRODUCTION_RULES.md should reference REVIEW.md rather than duplicating the checklist. Or the Production Rules version should be the master, and REVIEW.md should import/reference it.

---

### m-04 — No Episode Target Length Defined

**File:** `docs/SARA_PRODUCTION_RULES.md`

The script template references 3–10 minute episode lengths, but nowhere in the production rules is a target episode length defined for Sara's standard format. README.md says "5-15 minutes" appears in the Social Media Bible but not as a defined standard.

**Recommendation:** Add a default episode length target (e.g., "5-8 minutes for standard episodes") to SARA_PRODUCTION_RULES.md.

---

### m-05 — Music Source Not Defined

**File:** `docs/SARA_PRODUCTION_RULES.md`
**Section:** Music Rules

The rules say "Do not use recognizable commercial tracks" but provide no guidance on where music should come from or what tools/libraries are approved for sourcing music.

**Recommendation:** Add a line recommending specific sources for copyright-free music appropriate for this project type.

---

### m-06 — Scene Prompts Missing Negative Prompt Guidance

**File:** `prompts/character/sara_base_prompt.md`, `prompts/scenes/`

Most AI image generation tools use negative prompts to exclude unwanted features. No document mentions negative prompts.

Common things that should be excluded for Sara: "anime style, illustration, overly stylized, artificial looking, uncanny, plastic skin, high fashion, western features, model pose"

**Recommendation:** Add a negative prompts section to `sara_base_prompt.md` and a note in `_scene_template.md` about including negatives in production prompts.

---

### m-07 — Red Sea Color Description Is Generic

**File:** `prompts/scenes/jeddah_corniche.md`

"Deep blue-green" for the Red Sea is generic. The Red Sea near Jeddah is notable for its exceptional clarity and characteristic turquoise color in shallow areas, shifting to deep blue offshore. This specificity helps distinguish Jeddah Corniche from any other generic waterfront.

**Recommendation:** Replace "deep blue-green" with "clear turquoise to deep blue, exceptional visibility, distinctly warm-toned in late afternoon light."

---

### m-08 — Social Media Bible Missing Handle Documentation

**File:** `docs/SARA_SOCIAL_MEDIA_BIBLE.md`

No mention of Sara's social media handles/account names. When these are established they need a canonical home in the documentation.

**Recommendation:** Add a "Platform Accounts" section (can be blank initially) where handle names are recorded once approved.

---

### m-09 — Arabic vs English in Captions Not Defined

**File:** `docs/SARA_SOCIAL_MEDIA_BIBLE.md`

The document specifies caption style but never addresses whether captions should be Arabic only, Arabic with English translation, or bilingual. This matters especially for Instagram which serves both Arabic and international audiences.

**Recommendation:** Add a language policy for captions on each platform.

---

### m-10 — Word Count Rate Not Verified for AI-Generated Arabic

**File:** `prompts/scripts/_script_template.md`
**Section:** Script Duration Guide

The table uses "120-150 words/minute" for Arabic. Human spoken Arabic is approximately 120-150 words/minute. AI-generated Arabic voice (especially Hejazi Arabic) often runs closer to 100-120 words/minute due to longer pauses between words and slightly slower phoneme generation.

If scripts are written to the 150-word/minute target, episodes may run significantly longer than planned.

**Recommendation:** Flag this as "estimate — verify against actual voice output from approved model" and suggest using 110 words/minute as a conservative planning figure until verified.

---

## Files Not Audited

The following files require no changes based on this audit:

* `README.md` — highest authority, not modified, no issues found
* `episodes/README.md` — functional, no issues
* `episodes/PRODUCTION_DECISIONS_LOG.md` — functional, no issues
* `assets/README.md` — functional, no issues
* `references/README.md` — functional, no issues
* `prompts/README.md` — functional, no issues
* `episodes/_TEMPLATE/CONCEPT.md` — functional, no issues
* `episodes/_TEMPLATE/PRODUCTION_NOTES.md` — minor (voice platform field missing, single-row issue log)
* `prompts/character/sara_outfit_guide.md` — consistent, no issues

---

## Recommended Fix Priority

### Before Any Episode Production Begins

1. C-01 — Fix Social Media Bible contradiction
2. M-01 — Remove or quarantine invented backstory
3. M-02 — Mark Sara's age as pending approval
4. M-03 — Add pronunciation guidance to Voice Bible
5. M-05 — Specify Sara's dialect as Hejazi Arabic
6. M-06 — Add vocabulary guide
7. M-08 — Create missing reference subfolders
8. M-09 — Correct Al-Balad building height to 5-7 stories
9. M-10 — Add placeholder warning to sara_base_prompt.md
10. M-12 — Add living neighborhood note for Al-Balad

### Before Publishing Episode 1

11. M-04 — Approve voice and complete the Approved Voice section
12. M-07 — Add transition language guide
13. M-11 — Define subtitle policy

### Ongoing Improvements

14. m-01 through m-10 as encountered in production

---

## Closing Note

The bootstrap documents are structurally sound and generally faithful to README.md principles. The issues found are largely of two types:

1. **Invented specifics** — age, backstory, physical features — that were generated to fill document space but were never authorized. These need to be clearly marked as placeholders or removed.

2. **Missing depth** — particularly in pronunciation guidance, dialect specification, and Jeddah-specific context. These gaps will cause consistency problems as soon as actual episode production begins.

The most urgent fix is C-01 (the Social Media contradiction), followed by the invented backstory and age issues, followed by the pronunciation and dialect gaps.

No files require wholesale rewriting. Targeted additions and corrections will resolve all findings.
