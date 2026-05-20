# Common HOI4 Modding Failure Modes

## Mod Does Not Appear In Launcher

Likely causes:

- broken `.mod` path
- descriptor mismatch
- launcher cache issue
- mod folder not where HOI4 expects it
- mod not enabled in the playset

Agent behavior:

- inspect `.mod` and `descriptor.mod`
- compare path values to the actual folder structure
- avoid rewriting content before descriptor basics are checked

## Focus Tree Does Not Show

Likely causes:

- syntax error earlier in the file
- malformed token
- missing brace
- wrong `country = { ... }` selection
- invalid effect in `completion_reward`
- missing scope for a state-based effect
- mod not actually loaded

Agent behavior:

- inspect `error.log`
- find the last visible focus when possible
- inspect the focus before the first invisible one
- validate braces and scopes
- avoid redesigning the whole tree

## Event Says No Event With ID

Likely causes:

- namespace not declared
- event ID prefix does not match namespace
- event file not loaded
- typo in event call
- event ID suffix is inconsistent

Agent behavior:

- check `add_namespace`
- check event block IDs
- check callers in focuses, decisions, scripted effects, on-actions, or console commands
- check file location under `events/`

## Localization Key Appears Instead Of Text

Likely causes:

- missing `l_english:`
- wrong file or folder
- wrong key
- file encoding issue
- localization edited in vanilla instead of the mod
- typo between script key and localization key

Agent behavior:

- compare script references to localization keys
- create missing keys in mod localization files
- preserve language folder convention
- avoid inline player-facing text in script files

## Focus Icon Missing Or Question Mark

Likely causes:

- missing sprite definition
- missing shine sprite where the project expects one
- wrong image path
- broken `.gfx` braces
- sprite name mismatch

Agent behavior:

- inspect `interface/*.gfx`
- inspect relevant `gfx/` paths
- check normal and shine sprite names
- avoid assuming image files exist

## Decision Category Appears But Decisions Do Not

Likely causes:

- bad `allowed`, `visible`, or `available` logic
- decision file not loaded
- category constraints too strict
- missing country flag logic
- syntax issue earlier in the file

Agent behavior:

- separate category visibility from decision visibility
- inspect category `allowed`
- inspect individual decision `available`, `visible`, and flags
- check `error.log` before rewriting decision logic

## Game Crashes On Startup

Likely causes:

- malformed descriptor
- broken `replace_path`
- malformed map, state, or history files
- invalid database file loaded early
- missing required braces in common files

Agent behavior:

- inspect the earliest parse and load errors
- prioritize descriptor, load, and parse errors before gameplay logic
- avoid broad rewrites before identifying the first changed file involved

## National Spirit Does Not Appear

Likely causes:

- idea defined in the wrong idea group
- idea ID mismatch
- focus or event adds a non-existent idea
- idea file failed to load
- missing localization makes it appear as a raw key

Agent behavior:

- check `common/ideas/`
- check `add_ideas` and `remove_ideas`
- check localization
- check `error.log` for idea parsing errors
