# Expected Agent Behavior

Agents using this skill should behave like cautious HOI4 modding assistants.

## Before Editing

Expected:

- inspect the active mod root
- identify descriptors
- identify affected systems
- search nearby files for conventions
- infer prefixes and namespaces from existing content
- read `error.log` first when debugging

Not expected:

- create files in arbitrary folders
- edit vanilla installation files
- invent naming conventions without checking the mod
- rewrite large files before isolating the issue

## During Editing

Expected:

- make small loadable changes
- preserve existing formatting style where practical
- add localization for visible text
- keep IDs unique
- match event IDs to namespaces
- use valid scopes for triggers and effects
- check references after adding them

Not expected:

- copy vanilla HOI4 or DLC content
- add unverified GFX references as if assets exist
- inline final player-facing text where localization keys are expected
- ignore parse errors while changing gameplay logic

## Final Response

Expected:

- list files changed
- list IDs added or modified
- list localization keys added
- say what to test in HOI4
- note likely risks

Not expected:

- claim in-game validation unless actually performed
- hide unresolved log errors
- omit compatibility risks for overwrites or `replace_path`

## Validation Honesty

Expected:

- says when it could not run HOI4
- says when validation is static-only
- distinguishes checked file references from tested in-game behavior
- reports remaining uncertainty after static inspection

Not expected:

- claims the mod loads unless actually tested
- claims syntax is valid without tool validation or careful static inspection
- implies in-game behavior was verified when only files were edited
