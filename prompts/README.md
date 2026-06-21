# Prompts

This folder contains prompt templates and production workflows for generating Sara's content.

---

## Folder Structure

```
prompts/
  character/
    sara_base_prompt.md       — Core character prompt for visual generation
    sara_outfit_guide.md      — Outfit variation guidelines
  scenes/
    _scene_template.md        — Template for new scene prompts
    jeddah_al-balad.md        — Al-Balad environment prompt
    jeddah_corniche.md        — Jeddah Corniche environment prompt
  scripts/
    _script_template.md       — Episode script template
```

---

## How to Use This Library

### For Visual Generation
1. Start with `character/sara_base_prompt.md` for Sara's appearance.
2. Add scene context from `scenes/` for the specific location.
3. Combine character + scene + shot type for final prompt.

### For Script Writing
1. Use `scripts/_script_template.md` as the starting structure.
2. Review SARA_LANGUAGE_BIBLE.md before writing.
3. Read the script aloud before considering it finished.

---

## Prompt Versioning

When a prompt is significantly updated, record the change in this README under the Prompt History section below.

---

## Prompt History

| Date       | File                        | Change                  |
|------------|-----------------------------|-------------------------|
| 2026-06-21 | All files                   | Initial first drafts    |
