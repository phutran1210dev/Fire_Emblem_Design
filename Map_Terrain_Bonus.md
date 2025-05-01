# 🗺️ Map Terrain Bonus

This document describes the terrain system used in the SRPG game, including movement cost, combat bonuses, and strategic effects.

---

## 🌍 Terrain Types & Effects

| Terrain         | Move Cost | Avoid Bonus | DEF Bonus | RES Bonus | Special Effects               |
|-----------------|-----------|-------------|-----------|-----------|-------------------------------|
| Plain           | 1         | 0%          | 0         | 0         | —                             |
| Forest          | 2         | +20%        | +1        | 0         | Harder to hit                 |
| Mountain        | 3         | +30%        | +2        | 0         | Only infantry or fliers       |
| Hill            | 2         | +10%        | +1        | 0         | —                             |
| Water (Shallow) | 3         | 0%          | 0         | 0         | Only some classes can enter   |
| Water (Deep)    | —         | —           | —         | —         | Impassable except fliers      |
| Road            | 1         | 0%          | 0         | 0         | No penalties, +1 Move         |
| Fort            | 2         | +20%        | +2        | +2        | Heal 10% HP per turn          |
| Castle          | 1         | +25%        | +3        | +3        | Heal 20% HP per turn          |
| Bridge          | 1         | 0%          | 0         | 0         | Connects water tiles          |
| Desert          | 2–3       | +5%         | 0         | +1        | Some classes struggle to move |
| Cliff           | —         | —           | —         | —         | Impassable unless flying      |
| Gate            | 1         | +30%        | +4        | +2        | Usually guarded objective     |

---

## 🦶 Movement Types & Penalties

| Movement Type | Ignores Terrain | Struggles With         |
|----------------|------------------|------------------------|
| Infantry       | No               | Water, Mountains       |
| Cavalry        | No               | Forests, Hills, Gates  |
| Armor          | No               | Everything except road |
| Flying         | Yes              | None (but vulnerable)  |
| Mage / Staff   | No               | Mountains, Desert      |
| Thief          | Partial          | Can move through doors |

---

## 🧠 Strategy Notes

- **Forest** is ideal for dodging enemy attacks
- **Fort** and **Castle** give excellent defense and HP regen
- Use **Flying units** to bypass cliffs, water, or ambush zones
- Cavalry excels on **Roads** but is weak in **Forests**

---

## 🧱 Terrain Interaction (Advanced)

| Interaction Type | Example                             |
|------------------|--------------------------------------|
| Destructible     | Breakable walls, crates              |
| Unlockable       | Doors and chests (with key)          |
| Trigger          | Step tile to activate events/traps   |
| Objective        | Seize Gate, Defend Point             |

---

## 🗡️ Combat Positioning Tips

- Lure enemies into **Forest** to boost evasion
- Place tanks on **Fort** or **Castle** to soak damage
- Use **Terrain Control** to limit enemy movement range

---

🌟 *Master the terrain, and you master the battlefield.*