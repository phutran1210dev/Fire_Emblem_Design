# 📈 Level-Up Growth System

Defines how characters gain stats when leveling up, based on their class and personal growth rates.

---

## 🧬 Growth Rates

Each character and class has a growth rate for each stat:

```json
{
  "hp": 60,
  "str": 45,
  "mag": 20,
  "skl": 40,
  "spd": 35,
  "def": 30,
  "res": 25,
  "lck": 50
}
```

- Values are percentages (0–100%)
- Rolled once per stat when leveling up

---

## 📘 Stat Growth Formula

```ts
levelUp():
  for each stat:
    if random(0, 100) < growth[stat]:
      stat += 1
```

- Some characters may gain multiple stats per level
- Growth can be modified by class or item bonus

---

## 🏷️ Class Growth Modifiers

| Class          | HP | STR | MAG | SPD | DEF | RES | LCK |
|----------------|----|-----|-----|-----|-----|-----|-----|
| Knight         | +20| +10 | 0   | -5  | +20 | 0   | 0   |
| Mage           | +5 | 0   | +20 | +10 | -5  | +10 | 0   |
| Thief          | +5 | +5  | 0   | +15 | 0   | 0   | +10 |

---

📌 Encourages unique growth per character + class synergy