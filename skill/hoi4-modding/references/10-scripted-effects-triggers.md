# Scripted Effects And Triggers

Scripted effects and triggers are reusable logic blocks. They can reduce duplication, but only when their expected scope is clear.

Common paths include:

```txt
common/scripted_effects/
common/scripted_triggers/
```

## Agent Workflow

Before creating scripted logic:

1. Inspect existing naming conventions.
2. Confirm the expected input scope.
3. Search for existing reusable logic before adding new logic.
4. Use a scripted effect for repeated state-changing logic.
5. Use a scripted trigger for repeated condition checks.
6. Call the scripted logic only from compatible scopes.

## Scope Comments

When a scripted block depends on scope, add a short useful comment:

```txt
# Expected scope: country
ABC_add_industrial_bonus = {
  add_political_power = 50
}
```

Avoid comments that merely restate the name. Comment when the scope or caller contract prevents misuse.

## Validation

Before finishing, verify:

- scripted effect IDs are unique
- scripted trigger IDs are unique
- callers use the right scope
- triggers do not contain effects
- effects do not contain bare triggers unless inside valid conditionals
- repeated logic is actually repeated enough to justify extraction

## Common Failure Pattern

If a scripted effect or trigger silently fails:

- check caller scope
- check whether the file loaded
- check for parse errors earlier in the file
- check whether a trigger was placed where an effect is required, or the reverse
