# Map Events & Triggers

> Merged from: `Map_Event_Trigger_Flow.md`, `Diagram_Summary.md` (section 4).
> Diagram: [map-event-trigger-flowchart.png](../diagrams/map-event-trigger-flowchart.png)

## Overview

Maps hold triggers. When a condition is met, an event runs once (guarded by a
flag) and the battle resumes.

## Detailed Rules

```text
Start map → register triggers → player moves / acts
→ condition met? → resolve event type → apply effect
→ set event flag (no repeat) → resume battle
```

### Event types

| Type | Effect |
|------|--------|
| Enemy spawn | Reinforcements at given tiles |
| Dialogue | Cutscene / story talk |
| Item grant | Free item or treasure |
| Door / Gate | Opens a path |
| Scripted | Story branch or condition change |

### Conditions

| Condition | Example |
|-----------|---------|
| Position | A player unit steps on (x, y) |
| Kill count | Enemies remaining < 3 |
| Turn number | Turn ≥ 5 |
| Unit action | Talk, use key, wait on tile |
| Flag check | Event not yet triggered |

### Flags

```ts
if (!eventFlags["ch2_gate_open"]) {
  openGate()
  eventFlags["ch2_gate_open"] = true
}
```

Flags stop repeats, can feed win/loss conditions, and are saved (`save-load.md`).

### Example

Chapter 3 — Bridge Siege: trigger tile (8, 4); a player unit steps on it;
3 Wyvern Riders spawn from the north; flag `ch3_wyverns_spawned`.

## Dependencies

`game-loop.md`, `enemy-ai.md` (scripted triggers), `save-load.md`, `terrain-and-maps.md`.

## Open Questions

[open-questions.md](open-questions.md): Q38 do enemy units fire position triggers,
Q39 Wyvern Rider is not a class in the class tree.
