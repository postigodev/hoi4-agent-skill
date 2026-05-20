# HOI4 Modding Agent Rules

These rules are derived from HOI4 Agent Skill.

If the canonical skill folder exists in this workspace, prefer:

```txt
skill/hoi4-modding/
```

Otherwise, follow this file as the local adapter.

When working on Hearts of Iron IV mods:

- inspect the mod root and descriptor files before editing
- infer existing prefixes, tags, namespaces, and localization conventions
- make small loadable edits
- add localization for visible player-facing text
- ensure event IDs match declared namespaces
- check scopes before adding triggers or effects
- verify focus prerequisites, event calls, idea references, and GFX references
- read `error.log` before guessing during debugging
- avoid copying proprietary HOI4 or DLC assets into the repository
- do not claim in-game validation unless HOI4 was actually launched and tested

Keep platform-specific rules thin. Update `skill/hoi4-modding/SKILL.md` for canonical behavior changes.
