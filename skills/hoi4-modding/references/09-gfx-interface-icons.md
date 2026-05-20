# GFX, Interface, And Icons

GFX and interface references connect script IDs to sprite definitions and image files.

Common paths include:

```txt
interface/
gfx/
gfx/interface/
gfx/interface/goals/
```

## Agent Workflow

Before adding a custom icon:

1. Check whether an existing sprite can be reused.
2. Inspect relevant `.gfx` files.
3. Verify sprite names match script references exactly.
4. Verify image paths exist in the mod workspace.
5. Check normal and shine conventions where the project uses them.
6. Do not claim an icon exists unless the file is present.

## Minimal Sprite Shape

Use original names and paths:

```txt
spriteTypes = {
  spriteType = {
    name = "GFX_goal_ABC_industrial_push"
    texturefile = "gfx/interface/goals/ABC_industrial_push.dds"
  }
}
```

Use nearby project examples for `spriteTypes`, shine sprites, and image format conventions.

## Validation

Before finishing, verify:

- `.gfx` braces are balanced
- sprite names match script references
- texture paths exist or are clearly marked placeholders
- image files are original or user-provided
- no proprietary Paradox artwork is copied into the repository

## Common Failure Pattern

If a focus icon shows as missing or a question mark:

- check sprite definition
- check image path
- check `.gfx` syntax
- check whether the project expects a shine sprite
- check file extension and case sensitivity for target platforms
