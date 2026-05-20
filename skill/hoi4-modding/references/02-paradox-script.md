# Paradox Script

HOI4 script is data-oriented Paradox script. Treat it as its own configuration language, not as Python, JavaScript, JSON, or YAML.

## Basic Syntax

Common patterns:

```txt
key = value
block = {
  key = value
}
# comment
```

Booleans are usually:

```txt
yes
no
```

Common values include numbers, decimals, strings, `yes`/`no` booleans, IDs, and blocks.

## Blocks And Braces

Most serious failures come from malformed blocks:

- missing `{`
- missing `}`
- unexpected token
- invalid nesting
- assigning a block where a scalar is expected
- assigning a scalar where a block is expected

Agent behavior:

- Preserve local indentation style.
- Check the block before the first broken or invisible feature.
- Fix parse errors before logic errors.
- Avoid large rewrites when one malformed block is the likely cause.

## Scopes

Effects and triggers run in scopes. Common scope names include:

- `ROOT`
- `FROM`
- `PREV`
- `THIS`

Common practical scopes include country, state, character, unit leader, and strategic region contexts.

Agent behavior:

- Identify the current scope before adding triggers or effects.
- Check nearby working examples in the same file or system.
- Do not move state effects into country scope unless wrapped in the right state selection.
- When an effect complains about scope, fix the scope chain rather than renaming IDs.

## Conditional Blocks

Common forms:

```txt
if = {
  limit = {
    tag = ABC
  }
  add_political_power = 50
}

else_if = {
  limit = {
    tag = DEF
  }
  add_stability = 0.05
}

else = {
  add_war_support = 0.05
}
```

Use nearby project style for `hidden_effect`, `custom_effect_tooltip`, flags, variables, and scripted effects.

## Triggers Versus Effects

Triggers check conditions. Effects change game state.

Do not place effects inside trigger-only blocks such as:

- `allowed`
- `visible`
- `available`
- `trigger`
- `limit`

Do not place triggers directly inside effect-only blocks such as `completion_reward` unless they are inside a valid conditional wrapper:

```txt
if = {
  limit = {
    tag = ABC
  }
  add_political_power = 50
}
```

Do not invent comparison syntax. Use nearby working examples for `has_*`, `is_*`, `owns_state`, `controls_state`, variables, and modifiers.

## Validation Habits

Before finishing:

- Check braces.
- Check scopes.
- Check referenced IDs.
- Check localization keys for visible content.
- Check `error.log` when debugging existing broken content.
