# Game Loop & Battle Flow

> Merged from: `Gameplay_Loop.md`, `BattleFlow.md`, `Victory_Conditions.md`,
> `Diagram_Summary.md` (section 1). Diagram: [game-loop-flowchart.png](../diagrams/game-loop-flowchart.png)

## Overview

A phase-based tactical RPG on a grid. Each round runs every side's phase in a
fixed order, then checks the mission's win and loss conditions. The loop repeats
until one of them is met.

## Detailed Rules

### Round structure

```text
Start Game / Load Save
↓
Preparation Phase
↓
Player Phase       → each player unit: Move / Act (Attack, Skill, Item, ...)
↓
Enemy Phase        → AI movement and attacks (see enemy-ai.md)
↓
Ally Phase         → (optional) friendly NPC units act
↓
Environment Phase  → traps, regen tiles, reinforcements, weather, event triggers
↓
Victory / Defeat check
↓
No condition met → next round, back to Player Phase
```

| Phase | Who acts | Notes |
|-------|----------|-------|
| Player | All player units, one action each | Player chooses unit order |
| Enemy | AI units | Behaviour per `enemy-ai.md` |
| Ally | Friendly NPCs | Optional; escort / defend missions |
| Environment | The map | Traps, regen, reinforcements, scripted events |

### Unit action flow

```text
Start unit turn → Move (optional) → Act (optional) → End unit turn
```

- A unit acts **once per phase**.
- After Attack or an Active Skill the unit **cannot move again**.
  Exception: skills like **Canto** allow movement after acting.

| Action | Description |
|--------|-------------|
| Move | Up to the unit's `mov` stat, terrain costs apply (`terrain-and-maps.md`) |
| Attack | Weapon attack, melee or ranged (`combat-system.md`) |
| Skill | Active ability (`skill-system.md`) |
| Item | Use a consumable or equip gear (`items-and-inventory.md`) |
| Wait | End the unit's turn |
| Talk | Special interaction (recruit, dialogue) |
| Rescue | Carry another unit, if allowed |

### End-of-round events (Environment Phase)

- HP regen from terrain or passives
- Poison and other status ticks
- Buff / debuff durations decrease (`status-effects.md`)
- Reinforcements and story triggers (`map-events.md`)

### Victory conditions

| Type | Rule |
|------|------|
| Rout | Defeat all enemy units |
| Boss Kill | Defeat a specific enemy |
| Seize | Move a (lord) unit onto the goal tile |
| Defend | Survive X turns |
| Escape | All player units reach the destination tile(s) |
| Rescue / Protect | Escort an NPC; it must survive |
| Puzzle | Meet a specific non-combat goal |

### Defeat conditions

| Condition | Rule |
|-----------|------|
| Player wiped | All player units defeated |
| Main hero dies | A specific unit is defeated |
| NPC dies | The objective unit is defeated |
| Turn limit | Max turn count exceeded |

```ts
if (goal === 'seize' && unit.position === gateTile) battleWin()
```

## Dependencies

- `enemy-ai.md` (Enemy Phase), `map-events.md` (Environment Phase)
- `combat-system.md`, `skill-system.md`, `items-and-inventory.md` (actions)
- `turn-order-timeline.md` replaces this phase model if that optional system is chosen

## Open Questions

See [open-questions.md](open-questions.md): Q1 (Preparation Phase contents),
Q2 (does victory get checked mid-phase?).
