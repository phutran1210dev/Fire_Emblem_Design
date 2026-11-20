# Turn-Order Timeline (optional)

> From: `Turn_Order_Timeline.md`. **Alternative** to the phase model in `game-loop.md`;
> pick one before building.

## Overview

An initiative system in the style of classic tactics games: units act one at a
time in SPD order instead of by side.

## Detailed Rules

- Each unit has an initiative score from SPD; the order is re-sorted every round.
- Skills like Slow and Haste move units on the timeline.
- UI: a bar on the screen edge showing the next 10 actions as portraits.

| Effect | Description |
|--------|-------------|
| Delay | Push a unit later |
| Skip turn | Remove its next slot |
| Interrupt | Cancel the current action |

Best for 1v1 and boss fights.

## Formulas

```ts
initiative = unit.SPD + random(0, 3)
```

## Dependencies

Replaces the phase loop in `game-loop.md`; affects `enemy-ai.md` and `status-effects.md` (durations).

## Open Questions

[open-questions.md](open-questions.md): Q43 phase model or timeline — decision needed.
