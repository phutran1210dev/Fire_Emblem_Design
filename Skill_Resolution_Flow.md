# ✨ Skill Resolution Flow

This document outlines the sequence of actions and checks when a skill is used in battle.

---

## 🔄 Skill Use Flow

```text
Skill Activated
↓
Check Skill Type
↓
Target Selection
↓
Check MP/SP Cost
↓
Apply Primary Effect (Damage / Heal / Buff / Debuff)
↓
Trigger Secondary Effects (Status / AoE / Chain)
↓
Apply Cooldown / Cost
↓
Skill Ends
```

---

## 🧠 Skill Types

| Type         | Description                              |
|--------------|------------------------------------------|
| Active       | Used during player's turn                |
| Passive      | Always active, no cost                   |
| Reaction     | Triggered by damage or condition         |
| Terrain-Based| Activates based on location              |

---

## 🎯 Targeting Logic

| Target Type | Description               |
|-------------|---------------------------|
| Self        | Only caster is affected   |
| Ally        | Heals, buffs              |
| Enemy       | Damage, debuffs           |
| AoE         | Area of Effect (multi-tile)|
| Conditional | Based on HP, distance, etc.|

---

## 💸 Cost & Cooldown

- **MP / SP Cost**: Resource used to activate skill
- **Cooldown**: Turns until skill can be used again
- **Charge Skill**: May take multiple turns to activate

---

## ⚙️ Primary Effect Application

- For offensive skills: calculate damage like a normal attack
- For healing: restores HP up to max
- For buffs/debuffs: apply stat modifiers for duration

---

## 🔁 Secondary Effects

| Type         | Description                       |
|--------------|-----------------------------------|
| Status       | Stun, Poison, Sleep, etc.         |
| AoE Chain    | Hits multiple nearby enemies      |
| Trigger Skill| Activates another skill or passive|

---

## 📘 Example

> **Skill:** Flame Nova  
> **Type:** Active  
> **Cost:** 8 MP  
> **Effect:** Fire AoE (2 tiles), 10 base damage  
> **Status Chance:** 30% Burn

---

## ✅ Summary

| Phase              | Action                             |
|--------------------|-------------------------------------|
| Activation         | Triggered by player or event        |
| Cost Check         | Validates resources                 |
| Target Resolution  | Determines who is affected          |
| Effect Resolution  | Applies damage, status, healing     |
| Cooldown / End     | Prevents reuse for X turns          |

📌 Skill design allows creative combos, utility, and power scaling.