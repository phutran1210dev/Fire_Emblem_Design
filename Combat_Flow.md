# ⚔️ Combat Flow

This document outlines the detailed step-by-step process of a combat interaction in the SRPG system.

---

## 🎯 Combat Sequence Overview

```text
Start Combat (Player or Enemy)
↓
Check Range to Target
↓
Move to Attack Range (if needed)
↓
Choose Action (Attack / Skill / Item)
↓
Calculate Hit / Crit / Damage
↓
Trigger Reaction Skills (if any)
↓
Apply Damage to Target
↓
Apply Status Effects (if applicable)
↓
Check if Target is Defeated
↓
Gain EXP / Skill Points
↓
End Combat Phase
```

---

## 🔢 Step Breakdown

### 1. Check Range
- If not in range, unit moves into attack range.
- If unreachable, combat is cancelled.

### 2. Choose Action
- Player picks an action: Weapon attack, skill use, or item.
- Some skills/items may target multiple units.

### 3. Calculate Hit / Crit
- Uses attacker SKL, LCK, weapon stats vs. target's SPD, LCK.
- Applies weapon triangle or proficiency bonuses.

### 4. Reaction Skills
- Defender may counterattack or trigger passive skills like “Miracle” or “Counter”.

### 5. Apply Damage
- Damage = (Weapon Might + STR/MAG) - Target DEF/RES
- Clamped to minimum 0

### 6. Status Effects
- Check skill or weapon properties for poison, stun, debuff, etc.

### 7. Check Defeat
- If HP ≤ 0 → target is marked dead and removed from map

### 8. Grant EXP
- Based on damage dealt or kill
- Extra EXP for defeating high-tier or boss units

---

## ✅ Summary Table

| Step           | Action                          |
|----------------|----------------------------------|
| Range Check    | Can unit reach the target?       |
| Move & Select  | Pick skill, weapon, or item      |
| Calculation    | Hit, crit, damage rolled         |
| Resolution     | Damage applied, status triggered |
| Aftermath      | EXP gained, death handled        |

📌 This system ensures fair and dynamic combat in every encounter.