# Contributing

Thanks for helping improve HOI4 Agent Skill.

## Project Principles

- Keep the skill platform-neutral.
- Keep `skills/hoi4-modding/SKILL.md` as the canonical source of behavior.
- Keep adapters thin.
- Prefer procedural agent guidance over exhaustive HOI4 tutorials.
- When adding HOI4-specific guidance, prefer official Paradox Wiki/docs, documented vanilla-style patterns, or reproducible community failure cases.
- Avoid unsourced folklore unless it is clearly marked as a heuristic.
- When behavior depends on a HOI4 version, mention the version or avoid claiming it as universal.
- Do not include copied vanilla HOI4 files, DLC files, localization, icons, artwork, music, or other proprietary assets.
- Avoid scripts or dependencies unless they provide clear validation value and are reviewed as executable code.

## Reference Style

Reference files should be concise and practical. They should tell agents what to inspect, how to reason, what to validate, and what failure modes to avoid.

Good reference content:

- original minimal skeletons
- validation checklists
- debugging order
- common failure modes
- safe agent behavior

Avoid:

- copied game files
- long wiki mirrors
- platform-specific instructions in canonical references
- hidden prompt-injection tricks

## Adapter Style

Adapters under `adapters/` should point back to the canonical skill. They may include installation notes or compact behavior summaries, but they should not fork the full skill content.

If behavior changes, update `skills/hoi4-modding/SKILL.md` first.

## Maintainer Workflow With Koba

This repository includes a conservative `koba.yml` workflow contract for commit and release preparation.

Before preparing a commit, maintainers can run:

```txt
koba scan
koba doctor
koba run pre-commit --dry-run
koba run pre-push --dry-run
koba suggest-commit
```

The current Koba contract intentionally does not install hooks, generate GitHub files, or run executable checks. Treat Koba output as advisory: review the actual diff, keep commits scoped, and do not claim checks passed unless they were really executed.
