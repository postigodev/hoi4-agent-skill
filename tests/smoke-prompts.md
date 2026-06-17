# Smoke Prompts

These prompts are quick manual checks for the skill.

## Core Failure Modes

Use these as the primary v0.2 behavior checks.

### Event Namespace Mismatch

```txt
My decision calls abc_reform.1, but HOI4 says there is no event with that ID. Inspect the event file and caller, then make the smallest fix.
```

Pass criteria:

- checks `add_namespace`
- checks event block `id`
- checks the decision/focus caller
- avoids renaming unrelated events

### Missing Localization

```txt
ABC_start_reform and ABC_start_reform_desc show as raw keys in-game. Fix the localization without changing focus IDs.
```

Pass criteria:

- compares script IDs to localization keys
- preserves the existing localization file convention
- adds missing keys only
- does not inline player-facing text in script

### Invisible Focus Tree

```txt
After adding a second focus, the ABC focus branch disappeared. Read the relevant error.log excerpt and inspect the focus before the first missing one.
```

Pass criteria:

- fixes parse/brace errors before layout logic
- checks the nearest preceding focus block
- preserves focus IDs
- reports manual HOI4 test steps

### Decision Fires Event

```txt
Add one ABC decision that costs political power and fires abc_reform.1. Check that the event exists before wiring the decision.
```

Pass criteria:

- distinguishes category `allowed` from decision `visible` and `available`
- checks event namespace and ID
- adds decision localization
- reports IDs added or modified

### Focus Adds National Spirit

```txt
Add a focus reward that gives ABC a new national spirit. Create the idea and localization if missing.
```

Pass criteria:

- checks `common/ideas/`
- uses a valid `add_ideas` reference
- adds idea name and description localization
- reports static-only validation unless HOI4 was launched

### Custom GFX Reference

```txt
My custom focus icon GFX_goal_ABC_reform shows as a question mark. Check the sprite definition and texture path without assuming the asset exists.
```

Pass criteria:

- inspects `.gfx` sprite definitions
- checks texture paths
- marks missing assets as placeholders
- does not copy or invent proprietary assets

### Validation Honesty

```txt
Review this small HOI4 mod change and tell me whether it is ready. You cannot launch HOI4 from this environment.
```

Pass criteria:

- does not claim in-game testing
- distinguishes static checks from game validation
- reports manual test steps
- names unresolved risks

## Focus Tree

```txt
Add two focuses after ABC_start. The first should grant political power, and the second should add a national spirit. Follow existing prefixes and add localization.
```

Pass criteria:

- checks existing focus tree
- adds unique focus IDs
- uses valid prerequisite references
- adds localization
- reports test steps

## Event Namespace

```txt
The console says there is no event with ID abc_story.4. Debug the event files and caller.
```

Pass criteria:

- checks `add_namespace`
- checks event IDs
- checks the caller
- checks whether file loads
- reads `error.log` if available

## Localization

```txt
Several focus names show raw keys in-game. Fix localization without changing the focus IDs.
```

Pass criteria:

- compares script keys to localization keys
- preserves language folder convention
- adds missing keys
- does not rename IDs unnecessarily

## GFX Reference

```txt
A custom focus icon shows as a question mark. Find the likely reference problem and fix it if the asset exists.
```

Pass criteria:

- checks `.gfx` sprite definitions
- checks referenced image paths
- does not assume missing assets exist
- reports placeholder or asset requirements

## Review

```txt
Review this HOI4 mod branch for load-breaking issues.
```

Pass criteria:

- leads with findings
- prioritizes syntax, descriptor, localization, namespace, scope, and reference issues
- includes file/line references where possible

## National Spirit

```txt
Add a focus reward that gives country ABC a new national spirit. Create the idea and localization if missing.
```

Pass criteria:

- checks `common/ideas/`
- creates or reuses a valid idea
- adds matching localization
- uses the correct `add_ideas` reference
- reports static-only validation unless HOI4 was launched

## Decision

```txt
Add a decision category for ABC with one decision that costs political power and fires an event.
```

Pass criteria:

- creates or edits `common/decisions/`
- uses valid category and decision structure
- checks the event ID exists
- adds localization
- distinguishes `allowed`, `visible`, and `available`
- reports what to test in-game

## Learn From Broken Examples

```txt
Use the skill's broken-case examples to debug a mod where abc_reform.1 will not fire, ABC_start_reform appears as a raw key, and a new focus branch disappeared. Inspect the relevant files and error.log first. Make only the smallest fixes and do not overfix unrelated warnings.
```

Pass criteria:

- consults `examples/broken-cases/` as educational patterns
- checks event namespace and caller before renaming IDs
- compares script keys to localization keys
- fixes parse errors before focus layout or reward logic
- ignores unrelated warnings unless they block the requested feature
- reports static-only validation unless HOI4 was launched
