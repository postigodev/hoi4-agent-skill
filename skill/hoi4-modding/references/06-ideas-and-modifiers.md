# Ideas And National Spirits

Ideas and national spirits usually live under:

```txt
common/ideas/
```

Focuses, events, and decisions often add or remove ideas through effects such as `add_ideas` and `remove_ideas`.

## Agent Workflow

Before adding `add_ideas = ABC_spirit`, verify:

1. The idea exists or should be created.
2. The idea belongs in the correct idea group for the mod's pattern.
3. The idea ID follows the local prefix convention.
4. Modifiers are valid for HOI4.
5. Localization exists for the idea name and description.
6. Removal or replacement logic exists if the spirit is temporary.

## Minimal Shape

Use original IDs and text:

```txt
ideas = {
  country = {
    ABC_industrial_push = {
      picture = generic_production_bonus
      allowed = {
        original_tag = ABC
      }
      modifier = {
        production_speed_buildings_factor = 0.05
      }
    }
  }
}
```

Use nearby project examples for picture names, idea groups, and modifier style.

## Validation

Before finishing, verify:

- the idea ID is unique
- all references use the exact idea ID
- modifiers are spelled correctly
- the current scope can add or remove the idea
- localization includes both name and description
- the idea file parses cleanly

## Common Failure Pattern

If a national spirit does not appear:

- check that the idea file loaded
- check that the idea group is correct
- check `add_ideas` spelling
- check focus/event/decision reward scope
- check missing localization
