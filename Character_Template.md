# 🧙 Character Template

This document defines the structure, attributes, and metadata for designing characters in the SRPG system.

---

## 🧾 Basic Information

| Field        | Type     | Description                      |
|--------------|----------|----------------------------------|
| `id`         | string   | Unique identifier                |
| `name`       | string   | Character's name                 |
| `title`      | string   | Optional subtitle (e.g. "The Brave") |
| `class`      | enum     | Current class (CharacterClass)   |
| `tier`       | number   | 1–5                              |
| `level`      | number   | Current level (1–20 per tier)    |
| `exp`        | number   | Current EXP (0–100 per level)    |
| `affiliation`| string   | Faction or group name            |
| `bio`        | string   | Short background or lore         |

---

## 💪 Stats

| Stat    | Type   | Description                        |
|---------|--------|------------------------------------|
| `hp`    | number | Current HP                         |
| `maxHp` | number | Max HP                             |
| `str`   | number | Strength (physical damage)         |
| `mag`   | number | Magic power                        |
| `skl`   | number | Skill (accuracy, crit)             |
| `spd`   | number | Speed (turn order, avoid)          |
| `def`   | number | Defense (physical resist)          |
| `res`   | number | Resistance (magic resist)          |
| `lck`   | number | Luck (crit avoid, misc bonuses)    |
| `mov`   | number | Movement range                     |

---

## 🧠 Proficiency

| Weapon Type | Level (E → S+) |
|-------------|----------------|
| Sword       | string         |
| Axe         | string         |
| Lance       | string         |
| Bow         | string         |
| Dagger      | string         |
| Tome        | string         |
| Staff       | string         |
| Spear       | string         |
| Arcane      | string         |

---

## 🎒 Inventory

Each character can carry up to 10 items:

```json
[
  {
    "itemId": "iron_sword",
    "quantity": 1,
    "equipped": true
  },
  {
    "itemId": "healing_potion",
    "quantity": 2,
    "equipped": false
  }
]
```

---

## 🧬 Skills

Skills learned and currently equipped:

```json
{
  "learned": ["fireball", "counterattack", "evasion_boost"],
  "equipped": ["fireball", "evasion_boost"]
}
```

- Max equipped: 4 (by default)

---

## 💥 Status

| Field           | Description                        |
|------------------|------------------------------------|
| `statusEffects` | List of current buffs/debuffs       |
| `isAlive`       | Boolean, if current HP > 0          |
| `canAct`        | Boolean, not stunned/sleep/silenced |
| `position`      | Grid coordinate (x, y)              |

---

## 📘 Example Character JSON

```json
{
  "id": "unit_001",
  "name": "Lyra",
  "title": "Wings of Dawn",
  "class": "Falcon Knight",
  "tier": 3,
  "level": 7,
  "exp": 35,
  "affiliation": "Sky Order",
  "bio": "A noble knight of the skies.",
  "hp": 32,
  "maxHp": 40,
  "str": 12,
  "mag": 8,
  "skl": 14,
  "spd": 18,
  "def": 9,
  "res": 13,
  "lck": 10,
  "mov": 8,
  "proficiency": {
    "sword": "C",
    "lance": "A",
    "staff": "D"
  },
  "inventory": [
    { "itemId": "steel_lance", "quantity": 1, "equipped": true },
    { "itemId": "heal_staff", "quantity": 1, "equipped": false }
  ],
  "skills": {
    "learned": ["sky_strike", "wind_aura"],
    "equipped": ["sky_strike"]
  },
  "statusEffects": [],
  "isAlive": true,
  "canAct": true,
  "position": { "x": 5, "y": 12 }
}
```

---

📌 This structure allows deep integration with stat growth, skill trees, inventory, AI logic, and more.