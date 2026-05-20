# Prompt: Review Mod PR

Use this prompt to test code-review behavior for HOI4 mod changes.

```txt
Review this HOI4 mod PR. Focus on bugs and load risks: descriptor issues, syntax errors, missing localization, namespace mismatches, invalid references, invalid scopes, duplicate IDs, and proprietary asset concerns. Lead with findings grouped by load-breaking, gameplay-breaking, missing content/reference, and maintainability. Include file/line references where possible.
```

Expected behavior:

- reviews for behavioral/load failures first
- checks localization references
- checks event namespaces and callers
- checks focus prerequisites and GFX references
- flags copied proprietary assets when visible
- avoids style-only feedback unless it affects maintainability or mod load safety
