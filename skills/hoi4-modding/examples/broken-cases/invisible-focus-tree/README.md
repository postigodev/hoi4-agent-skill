# Broken Case: Invisible Focus Tree

This case demonstrates a focus tree that does not appear because a malformed focus block breaks parsing.

## Failure

The mod is enabled, but the expected focus tree or a focus branch is missing.

## Broken Snippet

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

  focus = {
    id = ABC_start_reform
    icon = GFX_goal_ABC_reform
    x = 0
    y = 0
    cost = 10

    completion_reward = {
      add_political_power = 50
    }

  focus = {
    id = ABC_industrial_committee
    prerequisite = { focus = ABC_start_reform }
    relative_position_id = ABC_start_reform
    x = 0
    y = 1
    cost = 10
  }
}
```

The first focus is missing its closing brace before the second `focus = { ... }` starts.

## Fixed Snippet

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

  focus = {
    id = ABC_start_reform
    icon = GFX_goal_ABC_reform
    x = 0
    y = 0
    cost = 10

    completion_reward = {
      add_political_power = 50
    }
  }

  focus = {
    id = ABC_industrial_committee
    prerequisite = { focus = ABC_start_reform }
    relative_position_id = ABC_start_reform
    x = 0
    y = 1
    cost = 10
  }
}
```

## What An Agent Should Inspect

- `error.log` before guessing.
- The first focus or branch that disappears.
- The nearest preceding braces and malformed tokens.
- The `country = { ... }` selector.
- `relative_position_id` and prerequisite references only after syntax is clean.

## Possible error.log Symptoms

```txt
Unexpected token: focus
Malformed token near common/national_focus/ABC_focus_tree.txt
Error while parsing focus tree ABC_focus_tree
```

Exact wording varies, and the root cause may be a few lines before the reported token.

## What Not To Overfix

- Do not redesign the focus tree.
- Do not change focus IDs unless there is a confirmed ID issue.
- Do not fix unrelated warnings before the parse error.
- Do not claim the tree appears in-game unless HOI4 was actually launched and checked.
