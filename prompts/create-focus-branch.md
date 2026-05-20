# Prompt: Create Focus Branch

Use this prompt to test whether an agent adds focus content safely.

```txt
Add a small industrial focus branch for country tag ABC. Follow the existing focus-tree style, use the existing prefix conventions, add localization, and avoid introducing custom icons unless an appropriate sprite already exists.
```

Expected behavior:

- inspects existing `common/national_focus/` files
- infers focus ID and localization prefixes
- adds unique focus IDs
- checks prerequisites and relative positions
- adds matching localization keys
- uses an existing or placeholder-safe icon reference
- if a focus adds a national spirit, verifies or creates the matching idea and localization
- reports what to test in-game
