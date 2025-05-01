# 🎒 Item System

This document defines the item system used in the SRPG game including item types, effects, limitations, and usage logic.

---

## 📦 Item Categories

| Type         | Description                               | Example Items           |
|--------------|-------------------------------------------|--------------------------|
| Healing      | Restores HP                               | Potion, Elixir, Heal Herb |
| Buff         | Temporarily increases stats               | Strength Tonic, Speed Leaf |
| Debuff       | Reduces enemy stats or status             | Poison Dust, Blind Bomb |
| Support      | Utility effects (revive, teleport, etc.)  | Revive Scroll, Warp Stone |
| Key Item     | Used to unlock paths, chests, or events   | Door Key, Master Key     |
| Weapon       | Equippable weapons                        | Iron Sword, Fire Tome    |
| Consumable   | Single-use and removed after use          | All healing/buff items   |
| Equipment    | Non-consumable, provides passive effects  | Boots of Speed, Cloak of Magic |

---

## 🩹 Healing Items

| Name         | HP Restored | Uses | Notes                      |
|--------------|-------------|------|----------------------------|
| Potion       | 20          | 3    | Basic HP restore           |
| Elixir       | Full        | 1    | Full HP restore            |
| Heal Herb    | 10          | 5    | Lightweight, low recovery  |

---

## 💪 Buff Items

| Name             | Effect                  | Duration | Stackable |
|------------------|-------------------------|----------|-----------|
| Strength Tonic   | +2 STR                  | 3 turns  | No        |
| Speed Leaf       | +2 SPD                  | 3 turns  | No        |
| Iron Skin        | +3 DEF                  | 3 turns  | No        |

---

## 🧪 Debuff / Utility Items

| Name           | Effect                  | Duration | Notes                  |
|----------------|-------------------------|----------|------------------------|
| Poison Dust    | -5 HP/turn              | 3 turns  | Magic Resistance applies |
| Blind Bomb     | -50% Hit                | 2 turns  | Reduces accuracy       |
| Warp Stone     | Teleports user          | Instant  | Choose adjacent tile   |

---

## 🗝️ Key Items

| Name         | Usage                     |
|--------------|----------------------------|
| Door Key     | Opens 1 locked door        |
| Chest Key    | Opens 1 chest              |
| Master Key   | Opens any door/chest       |

---

## ⚙️ Equipment (Passive Gear)

| Name             | Effect                       | Slot       |
|------------------|------------------------------|------------|
| Boots of Speed   | +2 Move                      | Footwear   |
| Cloak of Magic   | +3 RES                       | Armor      |
| Amulet of Life   | Regenerate 5 HP per turn     | Accessory  |

---

## 🔄 Item Usage Rules

- **Inventory Limit**: Each unit can hold up to **10 items**
- **Only 1 equipment per slot** (footwear, armor, accessory)
- **Consumables** are removed on use
- **Key Items** are not usable in battle unless scripted

---

## 🎯 Item Target Types

| Target Type | Example Use           |
|-------------|------------------------|
| Self        | Healing, buffs         |
| Ally        | Revive, buff           |
| Enemy       | Debuff items           |
| Area        | Affects multiple units |

---

## 💡 Strategy Tips

- Buffs can be stacked across multiple units
- Equip passive gear based on map needs (magic-heavy = Cloak of Magic)
- Always carry at least 1 healing item