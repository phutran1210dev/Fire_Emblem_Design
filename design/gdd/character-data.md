# Character Data Model

> From: `Character_Template.md`. This is the data schema every unit uses.

## Overview

A unit is one JSON object: identity, stats, proficiencies, inventory, skills,
status and grid position.

## Detailed Rules

### Identity

| Field | Type | Description |
|-------|------|-------------|
| `id` | string | Unique id |
| `name` | string | Name |
| `title` | string | Optional subtitle ("Wings of Dawn") |
| `class` | enum | Current class (`class-system.md`) |
| `tier` | number | 1–5 |
| `level` | number | 1–20 per tier |
| `exp` | number | 0–100 per level |
| `affiliation` | string | Faction |
| `bio` | string | Short lore |

### Stats

| Stat | Meaning |
|------|---------|
| `hp` / `maxHp` | Current / max HP |
| `str` | Physical damage |
| `mag` | Magic damage |
| `skl` | Accuracy, crit |
| `spd` | Avoid (and turn order if timeline is used) |
| `def` | Physical resistance |
| `res` | Magic resistance |
| `lck` | Crit avoid, misc |
| `mov` | Movement range in tiles |

### Proficiency

Rank `E → S+` per weapon type: Sword, Axe, Lance, Bow, Dagger, Tome, Staff, Spear, Arcane.

### Inventory & skills

- Up to **10** inventory entries `{ itemId, quantity, equipped }`.
- Skills: `{ learned: [...], equipped: [...] }`, max **4** equipped by default.

### Runtime status

| Field | Description |
|-------|-------------|
| `statusEffects` | Active buffs / debuffs |
| `isAlive` | `hp > 0` |
| `canAct` | Not stunned / asleep (silence only blocks magic) |
| `position` | Grid `{ x, y }` |

### Example

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
  "hp": 32, "maxHp": 40,
  "str": 12, "mag": 8, "skl": 14, "spd": 18,
  "def": 9, "res": 13, "lck": 10, "mov": 8,
  "proficiency": { "sword": "C", "lance": "A", "staff": "D" },
  "inventory": [
    { "itemId": "steel_lance", "quantity": 1, "equipped": true },
    { "itemId": "heal_staff", "quantity": 1, "equipped": false }
  ],
  "skills": { "learned": ["sky_strike", "wind_aura"], "equipped": ["sky_strike"] },
  "statusEffects": [],
  "isAlive": true,
  "canAct": true,
  "position": { "x": 5, "y": 12 }
}
```

## Dependencies

Used by every other system.

## Open Questions

[open-questions.md](open-questions.md): Q17 no MP/SP fields, Q18 no growth-rate field,
Q19 example "Falcon Knight" is Tier 2 in the class tree but `tier: 3` here.
