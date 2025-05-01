# 🧪 Status Effects System

This document outlines the status effects (buffs, debuffs, and conditions) used in the SRPG game.

---

## 💡 Overview

Status effects can:
- Temporarily modify unit stats
- Apply ongoing damage or healing
- Alter movement or action capabilities
- Be cleansed or resisted based on class or item

---

## ✅ Buff Effects (Positive)

| Name           | Effect                          | Duration | Stackable | Source               |
|----------------|----------------------------------|----------|-----------|----------------------|
| STR Up         | +X Strength                     | 3 turns  | No        | Item, skill          |
| MAG Up         | +X Magic                        | 3 turns  | No        | Skill, tome          |
| DEF Up         | +X Defense                      | 3 turns  | No        | Skill, gear          |
| RES Up         | +X Resistance                   | 3 turns  | No        | Cleric, items        |
| SPD Up         | +X Speed                        | 3 turns  | Yes       | Buff potion, rally   |
| LCK Up         | +X Luck                         | 3 turns  | No        | Passive, equipment   |
| Regen          | Restore %HP per turn            | 3–5 turns| No        | Accessory, terrain   |
| Barrier        | Reduce next X magic damage      | 1 turn   | No        | Staff, divine skill  |

---

## ❌ Debuff Effects (Negative)

| Name           | Effect                          | Duration | Can Cleanse | Notes                  |
|----------------|----------------------------------|----------|--------------|-------------------------|
| Poison         | -X HP per turn                  | 3 turns  | Yes          | Ignores DEF             |
| Bleed          | -% Max HP when taking damage    | 2 turns  | Yes          | Stackable               |
| Blind          | -50% Hit rate                   | 2 turns  | Yes          | Affects physical only   |
| Silence        | Cannot use magic                | 2 turns  | Yes          | Affects Tome/Staff only |
| Sleep          | Cannot act                      | 1–2 turns| Yes          | Ends on damage          |
| Stun           | Skip next turn                  | 1 turn   | Yes          | Rare                    |
| Rooted         | Cannot move                     | 1–3 turns| Yes          | Traps, skills           |
| Confused       | Random actions or self-attack   | 1–2 turns| Yes          | Low chance to trigger   |

---

## 🌀 Status Resistance

Some classes or items grant immunity or resistance to certain effects:

| Class / Item         | Immune To               |
|----------------------|-------------------------|
| Saint / Miracle Saint| Silence, Sleep          |
| Knight / GreatKnight | Bleed, Poison           |
| Cloak of Mind (gear) | Confusion, Blind        |
| Flying units         | Rooted, Terrain traps   |

---

## 🧼 Cleanse & Recovery

| Method            | Removes Effects         |
|-------------------|--------------------------|
| Restore Staff     | All debuffs except death |
| Elixir Item       | All buffs & debuffs      |
| Cleric Passive    | 1 random effect/turn     |
| Terrain (Fountain)| All effects on rest      |

---

## 🔄 Application Priority

1. Passive immunity check
2. Effect applied (turn duration begins)
3. Turn loop:
    - Duration reduced by 1
    - Effect triggered (if applicable)
4. Remove when duration = 0

---

📌 Design Tips:
- Limit stacking for balance
- Encourage counterplay through cleanse/resist
- Combine with terrain & positioning for tactical combos