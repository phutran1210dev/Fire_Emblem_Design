# 🏁 Victory & Defeat Conditions

Defines possible mission goals and how they're evaluated.

---

## 🎯 Victory Conditions

| Type           | Description                          |
|----------------|--------------------------------------|
| Rout Enemies   | Defeat all enemy units               |
| Boss Kill      | Defeat specific target               |
| Seize          | Move unit to goal tile               |
| Defend         | Survive X turns                      |
| Escape         | All allies reach destination         |
| Rescue         | Protect and escort an NPC            |
| Puzzle         | Fulfill specific goal (non-combat)   |

---

## 💀 Defeat Conditions

| Condition       | Description                       |
|------------------|-----------------------------------|
| Player Wiped     | All units defeated                |
| Main Hero Dies   | Specific unit death               |
| NPC Dies         | Objective unit defeated           |
| Turn Limit       | Exceeded max turns allowed        |

---

## ✅ Evaluation Logic

```ts
if goal === 'seize' and unit.position === gate:
  battleWin()
```

---

📌 Clear goals support strategic diversity