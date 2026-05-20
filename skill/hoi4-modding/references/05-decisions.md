# Decisions

Decisions usually live under:

```txt
common/decisions/
```

Decision files define categories and decisions. Category visibility and individual decision visibility are separate concerns.

## Agent Workflow

Before editing:

1. Identify the relevant decision category.
2. Check whether the mod already has a country or feature prefix.
3. Distinguish category `allowed` logic from decision `visible` and `available` logic.
4. Check referenced events, ideas, flags, variables, and scripted effects.
5. Add localization for the category, decision name, and decision description.

## Common Fields

Common decision fields include:

```txt
allowed = { ... }
visible = { ... }
available = { ... }
cost = 50
days_remove = 30
complete_effect = { ... }
remove_effect = { ... }
cancel_effect = { ... }
ai_will_do = { factor = 1 }
```

Use nearby examples for exact structure and project style.

## Validation

Before finishing, verify:

- category IDs are unique
- decision IDs are unique within the relevant files
- event IDs fired by decisions exist
- ideas added or removed by decisions exist
- visible text has localization
- effects are valid in the decision's country scope
- `allowed`, `visible`, and `available` do not accidentally hide the decision forever

## Common Failure Pattern

If the category appears but the decision does not, inspect the individual decision's `visible`, `available`, flags, and country scope before changing the category.
