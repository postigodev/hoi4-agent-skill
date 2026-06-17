# Broken Case: Missing Localization

This case demonstrates visible raw keys in-game because script references have no matching localization entries.

## Failure

The focus exists, but the player sees raw keys such as `ABC_start_reform` or `ABC_start_reform_desc` instead of readable text.

## Broken Snippet

Script:

```txt
focus = {
  id = ABC_start_reform
  icon = GFX_goal_ABC_reform
  x = 0
  y = 0
  cost = 10
}
```

Localization file:

```yml
l_english:
  ABC_old_focus:0 "Old Focus"
  ABC_old_focus_desc:0 "This key does not match the script."
```

## Fixed Snippet

```yml
l_english:
  ABC_start_reform:0 "Begin Administrative Reform"
  ABC_start_reform_desc:0 "We will organize a small committee to review our institutions and prepare the next phase of reform."
```

## What An Agent Should Inspect

- The exact script IDs and visible text keys.
- Existing localization file and language-folder conventions.
- The `l_english:` header.
- File naming and extension, such as `ABC_l_english.yml`.
- Encoding and line endings, preserving the file's existing style.

## Possible error.log Symptoms

```txt
Missing localization: ABC_start_reform
Missing localization: ABC_start_reform_desc
```

Some missing localization issues may appear only as raw keys in-game.

## What Not To Overfix

- Do not rename focus IDs just to make text appear.
- Do not edit vanilla localization files.
- Do not add final player-facing text inline in script files.
- Do not normalize every localization file in the mod.
