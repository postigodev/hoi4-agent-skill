# Prompt: Debug error.log

Use this prompt to test whether an agent debugs from logs instead of guessing.

```txt
My HOI4 mod loads, but the new focus branch is missing in-game. I have an error.log excerpt with parse errors and missing localization warnings. Inspect the mod structure, read the log first, identify the highest-priority errors, and make the smallest safe fixes. Report changed files, IDs touched, localization keys added, and what I should test in HOI4.
```

Expected behavior:

- asks for or inspects `error.log`
- fixes parse errors before localization warnings
- checks the focus before the first missing/invisible focus
- avoids redesigning the whole tree
- ignores unrelated vanilla/mod warnings unless they block the requested feature
- reports remaining risks
