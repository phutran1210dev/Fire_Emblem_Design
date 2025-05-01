# 🔁 Battle Flow System

This document outlines the full turn-based combat loop and action resolution in the SRPG game.

---

## 🔄 Global Turn Structure

```text
Turn 1:
  - Player Phase
  - Enemy Phase
  - Ally Phase (optional NPCs)
  - Environment Phase (traps, events, reinforcements)
```

Each **battle turn** consists of multiple **phases**. The order repeats each round until a win/loss condition is met.

---

## 👥 Phase Breakdown

### 🧍 Player Phase

- Player controls all units
- Can move, attack, use skills/items
- Each unit can act once per turn

### 💀 Enemy Phase

- AI-controlled units act
- Based on priority, threat, or aggression
- May retreat or use skills strategically

### 🫱 Ally Phase

- Friendly NPCs may act autonomously
- Useful for escort or defend missions

### 🌋 Environment Phase

- Traps, events, weather, reinforcements, etc.
- Tile-based effects are triggered here

---

## 🧠 Unit Action Flow (Per Character)

```text
Start Turn →
  Can Move? → Move →
    Can Act (Skill/Item/Attack)? →
      Perform Action →
        End Turn
```

- Units **cannot act again** after attacking or using an active skill
- Exceptions: Skills like "Canto" allow movement after action

---

## 🎯 Action Types

| Action       | Description                        |
|--------------|------------------------------------|
| Move         | Based on unit's movement stat      |
| Attack       | Weapon-based attack (melee/range)  |
| Skill        | Active or reaction-based ability   |
| Item         | Use consumable or equip gear       |
| Wait         | Skip action and end turn           |
| Talk         | Special interaction (recruit, etc.)|
| Rescue       | Carry another unit (if allowed)    |

---

## 💢 Combat Interaction Steps

1. **Initiate** attack → check range & action validity
2. **Determine hit/crit/dodge** using stats + terrain
3. **Apply damage** and trigger effects
4. **Check for death, passive triggers, counters**
5. **Update EXP**, trigger level up if needed

---

## ⚠️ End of Turn Events

- HP regen (e.g., terrain, passive)
- Poison / status effect ticks
- Buff/debuff durations updated
- Enemy reinforcements or story triggers

---

## 🏆 Victory & Defeat Conditions

| Type             | Examples                         |
|------------------|----------------------------------|
| Rout Enemies     | Defeat all enemy units           |
| Seize Point      | Occupy specific tile             |
| Defend Turns     | Survive for X turns              |
| Escape           | All player units must reach tile |
| Boss Defeat      | Defeat specific enemy            |
| Protect Ally     | Prevent key unit from dying      |

---

📌 Clear battle flow ensures fair & predictable strategy.