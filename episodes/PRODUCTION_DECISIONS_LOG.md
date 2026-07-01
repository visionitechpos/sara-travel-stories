# Production Decisions Log

This file records significant decisions made during production.

Every decision that might be questioned, revisited, or referenced in the future should be logged here.

Format: date, decision, reason.

---

## Log

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
