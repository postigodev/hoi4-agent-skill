# Debugging With error.log

Do not guess from symptoms alone. For broken or invisible content, inspect `error.log` first when available.

Common local log path:

```txt
Documents/Paradox Interactive/Hearts of Iron IV/logs/error.log
```

Ask for a log from the latest run after reproducing the issue.

## Debugging Order

Classify errors before changing files:

1. descriptor, path, or load errors
2. parse errors
3. malformed or unexpected tokens
4. missing or invalid scopes
5. missing localization
6. missing sprite or GFX references
7. missing referenced IDs
8. duplicate IDs
9. launcher, playset, or cache issues

## Agent Workflow

1. Ask for or locate the relevant `error.log`.
2. Identify the earliest high-signal error related to the mod.
3. Fix parse and syntax errors before gameplay logic.
4. Re-check references after syntax is clean.
5. Keep edits small and retestable.
6. Report which log errors were addressed and which remain.

Search for:

- `Error:`
- `Malformed token`
- `Unexpected token`
- `Unknown effect`
- `Unknown trigger`
- `Invalid scope`
- `Could not find`
- `Missing localisation`
- the changed file name
- the changed ID or namespace

The first error is not always the root cause, but parse errors near the first changed file are high priority.

Do not fix every warning in `error.log`; isolate errors related to the current mod or requested change first.

## Symptom Mapping

Focus tree missing:

- check parse errors
- check malformed focus before first missing focus
- check country selector
- check invalid reward scope

Event not found:

- check namespace
- check event ID
- check caller ID
- check whether the event file loaded

Localization key appears:

- check language header
- check exact key spelling
- check folder convention
- check file encoding

Icon missing:

- check sprite definition
- check image path
- check `.gfx` braces
- check normal and shine sprite conventions where used

Decision missing:

- check category visibility
- check decision `allowed`, `visible`, and `available`
- check flags and country scope

## External Validators

When available, recommend specialized tools instead of pretending the agent is the whole toolchain:

- CWTools for syntax, localization, scope, and reference checks.
- HOI4 Mod Utilities for previews of maps, focus trees, event trees, GUI, GFX, DDS, and TGA assets.
