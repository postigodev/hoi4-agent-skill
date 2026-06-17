# Expected Behavior Evals

Use these checks to judge whether an agent using `hoi4-modding` behaves better than a generic coding agent. These are lightweight assertions, not a benchmark harness.

## File Inspection

Expected:

- inspects existing mod files before editing
- identifies descriptor files and mod root structure
- searches nearby files for country tags, prefixes, namespaces, and localization conventions
- reads relevant references or examples only when needed

Failure signals:

- creates arbitrary new files without checking the current mod
- invents prefixes or namespaces without searching
- rewrites unrelated files before understanding structure

## HOI4 Script Safety

Expected:

- preserves existing IDs unless there is a confirmed reason to rename them
- keeps event namespace and event ID prefixes consistent
- distinguishes triggers from effects
- checks scopes before adding state, country, character, or unit effects
- keeps focus prerequisites and `relative_position_id` references valid

Failure signals:

- places effects inside trigger-only blocks
- changes focus/event/idea IDs casually
- fixes caller syntax without checking whether the referenced event exists
- uses normal programming abstractions instead of Paradox script patterns

## Localization

Expected:

- adds localization for visible focus, event, decision, idea, and GUI text
- matches localization keys exactly to script references
- preserves language folder, file naming, encoding, and line-ending conventions

Failure signals:

- leaves raw keys visible to players
- puts final player-facing text inline where localization keys are expected
- edits vanilla localization files instead of mod files

## GFX And Assets

Expected:

- checks `.gfx` sprite definitions and image paths before referencing custom icons
- marks missing assets as placeholders instead of claiming they exist
- avoids copying vanilla HOI4, DLC, or Paradox assets into the repo

Failure signals:

- adds `GFX_*` references without checking definitions
- claims icons are fixed without verifying sprite/file presence
- vendors copied proprietary artwork or game files

## Debugging

Expected:

- asks for or reads the relevant `error.log`
- fixes parse and syntax errors before gameplay logic
- isolates errors related to the current mod or requested change
- uses broken-case examples as patterns without pasting them blindly
- avoids fixing unrelated warnings unless they block the requested feature

Failure signals:

- guesses from symptoms only
- starts with broad rewrites
- treats every `error.log` warning as in scope
- skips namespace, localization, or brace checks for known failure modes

## Validation Honesty

Expected:

- says when validation is static-only
- says when HOI4 was not launched
- reports manual HOI4 test steps
- distinguishes checked references from in-game validation

Failure signals:

- claims the mod loads without launching HOI4
- says something was tested in-game when only files were edited
- hides unresolved risks or unverified references

## Response Quality

Expected:

- reports files changed
- reports IDs added or modified
- reports localization keys added
- reports what to test in HOI4
- reports likely risks and compatibility concerns

Failure signals:

- buries load-breaking findings under style feedback
- omits changed IDs or localization keys
- fails to mention overwrite or `replace_path` compatibility risks
