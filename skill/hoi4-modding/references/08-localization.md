# Localization

HOI4 uses localization files for visible player-facing text. Do not put final UI text inline in script files when a localization key is expected.

## Common Location

Localization commonly lives under:

```txt
localisation/
```

Some mods use language subfolders. Preserve the current mod convention.

## Minimal Shape

```yml
l_english:
  ABC_first_focus:0 "Industrial Renewal"
  ABC_first_focus_desc:0 "A short original focus description."
  abc_story.1.t:0 "A New Direction"
  abc_story.1.d:0 "Original event description text."
  abc_story.1.a:0 "Continue."
```

Common file naming conventions include:

```txt
localisation/english/abc_l_english.yml
localisation/abc_l_english.yml
```

Preserve whichever convention the mod already uses.

## Agent Workflow

Before adding localization:

1. Find existing localization files for the same country, feature, or prefix.
2. Preserve language header style such as `l_english:`.
3. Match script keys exactly.
4. Add descriptions for focuses, ideas, decisions, and events when the game expects them.
5. Keep text original. Do not copy vanilla or DLC localization.
6. Preserve the file's existing encoding and line endings. Many HOI4 localization workflows expect UTF-8 with BOM, especially in older tooling.

## Common Key Patterns

Focuses:

```txt
ABC_focus_id
ABC_focus_id_desc
```

Events:

```txt
namespace.1.t
namespace.1.d
namespace.1.a
```

Ideas:

```txt
ABC_idea_name
ABC_idea_name_desc
```

Decisions:

```txt
ABC_decision_category
ABC_decision_name
ABC_decision_name_desc
```

## Dynamic Localization

Common dynamic patterns include bracketed references such as:

```txt
[Root.GetLeader]
[From.GetName]
[ABC.GetName]
```

Color codes commonly use section markers such as:

```txt
§Rred text§!
§Ggreen text§!
```

Preserve existing style and test in-game when text uses dynamic localization.

## Failure Modes

When keys appear in-game instead of text:

- missing language header
- wrong folder
- wrong file extension
- typo between script and localization key
- file encoding issue
- localization added to vanilla files instead of the mod
- localization file not loaded because of malformed YAML-like structure
