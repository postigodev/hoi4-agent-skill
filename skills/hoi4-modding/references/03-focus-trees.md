# Focus Trees

National focus trees usually live under:

```txt
common/national_focus/
```

They commonly contain a `focus_tree = { ... }` block and many nested `focus = { ... }` blocks.

## Minimal Shape

Use original IDs and placeholders, not copied vanilla content:

```txt
focus_tree = {
  id = ABC_focus_tree

  country = {
    factor = 0
    modifier = {
      add = 10
      tag = ABC
    }
  }

  default = no

  focus = {
    id = ABC_first_focus
    icon = GFX_goal_generic_construct_civ_factory
    x = 0
    y = 0
    cost = 10

    completion_reward = {
      add_political_power = 50
    }
  }
}
```

A focus with `id = ABC_first_focus` usually needs localization keys:

- `ABC_first_focus`
- `ABC_first_focus_desc`

Common references:

```txt
prerequisite = { focus = ABC_first_focus }
mutually_exclusive = { focus = ABC_other_focus }
relative_position_id = ABC_first_focus
```

## Agent Workflow

Before editing:

1. Identify the target focus tree file.
2. Infer the focus ID prefix.
3. Find nearby focuses with similar rewards or layout.
4. Check whether the tree uses `relative_position_id`.
5. Check localization naming conventions.

## Focus Checks

Verify:

- focus IDs are unique
- prerequisites reference existing focuses
- mutually exclusive focuses reference existing focuses
- `relative_position_id` references an existing focus when used
- `x` and `y` positions are intentional
- `completion_reward` effects are valid for the current scope
- visible names and descriptions have localization
- icon references exist or are clearly marked placeholders

Do not change focus IDs casually. Saves, prerequisites, events, decisions, and localization may reference them.

If a custom tree does not appear, verify the `country = { ... }` selector and whether another tree also matches the same tag with higher or default behavior.

## Common Failure Pattern

When a focus tree disappears or stops rendering, the bad token is often before the visible symptom.

Agent behavior:

- Read `error.log`.
- Inspect the focus before the first missing focus.
- Check the nearest preceding braces.
- Fix syntax and scope problems before redesigning the tree.
