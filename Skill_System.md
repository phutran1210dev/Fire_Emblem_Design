# 🧠 Skill System

This document defines the structure and logic of the skill system in the SRPG game.

---

## 🧩 Skill Categories

| Type         | Description                              | Example Skills             |
|--------------|------------------------------------------|----------------------------|
| Active       | Used manually during battle              | Power Strike, Heal, Fireball |
| Passive      | Always in effect once learned            | Dodge +10%, Crit Boost     |
| Reaction     | Triggers under certain conditions        | Counterattack, Miracle     |
| Terrain-based| Activated when standing on certain tiles | Forest Camouflage          |
| Class-Specific | Unique to certain classes or tiers     | Pegasus Blessing, Mage Focus |

---

## ⚔️ Sample Skill Definitions

### 🔹 Active Skill

```json
{
  "id": "fireball",
  "name": "Fireball",
  "type": "active",
  "range": 2,
  "power": 12,
  "cost": 3,
  "effect": "magic_damage",
  "cooldown": 0
}
```

### 🔹 Passive Skill

```json
{
  "id": "dodge_plus_10",
  "name": "Evasion Boost",
  "type": "passive",
  "effect": "increase_avoid",
  "value": 10
}
```

### 🔹 Reaction Skill

```json
{
  "id": "miracle",
  "name": "Miracle",
  "type": "reaction",
  "trigger": "lethal_damage",
  "effect": "survive_with_1hp",
  "chance": 20
}
```

---

## 🧠 Skill Mechanics

- Skills can be learned via:
  - Level up
  - Promotion
  - Scrolls or Tomes
  - Event unlock

- Skills can be **equipped** (if limit applies):
  - Max 4 skills equipped (customizable)

- **Skill Points (SP)** system for learning:
  - Gain SP per combat action or battle
  - Cost varies based on tier

---

## 🧬 Skill Tier & Rarity

| Tier | Description              | Example                    |
|------|--------------------------|----------------------------|
| Common  | Low effect, widely available  | +5% Crit                  |
| Rare    | Moderate effect or limited use | Counterattack            |
| Epic    | High utility or powerful passives | Nullify Terrain Penalty |
| Legendary | Class-defining effects     | Heal All, Dragon Wrath   |

---

## 🎯 Targeting & Effects

| Target Type | Example Skills      |
|-------------|---------------------|
| Self        | Heal, Buff          |
| Ally        | Heal, Revive        |
| Enemy       | Damage, Debuff      |
| AoE (Area)  | Flame Circle, Rally |

---

## 🔄 Cooldown & Cost System

| Stat       | Explanation                      |
|------------|----------------------------------|
| Cooldown   | Turns before skill can be reused |
| Cost       | MP, SP, or HP                    |
| Duration   | Number of turns effect lasts     |

---

💡 Combine passive + active + terrain + class synergy for tactical depth.