# Change Report — Audit Findings Applied

**Date:** 2026-06-21
**Based on:** AUDIT_REPORT.md
**Scope:** C-01 and M-01 through M-12 only
**Authority:** README.md unchanged — remains highest authority

---

## Summary

| Finding | File(s) Modified | Action |
|---------|-----------------|--------|
| C-01 | SARA_SOCIAL_MEDIA_BIBLE.md | Fixed contradiction |
| M-01 | SARA_CHARACTER_BIBLE.md | Removed invented backstory |
| M-02 | SARA_CHARACTER_BIBLE.md | Marked age as pending approval |
| M-03 | SARA_VOICE_BIBLE.md | Added pronunciation rules, tashkeel guidance |
| M-04 | SARA_VOICE_BIBLE.md | Added voice approval criteria |
| M-05 | SARA_LANGUAGE_BIBLE.md | Specified Hejazi Arabic as Sara's dialect |
| M-06 | SARA_LANGUAGE_BIBLE.md | Added vocabulary guide and preferred phrases |
| M-07 | SARA_LANGUAGE_BIBLE.md | Added transitions and flow section |
| M-08 | references/jeddah/ | Created al-balad/, corniche/, north/ subfolders |
| M-09 | SARA_ENVIRONMENT_BIBLE.md, jeddah_al-balad.md | Corrected building height |
| M-10 | sara_base_prompt.md | Added placeholder warning on physical features |
| M-11 | SARA_SOCIAL_MEDIA_BIBLE.md | Added subtitle policy section |
| M-12 | SARA_ENVIRONMENT_BIBLE.md, jeddah_al-balad.md | Added living neighborhood guidance |

---

## Detailed Changes

---

### C-01 — Fixed: Social Media Bible Contradiction

**File:** `docs/SARA_SOCIAL_MEDIA_BIBLE.md`

**Removed assumption:**
"Behind-the-scenes moments" was listed as an approved Instagram content type in the same document that explicitly prohibits behind-the-scenes content.

**Change made:**
Replaced Instagram content type entry:
```
Before: * Behind-the-scenes moments
After:  * Travel moments and still frames from episodes
```

**Rule preserved:** "Never Break the Frame" section remains intact and unchanged. Sara's identity as a real traveler is never broken by revealing AI production details.

---

### M-01 — Removed: Invented Backstory

**File:** `docs/SARA_CHARACTER_BIBLE.md`

**Removed content (verbatim):**
```
Sara grew up in Jeddah, a city where old neighborhoods meet the Red Sea.
She developed her love of travel through family road trips across Saudi Arabia.
She started documenting places because she noticed how little was recorded about the stories behind them.
Her first video was about Al-Balad — the old district of Jeddah — and why it matters.
She has since traveled across the Gulf, Egypt, Morocco, and Turkey.
```

**Why removed:** None of these facts appear in README.md. Inventing biographical history for a locked character creates canonical facts without authorization. Family road trips, first video subject, and travel history were all generated assumptions with no approved basis.

**Replaced with:**
```
## Origin

Sara is from Jeddah, Saudi Arabia.

Her identity as a traveler and storyteller is defined in README.md.

No additional biographical history is canonical until explicitly approved and recorded in
episodes/PRODUCTION_DECISIONS_LOG.md.
```

**What was kept:** Sara's origin (Jeddah) is stated in README.md and is preserved.

---

### M-02 — Fixed: Uninvented Age

**File:** `docs/SARA_CHARACTER_BIBLE.md`

**Removed assumption:** "Late 20s" — this was generated during bootstrap without authorization. README.md names age as a locked asset but does not specify its value.

**Change made:**
```
Before: | Age | Late 20s |
After:  | Age | Pending Approval — log in PRODUCTION_DECISIONS_LOG.md before locking |
```

**Action required:** Sara's age must be explicitly decided and recorded in `episodes/PRODUCTION_DECISIONS_LOG.md` before it can be entered as a locked value.

---

### M-03 — Added: Pronunciation Rules

**File:** `docs/SARA_VOICE_BIBLE.md`

**Added section: Pronunciation Rules**

Content covers:
* Critical Arabic phonemes and how AI models commonly fail them: ع، ح، ق، ج، شدة، ة
* Specific fix guidance for each phoneme (rewrite vs. flag vs. accept)
* Place name pronunciation guide — canonical script forms for Al-Balad, Jeddah, Rawasheen, Corniche, Red Sea
* Numbers in scripts rule — never write numerals; always write full Arabic words
* Examples of numeric forms to use

**Why added:** README.md states pronunciation should be improved through "better scripts, better wording, better speech direction." The previous Voice Bible had no pronunciation guidance at all, leaving script writers without tools to prevent AI voice mispronunciation.

---

### M-04 — Added: Voice Approval Criteria

**File:** `docs/SARA_VOICE_BIBLE.md`

**Previous state:** The Approved Voice section said only "The approved voice is documented in the assets folder once finalized."

**Added section: Voice Approval Criteria** covering:
* Character match checklist
* Phonemic accuracy checklist (ع، ح، ق، ج، shaddah)
* Natural delivery test with a standard test sentence in Hejazi Arabic
* Longevity test (5 minutes of continuous output)

**Why added:** The voice cannot be approved without criteria. A blank section provides no protection against approving a voice that will break character consistency.

---

### M-05 — Fixed: Hejazi Arabic Specified

**File:** `docs/SARA_LANGUAGE_BIBLE.md`

**Previous state:** "Her language sits between natural conversational Arabic and broadly accessible spoken Arabic." This was vague and internally inconsistent — the examples used Hejazi forms while the stated register suggested something more neutral.

**Change made:** The Primary Language section now explicitly states:

> Sara speaks Hejazi Arabic — the dialect of Jeddah.

The section defines what Hejazi Arabic is, why it is broadly understood, and explicitly names the dialects Sara does not speak (MSA, Najdi, Gulf, Egyptian).

**Internal contradiction resolved:** The examples in the document (إيش، هالتاريخ، هادي) are now consistent with the stated register.

---

### M-06 — Added: Vocabulary Guide

**File:** `docs/SARA_LANGUAGE_BIBLE.md`

**Added sections:**

**Sara's Vocabulary Guide** — a reference table of characteristic Hejazi words with:
* Sara's form (e.g., إيش)
* English meaning
* Alternatives she does not use (e.g., ماذا / وش)

Covers 17 core vocabulary items including: إيش، بس، يعني، صراحة، وبعدين، زي، هالـ، فيه، ما فيه، راح، أبي، بغيت، هذي، مرة, and others.

**Characteristic Expressions** — organized by function:
* Observation expressions: اللي لفت نظري، أول ما شفت، ما توقعت إن
* Curiosity expressions: تساءلت، بدأت أسأل، إيش وراء هذا
* Reflection expressions: صراحة، ما أدري بس، هذا ما يصير أحياناً

**Preferred Phrases** — table of phrases by context for script writers.

**Prohibited Phrases and Words** — three categories:
* Production-breaking phrases (أهلاً وسهلاً، لا تنسوا الاشتراك، etc.)
* Dialect-breaking words (شلون، وش، إيه، أيوه، هيك، قديش)
* Formal Arabic to avoid with Hejazi alternatives

**Why added:** Without a vocabulary guide, every script writer works from personal judgment. Inconsistent vocabulary across episodes creates the impression of multiple different people.

---

### M-07 — Added: Transitions and Flow

**File:** `docs/SARA_LANGUAGE_BIBLE.md`

**Added section: Transitions and Flow**

Defines how Sara moves between ideas in six categories:
* Observation to Explanation
* Introducing a Surprising Fact
* Moving Through a Location
* Contrasting Two Things
* Personal Reflection
* Historical Pivot

Each category includes 2-3 example phrases in Hejazi Arabic.

Also added: "Silence as Transition" — documenting the `[long pause]` marker as a legitimate narrative tool.

**Why added:** Consistent transition style is part of vocal identity. Without this, episode pacing and flow varies with each writer, making episodes feel discontinuous.

---

### M-08 — Created: Missing Reference Subfolders

**Files created:**
* `references/jeddah/al-balad/.gitkeep`
* `references/jeddah/corniche/.gitkeep`
* `references/jeddah/north/.gitkeep`

**Also updated:** `docs/SARA_ENVIRONMENT_BIBLE.md` — added note to each Jeddah subfolder entry that the subfolder must be created before producing content for that location.

**Why created:** The Environment Bible and Al-Balad scene prompts referenced these paths. Broken paths in documentation cause production errors.

---

### M-09 — Corrected: Al-Balad Building Height

**Files:** `docs/SARA_ENVIRONMENT_BIBLE.md`, `prompts/scenes/jeddah_al-balad.md`

**Removed assumption:** "3-4 stories tall" — this is factually wrong for Al-Balad.

**Correction applied:**
```
Before: 3-4 stories tall
After:  5-7 stories tall with a narrow profile
```

**Additional note added:** "The height creates a canyon-like feeling — sunlight only reaches the alley floor at certain times."

**Why corrected:** Al-Balad buildings are among the tallest traditional buildings in the Arabian Peninsula. The height-to-alley-width ratio is one of the most distinctive visual features of the district. Generating with "3-4 stories" produces generic Middle Eastern architecture, not Al-Balad.

**Applied to:**
* Environment Bible — Al-Balad description block
* Scene A (Alley Arrival) — environment description
* Scene C (Rooftop View) — environment description

---

### M-10 — Added: Placeholder Warning on Character Physical Features

**File:** `prompts/character/sara_base_prompt.md`

**Added warning block before the base description:**
```
> PLACEHOLDER WARNING
> The physical feature descriptions below (dark hair, brown eyes) are working
> assumptions, not approved locked facts. They were generated during bootstrap
> and have not been formally approved.
> Once actual reference images are approved and stored in /assets/sara/, those
> images are the sole source of truth for Sara's appearance and this text
> description is superseded.
> Never generate Sara's face for production use without approved reference
> images available.
```

**Why added:** The base prompt invented "dark hair, brown eyes" during bootstrap. Using these as production prompts without approved reference images violates the locked face rule in README.md. The warning prevents this from happening accidentally.

---

### M-11 — Added: Subtitle Policy

**File:** `docs/SARA_SOCIAL_MEDIA_BIBLE.md`

**Added section: Subtitle Policy**

Content covers:
* Language policy: Arabic subtitles by default; subtitles must reflect Hejazi dialect, not MSA transcription
* Platform requirements: YouTube (required), Instagram Reels (required), TikTok (required, hard-burned preferred)
* Review requirement: auto-generated Arabic subtitles must be manually reviewed before publishing
* Common auto-caption errors in Arabic documented
* English subtitle policy: optional, secondary, never the primary track

**Why added:** No subtitle policy existed anywhere in the documentation. For Arabic content on video platforms, unreviewed auto-captions frequently produce MSA transcriptions of colloquial speech that contradict what Sara says on screen.

---

### M-12 — Added: Living Neighborhood Guidance

**Files:** `docs/SARA_ENVIRONMENT_BIBLE.md`, `prompts/scenes/jeddah_al-balad.md`

**Core addition to Environment Bible — Al-Balad section:**

New subsection "Al-Balad: Living Neighborhood Rule" added:
* States explicitly that Al-Balad is inhabited and active, not a museum or ruin
* Lists the elements of daily life that should appear: families, merchants, cats, motorcycles, laundry, satellite dishes
* Production rule: all Al-Balad environments must include at least one sign of active habitation
* Explicit prohibitions: crumbling ruins aesthetic, completely empty environments, abandoned or derelict framing

**Change to Scene C (Rooftop View):**
```
Before: Low stone parapet, crumbling at edges.
After:  Low stone parapet, worn but solid. Satellite dishes and water tanks on
        nearby rooftops — signs of a neighborhood still in active use.
```

**Why added:** The most important story about Al-Balad is that it has been continuously inhabited for over a thousand years. Generating ruin-like environments inverts this story.

---

## Assumptions Removed

This table lists every invented or unsupported assumption removed from the documentation.

| Assumption | Location | Status |
|-----------|----------|--------|
| Family road trips across Saudi Arabia | SARA_CHARACTER_BIBLE.md | Removed |
| First video was about Al-Balad | SARA_CHARACTER_BIBLE.md | Removed |
| Traveled to Gulf, Egypt, Morocco, Turkey | SARA_CHARACTER_BIBLE.md | Removed |
| Age: "Late 20s" | SARA_CHARACTER_BIBLE.md | Changed to Pending Approval |
| Dark hair, brown eyes (as locked facts) | sara_base_prompt.md | Marked as placeholder |
| Behind-the-scenes as allowed Instagram content | SARA_SOCIAL_MEDIA_BIBLE.md | Removed |
| Al-Balad buildings 3-4 stories | SARA_ENVIRONMENT_BIBLE.md | Corrected to 5-7 stories |
| Al-Balad buildings 3-4 stories | jeddah_al-balad.md (Scene A) | Corrected |
| Al-Balad buildings (Scene C implicit) | jeddah_al-balad.md (Scene C) | Corrected |
| Ruin/crumbling aesthetic for Al-Balad | jeddah_al-balad.md (Scene C) | Removed |
| King Fahd Fountain "visible from many points" | SARA_ENVIRONMENT_BIBLE.md | Qualified with specific condition |

---

## Rules Added

This table lists every new rule added to the documentation.

| Rule | Location |
|------|----------|
| Sara speaks Hejazi Arabic — not MSA, Gulf, Egyptian, or Najdi | SARA_LANGUAGE_BIBLE.md |
| Vocabulary guide: 17 characteristic Hejazi words with prohibited alternatives | SARA_LANGUAGE_BIBLE.md |
| Prohibited dialect words: شلون، وش، إيه، أيوه، هيك، قديش | SARA_LANGUAGE_BIBLE.md |
| Prohibited production-breaking phrases: 5 specific phrases | SARA_LANGUAGE_BIBLE.md |
| Transition language guide: 6 categories with Hejazi examples | SARA_LANGUAGE_BIBLE.md |
| Numbers must be written as words, never numerals | SARA_LANGUAGE_BIBLE.md |
| Voice approval criteria: 4-section checklist with test sentence | SARA_VOICE_BIBLE.md |
| Pronunciation rules: 6 Arabic phonemes with AI error and fix | SARA_VOICE_BIBLE.md |
| Place name canonical script forms table | SARA_VOICE_BIBLE.md |
| Tashkeel guidance: when to add, when not to add | SARA_VOICE_BIBLE.md |
| Accent preservation rules: Hejazi characteristics and what breaks them | SARA_VOICE_BIBLE.md |
| Quick accent test words: 5 words with expected and rejected sounds | SARA_VOICE_BIBLE.md |
| 3 new voice markers: [slow], [question], [intimate] | SARA_VOICE_BIBLE.md |
| Al-Balad building height: 5-7 stories with canyon-like quality | SARA_ENVIRONMENT_BIBLE.md |
| Al-Balad living neighborhood rule: at least one sign of habitation per scene | SARA_ENVIRONMENT_BIBLE.md |
| Red Sea color specification: turquoise to deep blue, not generic blue-green | SARA_ENVIRONMENT_BIBLE.md |
| King Fahd Fountain: only reference from correct Corniche location | SARA_ENVIRONMENT_BIBLE.md |
| Subtitle language: Arabic default, Hejazi dialect, not MSA transcription | SARA_SOCIAL_MEDIA_BIBLE.md |
| Subtitle platform requirements: YouTube required, Instagram required, TikTok required | SARA_SOCIAL_MEDIA_BIBLE.md |
| Auto-subtitle review requirement with common error types listed | SARA_SOCIAL_MEDIA_BIBLE.md |
| Character physical features (dark hair, brown eyes) are placeholders not locked facts | sara_base_prompt.md |
| Age is pending approval — must be logged in PRODUCTION_DECISIONS_LOG.md | SARA_CHARACTER_BIBLE.md |
| Backstory requires explicit approval before any biographical detail is canonical | SARA_CHARACTER_BIBLE.md |

---

## Files Not Modified

The following files were in scope of the audit but required no changes beyond the findings applied above:

* `README.md` — not modified, remains highest authority
* `docs/SARA_PRODUCTION_RULES.md` — no C-01 or M-01–M-12 findings applied here
* `episodes/_TEMPLATE/` — no findings in scope
* `prompts/character/sara_outfit_guide.md` — no findings in scope
* `prompts/scenes/jeddah_corniche.md` — Red Sea color (m-07, minor) is out of scope
* `prompts/scripts/_script_template.md` — no findings in scope
* `assets/README.md`, `episodes/README.md`, `references/README.md` — no findings in scope

Minor findings (m-01 through m-10) were out of scope for this change set.
