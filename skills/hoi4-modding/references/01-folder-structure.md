# Folder Structure And Descriptors

HOI4 mods are project folders loaded on top of the base game. Do not edit the base HOI4 installation directly when working on a mod.

## Common Mod Layout

Common top-level paths include:

```txt
common/
events/
gfx/
history/
interface/
localisation/
map/
descriptor.mod
```

Common local development paths include:

- Windows: `Documents/Paradox Interactive/Hearts of Iron IV/mod/`
- Steam Workshop mods: managed separately by Steam and should not be edited directly for original work.

A local launcher `.mod` file often points at the mod folder. A published or portable mod usually includes `descriptor.mod` inside the mod folder.

## Agent Workflow

Before changing content:

1. Identify the active mod root.
2. Locate `descriptor.mod` and any sibling `.mod` launcher descriptor.
3. Check `path`, `name`, `supported_version`, dependencies, and `replace_path` entries when present.
4. Confirm the requested file belongs in the mod folder, not the vanilla install.
5. Search nearby files for naming conventions before creating new files.

## Overwrite Behavior

HOI4 loads mod files over base-game files. A file with the same path and name as a vanilla file may replace or override vanilla behavior depending on the folder and game system.

Agent behavior:

- Avoid silent overwrite unless the request clearly needs it.
- Prefer additive files when possible.
- Mention compatibility risks when changing files that likely override vanilla or another mod.
- Treat `replace_path` as high risk. It can disable entire vanilla folders and break compatibility with other mods.

## Descriptor Shape

Descriptors commonly look like:

```txt
name="My Mod"
path="mod/my_mod"
supported_version="1.*"
tags={
  "Alternative History"
}
```

Preserve the existing descriptor style and quote conventions.

## Descriptor Checks

When a mod does not appear or does not load:

- Check that the launcher descriptor points to the real folder.
- Check that `descriptor.mod` exists in the mod folder.
- Check for mismatched names, wrong paths, and stale launcher cache symptoms.
- Do not rewrite the mod structure before confirming descriptor basics.
