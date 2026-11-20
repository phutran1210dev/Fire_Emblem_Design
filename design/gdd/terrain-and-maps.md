# Terrain & Maps

> Merged from: `Map_Terrain_Bonus.md`, `Map_Design_Examples.md`.

> **Approved change (2026-11-21, [review](../reviews/2026-11-21-gameplay-differentiation.md)):** P1 Living Battlefield: Burning → Ash, Ice over water, thunder chains through water, wind pushes and puts out fire. Forced movement (Shove / Pull / Swap); pushes off cliffs Stun + 5 dmg instead of killing.
> Not yet written into the sections below — next `/design-system` pass.

## Overview

Every tile has a terrain type with a movement cost and defensive bonuses.
Movement types decide which terrain a unit can cross.

## Detailed Rules

### Terrain

| Terrain | Move cost | Avoid | DEF | RES | Special |
|---------|-----------|-------|-----|-----|---------|
| Plain | 1 | 0% | 0 | 0 | — |
| Forest | 2 | +20% | +1 | 0 | Harder to hit |
| Mountain | 3 | +30% | +2 | 0 | Infantry or fliers only |
| Hill | 2 | +10% | +1 | 0 | — |
| Shallow water | 3 | 0% | 0 | 0 | Some classes only |
| Deep water | — | — | — | — | Fliers only |
| Road | 1 | 0% | 0 | 0 | +1 Move |
| Fort | 2 | +20% | +2 | +2 | Heal 10% HP / turn |
| Castle | 1 | +25% | +3 | +3 | Heal 20% HP / turn |
| Bridge | 1 | 0% | 0 | 0 | Crosses water |
| Desert | 2–3 | +5% | 0 | +1 | Some classes slowed |
| Cliff | — | — | — | — | Fliers only |
| Gate | 1 | +30% | +4 | +2 | Usually the seize objective |

### Movement types

| Type | Ignores terrain | Struggles with |
|------|-----------------|----------------|
| Infantry | No | Water, mountains |
| Cavalry | No | Forest, hills, gates |
| Armor | No | Everything except road |
| Flying | Yes | None (but weak to bows) |
| Mage / Staff | No | Mountains, desert |
| Thief | Partial | Can pass doors |

### Interactive terrain

| Kind | Example |
|------|---------|
| Destructible | Breakable walls, crates |
| Unlockable | Doors, chests (key) |
| Trigger | Step on tile → event / trap |
| Objective | Seize gate, defend point |

Tactics: lure enemies into forest, park tanks on forts/castles, use fliers to
cross cliffs and water, keep cavalry on roads.

### Example maps

**Chapter 1 — Forest Ambush.** 12×12, forests and plains, 5 bandits + 1 boss, objective: Rout.

```
P P P P F F F F F F F P
P P P P F . . . . F B P
P H . . . . . . . . . P
. . . . . . . . . . . .
```
P = Plain, F = Forest, H = House, B = Boss start (only 4 of 12 rows drawn so far).

**Chapter 2 — Castle Siege.** 15×15, gates, fort, road. Guards, archers, boss. Objective: seize the throne.

**Chapter 3 — Bridge Siege.** See `map-events.md` (wyvern ambush).

## Dependencies

`combat-system.md`, `class-system.md` (movement type per class), `map-events.md`, `enemy-ai.md`.

## Open Questions

[open-questions.md](open-questions.md): Q5 terrain avoid in hit formula, Q13 class → movement type,
Q35 numeric extra costs for "struggles with", Q36 desert 2 vs 3, Q37 Chapter 1 map incomplete.
