# Events

Events usually live under:

```txt
events/
```

Event files commonly declare a namespace and then define event blocks.

## Minimal Shape

```txt
add_namespace = abc_story

country_event = {
  id = abc_story.1
  title = abc_story.1.t
  desc = abc_story.1.d
  picture = GFX_report_event_generic

  is_triggered_only = yes

  option = {
    name = abc_story.1.a
  }
}
```

Common event caller shapes:

```txt
country_event = { id = abc_story.1 }
news_event = { id = abc_story.2 }
```

## Namespace Rules

Agent behavior:

- Check `add_namespace`.
- Ensure event IDs use the declared namespace.
- Ensure event calls use the exact event ID.
- Keep suffixes consistent and unique.
- Avoid mixing prefixes from different files without a clear reason.
- Use one namespace declaration style per event file. Do not create multiple competing namespaces unless the existing project already does that.

## Fired Versus Natural Events

If an event is fired from a focus, decision, scripted effect, or on-action, `is_triggered_only = yes` is often intended.

If the user expects the event to happen naturally, check for:

- `trigger`
- `mean_time_to_happen`
- `fire_only_once`
- `on_actions`
- date or country conditions

## Localization

Visible event fields should use localization keys:

```txt
title = abc_story.1.t
desc = abc_story.1.d
option = {
  name = abc_story.1.a
}
```

Add matching localization in the mod localization folder.

## Options And Effects

Options can contain effects. Verify the option runs in the expected country scope before adding state, character, or unit effects.

Check nearby examples before using `immediate`, `hidden_effect`, or delayed event firing.

## Debugging

For "no event with ID" or silent event failures:

1. Check the namespace declaration.
2. Check the event ID.
3. Check the caller.
4. Check that the file is under `events/`.
5. Check `error.log` for parse errors that may prevent later events from loading.
