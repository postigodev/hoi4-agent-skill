# Smoke Prompts

These prompts are quick manual checks for the skill.

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
