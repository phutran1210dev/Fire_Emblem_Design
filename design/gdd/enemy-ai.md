# Enemy AI

> From: `Enemy_AI.md`.

## Overview

Each enemy has a behaviour type and scores possible targets and moves, then
picks the best one unless a script overrides it.

## Detailed Rules

### Goals

Maximise threat to the player, follow objectives (attack, defend, retreat),
use terrain and formation.

### Behaviour types

| Type | Behaviour | Example |
|------|-----------|---------|
| Aggressive | Always moves and attacks if in range | Bandits rushing the nearest target |
| Defensive | Holds position until the player is near | Fort guards |
| Patrol | Walks a fixed path, attacks on contact | Castle patrols |
| Ambush | Hidden until triggered | Forest / behind-door units |
| Boss | Waits until attacked or scripted | Boss on the gate |
| Support | Buffs, heals, repositions allies | Healers |

### Turn flow

```text
Start AI turn → evaluate visible units → score possible moves
→ move toward / attack best target → end or wait
```

Each enemy asks: can I reach a target? can I survive the counter? can I block or delay the objective?

### Parameters

| Parameter | Meaning |
|-----------|---------|
| `aggroRadius` | Tiles before the unit activates |
| `moveLimit` | Max tiles from its origin |
| `targetBias` | Focus healers / tanks / weak units |
| `scriptTrigger` | Event-driven control |

### Scripted triggers

| Trigger | Example |
|---------|---------|
| Player enters zone | Ambush activates |
| Ally dies | Boss enrages |
| Turn count | Reinforcements on turn 5 |
| Objective reached | AI falls back / retreats |

### Advanced (later)

Adapt when the leader dies, coordinate formations, react to lost terrain, use skills/items.

## Formulas

```ts
priorityScore = lowHpBonus + damagePotential + classPriority + objectiveProximity
```

| Factor | Bonus |
|--------|-------|
| Target HP < 50% | +20 |
| Can kill target | +50 |
| Target is a healer | +30 |
| Target blocks objective tile | +40 |

## Dependencies

`combat-system.md` (damage prediction), `terrain-and-maps.md`, `map-events.md`, `game-loop.md`.

## Open Questions

[open-questions.md](open-questions.md): Q33 how "damage potential" and "survive retaliation"
turn into points, Q34 tie-breaking (needed for deterministic tests).
