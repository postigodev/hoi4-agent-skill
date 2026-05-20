---
name: hoi4-modding
description: Creates, edits, reviews, and debugs Hearts of Iron IV mods. Use for HOI4 focus trees, events, decisions, ideas, countries, states, history files, localization, GFX/interface references, scripted effects/triggers, descriptors, mod folder structure, and error.log issues.
license: MIT
metadata:
  domain: hearts-of-iron-iv-modding
  compatibility:
    - codex
    - claude
    - cursor
    - cline
    - agents-md
---

# HOI4 Modding Agent Skill

Use this skill when working on Hearts of Iron IV mods.

## Operating Model

Treat HOI4 mods as Paradox data-script projects, not normal software projects.

Prioritize:

- small loadable edits
- existing project conventions
- valid folder structure
- unique IDs
- correct event namespaces
- correct scopes
- localization for all visible player-facing content
- `error.log`-driven debugging
- compatibility with the current mod structure

Avoid:

- large speculative rewrites
- inventing syntax when a nearby project or vanilla-style pattern exists
- editing vanilla installation files directly
- copying proprietary game files or assets into public repositories
- adding GFX references without checking whether sprites/files exist
- adding visible UI content without localization keys

## First Actions

Before editing:

1. Inspect the active mod root.
2. Identify the descriptor file and mod folder.
3. Identify relevant country tags, file prefixes, event namespaces, idea prefixes, and localization prefixes.
4. Search nearby files for existing conventions.
5. Determine whether the requested change affects focus trees, events, decisions, ideas, history, localization, GFX, scripted effects, scripted triggers, map/state data, or descriptor files.
6. If debugging, inspect `error.log` before guessing from symptoms.

## Reference Loading

Read the relevant reference files only when needed:

- `references/01-folder-structure.md` for mod layout and descriptor issues.
- `references/02-paradox-script.md` for Paradox script syntax, braces, scopes, triggers, and effects.
- `references/03-focus-trees.md` for national focus trees.
- `references/04-events.md` for event namespaces, event IDs, options, and event firing.
- `references/05-decisions.md` for decision categories, visibility, availability, costs, and effects.
- `references/06-ideas-and-modifiers.md` for ideas, national spirits, modifiers, and `add_ideas`.
- `references/07-countries-history-states.md` for country setup, history files, states, and related references.
- `references/08-localization.md` for localization files, keys, formatting, and visible text.
- `references/09-gfx-interface-icons.md` for sprites, focus icons, `.gfx`, `.dds`, `.tga`, and interface references.
- `references/10-scripted-effects-triggers.md` for reusable scripted logic and expected scopes.
- `references/11-debugging-error-log.md` for debugging workflows.
- `references/13-common-failure-modes.md` for known HOI4 modding mistakes.

## Editing Checklist

Before finishing, verify:

- IDs are unique in the affected files.
- Event IDs match declared namespaces.
- Visible focus, event, decision, idea, and GUI text has localization.
- Localization keys match script references.
- Braces are balanced.
- Effects and triggers are used in valid scopes.
- Focus prerequisites reference existing focuses.
- Event calls reference existing events.
- Idea additions reference existing ideas.
- GFX references point to existing sprites/files or clearly marked placeholders.
- The change does not silently overwrite vanilla files unless intended.
- The change avoids bundling proprietary game assets.
- Do not claim in-game validation unless HOI4 was actually launched and tested.

## Debugging Workflow

When a mod does not load or content does not appear:

1. Check whether the mod is enabled in the active playset.
2. Check descriptor and path issues.
3. Read `error.log`.
4. Fix parse and syntax errors first.
5. Fix missing or invalid scope errors.
6. Fix missing localization.
7. Fix missing sprite or GFX references.
8. If HOI4 can be launched, test the smallest affected feature in-game. Otherwise, report this as a manual test step for the user.
9. Summarize remaining risks.

If `error.log` is unavailable, ask the user for the relevant excerpt or explain what to inspect manually.

## Response Format

When done, report:

- files changed
- IDs added or modified
- localization keys added
- what to test in HOI4
- likely risks
- whether validation was static-only or actually tested in-game
