# HOI4 Agent Skill

A portable agent skill for creating, editing, reviewing, and debugging Hearts of Iron IV mods with AI coding agents.

**AI-assisted HOI4 modding without AI slop.**

HOI4 Agent Skill turns AI coding agents from generic code writers into cautious Paradox-script modding assistants.

It helps agents work with:

- mod descriptors and folder structure
- national focus trees
- events and namespaces
- decisions
- ideas and national spirits
- countries, states, and history files
- localization
- GFX and interface references
- scripted effects and triggers
- `error.log` debugging

## Supported Agents

The canonical skill lives in:

```txt
skills/hoi4-modding/
```

The repository is designed to be portable across:

- Codex Skills
- Claude Skills
- Cursor Rules
- Cline Rules
- `AGENTS.md`-compatible agents

Platform adapters live under:

```txt
adapters/
```

Adapters are intentionally thin. The canonical behavior belongs in `skills/hoi4-modding/SKILL.md`.

## Why This Exists

HOI4 modding failures often come from brittle project structure rather than ordinary programming mistakes:

- wrong descriptor path
- wrong event namespace
- wrong trigger or effect scope
- wrong localization key
- wrong sprite reference
- wrong folder or file name
- missing braces or malformed Paradox script
- guessing from symptoms instead of reading `error.log`

This skill encodes those failure modes into reusable agent behavior.

It is not a replacement for learning HOI4 modding. It is a guardrail for agents: inspect structure, preserve IDs, add localization, respect namespaces and scopes, check GFX references, and debug through `error.log` instead of guessing.

## Install

Use the `skills/hoi4-modding/` directory with your agent platform.

### Install With Codex

```txt
$skill-installer install https://github.com/postigodev/hoi4-agent-skill/tree/main/skills/hoi4-modding
```

Restart Codex after installing.

### Use With Claude

Upload or install the `skills/hoi4-modding/` folder as a Claude Skill.

### Use With Cursor

Copy:

```txt
adapters/cursor/.cursor/rules/hoi4-modding.mdc
```

into your mod repository at:

```txt
.cursor/rules/hoi4-modding.mdc
```

Optionally copy `adapters/cursor/AGENTS.md` to the root of your mod repository.

### Use With Cline

Copy:

```txt
adapters/cline/.clinerules/hoi4-modding.md
```

into your mod repository at:

```txt
.clinerules/hoi4-modding.md
```

Optionally copy `adapters/cline/AGENTS.md` to the root of your mod repository.

## What To Try First

Open a real HOI4 mod repository with the skill installed, then start with:

```txt
Inspect this HOI4 mod before editing. Identify the descriptor, folder structure, country tags, event namespaces, localization conventions, and any obvious load risks. Do not change files yet. Summarize what you found and what you would check in error.log.
```

After the agent reports the structure, ask for a small scoped change, such as:

```txt
Add one small ABC focus that grants political power. Follow existing focus ID and localization conventions, keep the edit minimal, and report what I should test in HOI4.
```

## Examples

Original minimal snippets live in:

```txt
skills/hoi4-modding/examples/
```

They cover a tiny focus tree, event, decision, idea, localization file, and GFX declaration using the placeholder tag `ABC`.

Debugging mini-labs live in:

```txt
skills/hoi4-modding/examples/broken-cases/
```

Use them to teach agents the difference between namespace mismatches, missing localization, and parse errors that make focus trees disappear.

## Coverage

| Area | Status |
|---|---|
| Folder structure and descriptors | Covered |
| Paradox script basics | Covered |
| Focus trees | Covered |
| Events | Covered |
| Decisions | Covered |
| Ideas and national spirits | Covered |
| Countries, history, and states | Covered |
| Localization | Covered |
| GFX, interface, and icons | Covered |
| Scripted effects and triggers | Covered |
| `error.log` debugging | Covered |

## Asset And Legal Posture

This repository does not include copied vanilla HOI4 files, DLC files, Paradox artwork, icons, music, localization, or other proprietary game assets.

When using the skill, agents should avoid copying proprietary game files or assets into public repositories. Prefer original content, placeholders, or references to assets that already exist in the user's local mod workspace.

## Project Status

Current target: `0.2.0`

The current version is instruction-only. It includes the canonical skill, concise references, examples, thin adapters, and smoke prompts. It intentionally does not include scripts, binaries, dependency installs, or copied game content.
