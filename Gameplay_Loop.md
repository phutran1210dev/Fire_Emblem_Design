# 🔁 Gameplay Loop

This document describes the core turn-based flow in the SRPG system.

---

## 🧩 Turn Structure Overview

Each full round consists of the following phases:

1. **Player Phase**
   - Player units take turns
   - Units can move, attack, use skills, or items

2. **Enemy Phase**
   - AI-controlled units act based on targeting logic
   - Aggressive, defensive, or scripted behavior

3. **Ally Phase** *(optional)*
   - Friendly NPC units act
   - May provide support or follow preset paths

4. **Environment Phase**
   - Traps, healing tiles, reinforcements, weather effects
   - Event triggers or conditional spawns

---

## 📊 Gameplay Loop Order

```text
Start Game / Load Save
↓
Preparation Phase
↓
Player Phase
→ Move / Act / Skill / Item
↓
Enemy Phase
→ AI Movement / Attack
↓
Environment Phase
→ Traps / Regen / Reinforcements
↓
Victory / Defeat Check
↓
If no condition met → Next Turn
↓
Repeat Player Phase
```

---

## 🏁 Victory / Defeat Conditions

Victory:
- Defeat all enemies
- Seize objective tile
- Survive X turns
- Rescue or Escape missions

Defeat:
- Player wiped out
- Main hero dies
- Objective NPC dies
- Exceed turn limit

---

## ✅ Summary

| Phase           | Key Actions                        |
|------------------|------------------------------------|
| Player Phase     | Player moves and attacks           |
| Enemy Phase      | AI activates per behavior script   |
| Environment      | Events, traps, map-based effects   |
| Evaluation       | Check if game ends                |

📌 This loop repeats until a win or loss condition is met.