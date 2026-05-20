# Claude Adapter

The canonical Claude-compatible skill folder is:

```txt
skill/hoi4-modding/
```

That folder contains `SKILL.md` with YAML frontmatter plus supporting references.

Upload or install the entire `skill/hoi4-modding/` directory as a Claude Skill.

Claude should receive the skill folder itself:

```txt
hoi4-modding/
  SKILL.md
  LICENSE.txt
  references/
```

Do not upload the entire repository unless your Claude environment expects repository-level context.

Do not fork the full instructions into this adapter. The source of truth is `skill/hoi4-modding/SKILL.md`.
