---
title: HOI4 Agent Skill Design
date: 2026-05-20
status: historical-design-note
---

# HOI4 Agent Skill Design

## Purpose

HOI4 Agent Skill is a portable instruction package for AI coding agents working on Hearts of Iron IV mods. Its job is not to become a full HOI4 tutorial or clone community wikis. Its job is to make agents behave cautiously and effectively inside HOI4's brittle Paradox-script modding environment.

The skill should help agents avoid common modding failures:

- broken descriptor paths
- invalid folder structure
- mismatched event namespaces and IDs
- missing localization
- malformed Paradox script
- invalid trigger/effect scopes
- duplicate IDs
- broken GFX or sprite references
- focus tree layout/reference mistakes
- guessing from symptoms instead of reading `error.log`
- copying proprietary HOI4 or DLC assets into public repositories

## Product Positioning

Primary framing:

> HOI4 Agent Skill turns AI coding agents from generic code writers into cautious Paradox-script modding assistants.

Secondary framing:

> HOI4 modding fails less from not knowing how to code and more from brittle structure: wrong folder, wrong namespace, wrong scope, wrong localization key, wrong sprite reference, wrong descriptor path. This skill encodes those material failure modes into reusable agent behavior.

## Audience

The repository should be useful for people who use AI agents with HOI4 mods through:

- Codex Skills
- Claude Skills
- Cursor Rules
- Cline Rules
- `AGENTS.md`-compatible agents

The project should be fully neutral. No platform-specific adapter should become the canonical version.

## Architecture

The canonical source of truth is:

```txt
skill/hoi4-modding/SKILL.md
```

Supporting references live beside it:

```txt
skill/hoi4-modding/references/
```

Adapters are thin distribution targets:

```txt
adapters/
  codex/
  claude/
  cursor/
  cline/
```

Adapters may explain installation steps or provide compact rule files, but they must not fork the full skill content. When in doubt, adapters should point back to `skill/hoi4-modding/SKILL.md`.

## MVP Repository Structure

Version `0.1.0` should ship:

```txt
hoi4-agent-skill/
  README.md
  LICENSE
  SECURITY.md
  CONTRIBUTING.md

  skill/
    hoi4-modding/
      SKILL.md
      LICENSE.txt
      references/
        01-folder-structure.md
        02-paradox-script.md
        03-focus-trees.md
        04-events.md
        05-decisions.md
        06-ideas-and-modifiers.md
        07-countries-history-states.md
        08-localization.md
        09-gfx-interface-icons.md
        10-scripted-effects-triggers.md
        11-debugging-error-log.md
        13-common-failure-modes.md

  adapters/
    codex/
      README.md
    claude/
      README.md
    cursor/
      AGENTS.md
      .cursor/
        rules/
          hoi4-modding.mdc
    cline/
      AGENTS.md
      .clinerules/
        hoi4-modding.md

  prompts/
    debug-error-log.md
    create-focus-branch.md
    add-event-chain.md
    review-mod-pr.md

  tests/
    expected-agent-behavior.md
    smoke-prompts.md
```

## Core Skill Behavior

The skill should instruct agents to treat HOI4 mods as Paradox data-script projects, not normal software projects.

Agents should prioritize:

- small loadable edits
- existing project conventions
- valid mod folder structure
- unique IDs
- correct event namespaces
- correct scopes
- localization for all visible player-facing content
- error-log-driven debugging
- compatibility with the current mod's structure

Agents should avoid:

- large speculative rewrites
- inventing syntax when nearby mod or vanilla-style patterns exist
- editing vanilla installation files directly
- copying proprietary game files or assets
- adding GFX references without checking sprite/file existence
- adding visible UI content without localization keys

## First-Actions Workflow

Before editing, agents should:

1. Inspect the active mod root.
2. Identify the descriptor file and mod folder.
3. Identify country tag, file prefix, event namespace, idea prefix, and localization prefix where relevant.
4. Search nearby files for existing conventions.
5. Determine which systems are affected: focuses, events, decisions, ideas, history, localization, GFX, scripted effects, scripted triggers, map/state data, or descriptor files.
6. If debugging, inspect `error.log` before guessing.

## Reference Loading Policy

The `SKILL.md` should stay concise. Detailed material belongs in references and should be loaded only when relevant.

Reference file responsibilities:

- `01-folder-structure.md`: mod layout, descriptor files, load order, overwrite behavior, `replace_path`, and avoiding vanilla edits.
- `02-paradox-script.md`: key-value syntax, blocks, braces, comments, booleans, triggers/effects, and scopes such as `ROOT`, `FROM`, `PREV`, and `THIS`.
- `03-focus-trees.md`: `focus_tree` structure, focus IDs, prerequisites, relative positions, rewards, icons, and common invisibility issues.
- `04-events.md`: `add_namespace`, event IDs, externally fired events, options, localization keys, and event callers.
- `05-decisions.md`: decision categories, category visibility, decision visibility, availability, costs, event calls, and effects.
- `06-ideas-and-modifiers.md`: ideas, national spirits, modifiers, `add_ideas`, removal logic, and localization.
- `07-countries-history-states.md`: country tags, country definitions, history files, states, ownership, cores, and compatibility risks.
- `08-localization.md`: localization folder/file conventions, `l_english:`, keys, descriptions, dynamic localization, color codes, and encoding cautions.
- `09-gfx-interface-icons.md`: sprite definitions, focus icons, `.gfx` files, image paths, shine conventions, and asset checks.
- `10-scripted-effects-triggers.md`: reusable scripted logic, expected scopes, scripted triggers versus scripted effects, and caller contracts.
- `11-debugging-error-log.md`: log-first debugging workflow and error classification.
- `13-common-failure-modes.md`: recurring practical failures and required agent behavior.

## Adapter Policy

### Codex

`adapters/codex/README.md` should describe installation through a GitHub directory URL:

```txt
skill/hoi4-modding/
```

It should avoid Codex-only language in the canonical skill.

### Claude

`adapters/claude/README.md` should explain that `skill/hoi4-modding/` is a Claude-compatible skill folder because it contains a `SKILL.md` file with YAML frontmatter.

### Cursor

Cursor should receive:

```txt
adapters/cursor/AGENTS.md
adapters/cursor/.cursor/rules/hoi4-modding.mdc
```

These should be compact pointers to the canonical skill behavior, not a full duplicated manual.

### Cline

Cline should receive:

```txt
adapters/cline/AGENTS.md
adapters/cline/.clinerules/hoi4-modding.md
```

These should mirror the same compact behavior policy as Cursor.

## Security And Trust

The MVP should be instruction-only.

It should not:

- execute shell commands automatically
- download external files automatically
- modify files outside the active mod repository
- copy proprietary HOI4 or DLC assets into this repository
- ask agents to ignore user, system, or platform safety instructions
- include binaries
- require dependency installation

`SECURITY.md` should make this explicit.

## Examples And Scripts

Examples are deferred to `0.2.0`.

Potential examples:

- minimal mod descriptor
- minimal focus tree
- minimal event
- minimal decision
- minimal idea
- minimal localization file
- minimal `.gfx` focus icon declaration

Scripts are deferred until at least `0.4.0`, and only if repeated manual validation pain justifies them.

Potential scripts:

- brace-balance checker
- localization-key scanner
- event-namespace scanner
- focus-ID duplicate scanner

Scripts should not be part of the MVP.

## Acceptance Criteria For 0.1.0

The MVP is ready when:

- `skill/hoi4-modding/SKILL.md` has platform-neutral frontmatter and concise operating instructions.
- The core references exist and cover the main failure modes.
- The README clearly explains value, supported agents, install paths, and asset/legal posture.
- Adapter files exist and are thin.
- No proprietary HOI4 files, DLC files, images, or copied assets are included.
- No scripts or dependency install steps are required.
- Smoke prompts exist for focus trees, event chains, localization, `error.log`, and PR review behavior.

## Implementation Order

1. Add root project files: `README.md`, `LICENSE`, `SECURITY.md`, `CONTRIBUTING.md`.
2. Add `skill/hoi4-modding/SKILL.md`.
3. Add core references.
4. Add adapter READMEs and compact rule files.
5. Add smoke prompts and expected behavior tests.
6. Review for duplication and platform-specific leakage.
7. Verify the repo contains no proprietary HOI4 content.
