# Countries, History, And States

Country setup, history files, and states span multiple folders. These changes have a larger compatibility risk than isolated focuses or events.

Common paths include:

```txt
common/country_tags/
common/countries/
history/countries/
history/states/
map/
```

## Agent Workflow

Before editing:

1. Identify whether the request changes a country tag, country definition, history file, state ownership, cores, units, or map data.
2. Search for the target tag or state ID across the mod.
3. Check whether the mod is additive or overriding vanilla files.
4. Preserve local naming conventions.
5. Treat state and map changes as higher risk.

## Country Checks

When adding or editing a country, verify:

- country tag is unique
- tag is registered in the appropriate tag file
- country definition points to an existing country file
- history file exists and uses the expected tag/name convention
- localization exists for the country name when needed
- flag or cosmetic tag references are not claimed to exist unless files are present

## State And History Checks

When editing states or history:

- verify state IDs referenced by focuses, events, decisions, and effects
- check owner, controller, cores, claims, and victory points carefully
- avoid broad state-file rewrites
- mention compatibility risk when overriding vanilla state files
- read `error.log` for malformed state or history entries

## Common Failure Pattern

If a custom country has no name, flag, history, or expected land:

- check tag registration
- check country and history file paths
- check localization
- check state ownership and cores
- check referenced flag files only if the mod includes custom flags
