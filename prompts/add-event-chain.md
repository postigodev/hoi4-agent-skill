# Prompt: Add Event Chain

Use this prompt to test namespace and localization behavior.

```txt
Add a short two-event political event chain for country tag ABC. It should be triggered manually from a focus reward later, so make the events externally fired. Use the mod's existing event namespace conventions if they exist, add localization, and report the event IDs I can call.
```

Expected behavior:

- inspects existing `events/` files
- uses or creates a clear namespace
- sets externally fired events appropriately
- keeps event IDs unique
- adds title, description, and option localization
- reports exact event IDs
- reports the exact effect/call syntax to trigger the first event from a focus or decision
