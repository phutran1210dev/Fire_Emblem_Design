# Items & Inventory

> Merged from: `Item_System.md`, `Inventory_UI_Design.md`.

## Overview

Each unit carries up to 10 items: weapons, consumables, key items and passive
equipment. Items can be used, equipped, traded to an adjacent unit or discarded.

## Detailed Rules

### Categories

| Type | Description | Examples |
|------|-------------|----------|
| Healing | Restores HP | Potion, Elixir, Heal Herb |
| Buff | Temporary stat increase | Strength Tonic, Speed Leaf |
| Debuff | Weakens enemies | Poison Dust, Blind Bomb |
| Support | Utility | Revive Scroll, Warp Stone |
| Key Item | Opens paths, chests, events | Door Key, Master Key |
| Weapon | Equippable weapon | Iron Sword, Fire Tome |
| Consumable | Removed when used up | All healing / buff items |
| Equipment | Passive, non-consumable | Boots of Speed, Cloak of Magic |

### Healing

| Item | HP | Uses | Notes |
|------|----|------|-------|
| Potion | 20 | 3 | Basic |
| Elixir | Full | 1 | Full restore |
| Heal Herb | 10 | 5 | Light, low recovery |

### Buff items

| Item | Effect | Duration | Stacks |
|------|--------|----------|--------|
| Strength Tonic | +2 STR | 3 turns | No |
| Speed Leaf | +2 SPD | 3 turns | No |
| Iron Skin | +3 DEF | 3 turns | No |

### Debuff / utility

| Item | Effect | Duration | Notes |
|------|--------|----------|-------|
| Poison Dust | −5 HP/turn | 3 turns | RES applies |
| Blind Bomb | −50% Hit | 2 turns | |
| Warp Stone | Teleport user | Instant | Adjacent tile |

### Key items

| Item | Use |
|------|-----|
| Door Key | Opens 1 locked door |
| Chest Key | Opens 1 chest |
| Master Key | Opens any door / chest |

Key items are not usable in battle unless a script allows it.

### Equipment

| Item | Effect | Slot |
|------|--------|------|
| Boots of Speed | +2 Move | Footwear |
| Cloak of Magic | +3 RES | Armor |
| Amulet of Life | +5 HP regen per turn | Accessory |

One item per slot. Buffs from items can be spread across several units.

### Target types

Self (heal, buff) · Ally (revive, buff) · Enemy (debuff) · Area (multiple units).

### Inventory UI

| Action | Description |
|--------|-------------|
| Equip | Equip weapon or gear |
| Use | Use a healing / buff item |
| Trade | Move an item to an adjacent unit |
| Discard | Drop an item (e.g. when full) |
| View details | Show stats and effects |

UI elements: item list grid, detail pane on hover/click, equipment slot icons,
action pop-up menu. Goal: fast and clear during battle.

## Dependencies

`character-data.md`, `status-effects.md`, `weapons.md`, `map-events.md` (keys, chests).

## Open Questions

[open-questions.md](open-questions.md): Q27 Elixir, Q29 slot names differ
(Footwear/Armor/Accessory vs Weapon/Armor/Accessory), Q30 does using an item end the unit's action,
Q31 convoy / shared storage, Q32 promotion items (Master Seal) not listed.
