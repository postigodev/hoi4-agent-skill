# Broken Case: Event Namespace Mismatch

This case demonstrates an event that cannot be fired because the declared namespace and event ID prefix do not match.

## Failure

A focus, decision, console command, or scripted effect tries to fire:

```txt
country_event = { id = abc_reform.1 }
```

But the event file declares a different namespace.

## Broken Snippet

```txt
add_namespace = abc_events

country_event = {
  id = abc_reform.1
  title = abc_reform.1.t
  desc = abc_reform.1.d
  is_triggered_only = yes

  option = {
    name = abc_reform.1.a
  }
}
```

## Fixed Snippet

```txt
add_namespace = abc_reform

country_event = {
  id = abc_reform.1
  title = abc_reform.1.t
  desc = abc_reform.1.d
  is_triggered_only = yes

  option = {
    name = abc_reform.1.a
  }
}
```

## What An Agent Should Inspect

- The `add_namespace` line in the event file.
- The event block `id`.
- Any caller in focuses, decisions, scripted effects, on-actions, or console instructions.
- Whether the event file is actually under `events/`.
- `error.log` for parse errors earlier in the file that prevent the event from loading.

## Possible error.log Symptoms

```txt
Event referenced but not found: abc_reform.1
Could not find event with id abc_reform.1
```

Exact wording varies by game version and context.

## What Not To Overfix

- Do not rename every event in the mod.
- Do not change localization keys unless they are also wrong.
- Do not rewrite the caller before confirming the event namespace and ID.
- Do not claim the event was tested in-game unless HOI4 was actually launched.
