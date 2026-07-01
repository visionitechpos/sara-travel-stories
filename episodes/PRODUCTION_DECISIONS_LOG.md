# Production Decisions Log

This file records significant decisions made during production.

Every decision that might be questioned, revisited, or referenced in the future should be logged here.

Format: date, decision, reason.

---

## Log

### 2026-07-02 — Sync: Veo Character Info (Physical Details + Voice Status)

**Decision:** Synced `SARA_CHARACTER_BIBLE.md` and `SARA_VOICE_BIBLE.md` against the full Character Info text from Sara's approved Veo Character Production.

**New physical details added (not previously documented):** height ~168cm with balanced proportions, confident upright posture, graceful relaxed body language, natural eye contact, warm smile, relaxed realistic hand gestures while speaking. Added a style nuance: Sara is presentation-conscious as a Jeddawi woman, not just practical.

**Voice status corrected:** `SARA_VOICE_BIBLE.md` said the voice was "not yet formally selected" — this predated confirmation that voice is bundled into the Veo Character (not a separate external TTS model/platform). Documentation sync, not a new decision. The Voice Approval Criteria checklist is still unverified against an actual Veo audio sample — that remains open.

**Flagged, not decided:** voice being native to the Veo Character may resolve the open "native Veo dialogue vs. audio replacement" question in `docs/veo/SARA_PRODUCTION_GUIDE.md` — this is noted as a strategic implication requiring explicit user confirmation, not assumed or auto-resolved here.

**Wardrobe language check:** Character Info describes wardrobe as "intentionally flexible... may vary between episodes." Confirmed compatible with the existing Wardrobe Log system (`sara_outfit_guide.md`) — flexible/context-appropriate reuse, not literally unlimited new outfits. No conflict, no change made.

---

### 2026-07-01 — Sara's Visual Reference Sync Closed

**Decision:** Sara's approved face reference (`sara-face-reference-approved-2026-07-01.jpeg`, Google Drive `assets/sara/`) is now the confirmed source of truth, replacing the bootstrap-era text placeholder in `sara_base_prompt.md` ("dark hair, brown eyes" — never approved, written before any real reference existed).

**Reason:** Closes a documentation sync gap flagged repeatedly during this production cycle (architecture audit, Step 5 asset review). Confirmed observed features: warm olive/tan skin tone, dark thick eyebrows, brown eyes, warm approachable smile. Confirmed the hijab as a fixed identity feature — she is never depicted without one, which was not previously locked in documentation.

**Files updated:** `docs/SARA_CHARACTER_BIBLE.md`, `prompts/character/sara_base_prompt.md`, `assets/README.md`.

---

### 2026-07-01 — First Wardrobe Look Approved: Look 1 — Coastal Light

**Decision:** Sara's clothing is treated as a fixed, limited wardrobe — approved looks are reused across episodes rather than generating a new outfit every time. "Look 1 — Coastal Light" (sandy beige abaya and hijab, white sneakers) is the first approved entry, generated via ChatGPT using Sara's approved Veo face reference as the base, verified by human review as a genuine match to Sara. Logged in `prompts/character/sara_outfit_guide.md` — Wardrobe Log.

**Reason:** Without a tracked wardrobe, every episode would risk inventing a new outfit, which is unrealistic (a real person doesn't wear something new every single day) and creates unnecessary visual inconsistency across episodes.

**How to apply:** Before generating a wardrobe image for any future episode, check the Wardrobe Log first. Only generate a new look if no existing one fits the location/story. Reference image stored in Google Drive: `Sara Travel Stories - Media/assets/sara/wardrobe/`.

---

### 2026-07-01 — Media Storage Moved to Google Drive

**Decision:** All image and video assets for production are stored in Google Drive under the `visionitechpos@gmail.com` account, in a folder structure mirroring the repo (`Sara Travel Stories - Media/references/...`, `Sara Travel Stories - Media/episodes/...`). The git repository holds only text and documentation — no image or video binaries going forward.

**Reason:** Anticipated storage risk as episode count grows, primarily from video (Veo clips, assembled episodes can reach hundreds of MB to GBs; git does not handle repeated large binary versions efficiently). Rather than split images and video across two systems, both are kept in one place to avoid the risk of losing track of assets.

**How to apply:** New reference/production images and videos are uploaded directly to the matching Drive folder (create the folder if it doesn't exist yet, mirroring the repo path). Episode `PRODUCTION_NOTES.md` files link to the Drive files/folders instead of local repo paths. The existing images already committed to `references/jeddah/obhur/` in git predate this decision — see note below on whether they remain.

---

### 2026-07-01 — Documentation Sync: Sara's Age Locked at 26

**Decision:** Sara's age is 26, per a decision made prior to this session. This entry is a documentation synchronization, not a new production decision — the age itself was not reopened or renegotiated.

**Reason:** `SARA_CHARACTER_BIBLE.md` still listed age as "Pending Approval," and `prompts/character/sara_base_prompt.md` referenced "late 20s" as an unapproved placeholder. Both were out of sync with the already-decided value. Reviewed for conflicts across `docs/` and `prompts/` — no other file asserts a specific canonical age for Sara (two illustrative examples in `docs/veo/PROMPT_ENGINEERING.md` reference "a woman in her twenties" generically as prompt-writing technique, not as Sara's locked description — left unchanged).

**Files synced:**
- `docs/SARA_CHARACTER_BIBLE.md` — Age: Pending Approval → 26
- `prompts/character/sara_base_prompt.md` — "late 20s" → 26

**Still pending:** Sara's other physical features (hair, eyes, face) remain unapproved placeholders per the existing warning in `sara_base_prompt.md`, until reference images are generated and approved.

---

### 2026-07-01 — ep001_fish-sculpture-obhur Script Approved

**Decision:** The script for `ep001_fish-sculpture-obhur` (developed from the PILOT_001 candidate) is approved final, following the full `CLAUDE.md` workflow through Step 4.5: Story Development → Documentation Load → Research (Stages 1-4) → Script → AI dialect/structure review → one human review pass.

**Reason:** This is the first episode to complete the entire production workflow end to end, including the newly adopted principles from this session: "The Story Comes First," the no-institutional-criticism behavioral rule, the restructured five-layer Language Bible, and the Character Cognition Engine conceptual architecture (used as a mental model during writing, not as an execution pipeline).

**Files:** `episodes/ep001_fish-sculpture-obhur/CONCEPT.md`, `episodes/ep001_fish-sculpture-obhur/SCRIPT.md`.

**Note:** The Claude → AI review → human review approval sequence is being treated as an unproven Production Experiment, not a documented production rule. It will be considered for formal documentation only after it proves itself across several episodes.

---

### 2026-07-01 — Architecture Freeze Through First 10 Episodes

**Decision:** The Character Cognition Engine architecture (`docs/NORTH_STAR.md` D-09) is frozen. No new architectural layers, files, or pipeline changes until 10 episodes are produced — unless production proves a specific, real problem that requires a change.

**Reason:** The conceptual architecture work during PILOT_001 (Sara Dialogue Engine → Character Cognition Engine redesign, SARA_EXPRESSIONS.md) is complete for now. The project's own principle — "architecture evolves only when production experiments prove it must" (D-08) — was at risk of being violated by continued theoretical refinement before any real production had occurred. The next phase must prove the system works, not keep improving it on paper.

**How to apply:** Any new architectural idea during the next 10 episodes is recorded in `docs/NORTH_STAR.md` under Future Vision, not implemented. Only a demonstrated production failure justifies revisiting this freeze.

---

### 2026-06-21 — Project Bootstrap

**Decision:** Established initial project structure and documentation framework.

**Reason:** Repository was created with empty documentation files. All Bible documents, folder structure, and templates have been created as first drafts based on README.md as the primary authority.

**Files created:**
- `docs/SARA_CHARACTER_BIBLE.md`
- `docs/SARA_VOICE_BIBLE.md`
- `docs/SARA_LANGUAGE_BIBLE.md`
- `docs/SARA_ENVIRONMENT_BIBLE.md`
- `docs/SARA_PRODUCTION_RULES.md`
- `docs/SARA_SOCIAL_MEDIA_BIBLE.md`
- `episodes/README.md`
- `episodes/_TEMPLATE/` (episode template)
- `prompts/` (full prompt library structure)
- `assets/` (assets folder structure)
- `references/` (converted from empty file to folder with subfolders)

**Status:** First drafts. All documents require review and approval before being considered final.

---

<!-- Add new entries above this line, newest first -->
