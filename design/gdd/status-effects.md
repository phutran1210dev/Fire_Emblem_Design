# Status Effects

> From: `StatusEffects.md`.

> **Approved change (2026-11-21, [review](../reviews/2026-11-21-gameplay-differentiation.md)):** Burn defined (Burning tile or fire crit). All statuses tick in the Environment Phase.
> Not yet written into the sections below — next `/design-system` pass.

## Overview

Timed buffs and debuffs that change stats, deal or heal damage over time, or
restrict movement and actions. Some classes and gear are immune; several
methods cleanse them.

## Detailed Rules

### Buffs

| Name | Effect | Duration | Stacks | Source |
|------|--------|----------|--------|--------|
| STR Up | +X STR | 3 turns | No | Item, skill |
| MAG Up | +X MAG | 3 turns | No | Skill, tome |
| DEF Up | +X DEF | 3 turns | No | Skill, gear |
| RES Up | +X RES | 3 turns | No | Cleric, items |
| SPD Up | +X SPD | 3 turns | Yes | Potion, rally |
| LCK Up | +X LCK | 3 turns | No | Passive, equipment |
| Regen | Restore %HP per turn | 3–5 turns | No | Accessory, terrain |
| Barrier | Reduce next X magic damage | 1 turn | No | Staff, divine skill |

### Debuffs

| Name | Effect | Duration | Cleansable | Notes |
|------|--------|----------|------------|-------|
| Poison | −X HP per turn | 3 turns | Yes | Ignores DEF |
| Bleed | −% max HP when taking damage | 2 turns | Yes | Stacks |
| Blind | −50% Hit | 2 turns | Yes | Physical only |
| Silence | Cannot use magic | 2 turns | Yes | Tome / Staff only |
| Sleep | Cannot act | 1–2 turns | Yes | Ends on damage |
| Stun | Skip next turn | 1 turn | Yes | Rare |
| Rooted | Cannot move | 1–3 turns | Yes | Traps, skills |
| Confused | Random action / self-attack | 1–2 turns | Yes | Low trigger chance |

### Immunities

| Class / item | Immune to |
|--------------|-----------|
| Saint / Miracle Saint | Silence, Sleep |
| Knight / Great Knight | Bleed, Poison |
| Cloak of Mind (gear) | Confusion, Blind |
| Flying units | Rooted, terrain traps |

### Cleansing

| Method | Removes |
|--------|---------|
| Restore Staff | All debuffs except death |
| Elixir | All buffs and debuffs |
| Cleric passive | 1 random effect per turn |
| Fountain terrain | All effects on rest |

### Processing order

1. Check passive immunity
2. Apply effect; duration starts
3. Each turn: duration −1, then trigger the effect if it ticks
4. Remove at duration 0

Design notes: limit stacking; give counterplay through cleanse/resist; combine
with terrain and positioning.

## Dependencies

`combat-system.md`, `skill-system.md`, `items-and-inventory.md`, `game-loop.md` (tick timing).

## Open Questions

[open-questions.md](open-questions.md): Q25 Burn, Q26 "X" values, Q27 Elixir conflict
(item heals HP vs cleanses), Q28 tick at start or end of unit's turn.
