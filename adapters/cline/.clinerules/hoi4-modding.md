---
paths:
  - "**/*.txt"
  - "**/*.gui"
  - "**/*.gfx"
  - "**/*.asset"
  - "**/*.yml"
  - "**/*.mod"
---

# HOI4 Modding

These rules are derived from HOI4 Agent Skill. If `skill/hoi4-modding/` exists in this workspace, treat it as canonical. Otherwise, follow this adapter.

Use these rules when creating, editing, reviewing, or debugging Hearts of Iron IV mods.

- Treat HOI4 mods as Paradox data-script projects.
- Inspect the mod root and descriptor files before editing.
- Infer existing prefixes, tags, event namespaces, idea prefixes, and localization conventions.
- Make small loadable edits.
- Add localization for visible player-facing text.
- Match event IDs to declared namespaces.
- Check valid scopes before adding triggers or effects.
- Verify focus prerequisites, event calls, idea references, and GFX references.
- Read `error.log` before guessing during debugging.
- Fix parse errors before logic errors.
- Do not edit vanilla installation files directly.
- Do not copy proprietary HOI4 or DLC assets into the repository.
- Do not claim in-game validation unless HOI4 was actually launched and tested.
