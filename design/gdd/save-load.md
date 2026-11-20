# Save / Load

> From: `Save_Load_System.md`.

## Overview

Saves the full battle and campaign state as JSON so a game can resume anywhere,
including mid-battle.

## Detailed Rules

| Section | Contents |
|---------|----------|
| Player state | Every unit's stats, items, EXP |
| Map state | Tile layout, units on grid |
| Turn state | Round, phase, whose turn |
| Event flags | Triggers fired, choices made |
| Timestamp | When saved |

| Save type | When |
|-----------|------|
| Manual | From the menu |
| Auto | After a chapter, turn or battle |
| Quick | Temporary mid-battle save |

```json
{
  "map": "chapter3_castle",
  "turn": 4,
  "phase": "player",
  "units": [],
  "flags": { "boss_escaped": false },
  "timestamp": "2025-05-02T12:00:00Z"
}
```

## Dependencies

`character-data.md`, `map-events.md`, `game-loop.md`.

## Open Questions

[open-questions.md](open-questions.md): Q40 save versioning, Q41 RNG seed in save (anti save-scum or not),
Q42 number of slots.
