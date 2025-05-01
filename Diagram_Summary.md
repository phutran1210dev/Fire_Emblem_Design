# 📊 Gameplay Flowcharts (Diagram Summary)

This document summarizes all gameplay flowcharts as diagrams for the SRPG system. Each section represents a different gameplay mechanic or system flow.

---

## 1. 🌀 General Gameplay Loop

**Phases:**
- Player Phase → Enemy Phase → Environment Phase
- Each unit acts once per phase
- Victory / Defeat checked at the end of each turn

---

## 2. ⚔️ Combat Flow

**Steps:**
1. Check range & move if needed
2. Choose action (attack, skill, item)
3. Calculate hit, crit, and damage
4. Apply damage and status effects
5. Check if the target is defeated
6. Grant EXP and end combat

---

## 3. 🧱 Promotion Flow

**Conditions:**
- Unit must reach max level
- Must possess promotion item
- Player chooses new class
- Stats and tier updated
- New class skills unlocked

---

## 4. 🧩 Map Event Trigger Flow

**Trigger logic:**
- Events activated by entering zones
- Event types: enemy spawn, open path, give item, start dialogue
- All events set internal flags
- Resumes battle after effect

---

## 5. ✨ Skill Resolution Flow

**Skill casting logic:**
- Player activates skill
- System checks type and target
- Validates resource cost (MP/SP)
- Applies main effect (damage/heal/buff)
- Triggers secondary effect (status, AoE)
- Applies cooldown and ends skill

---

## 📁 Flowchart Files

| Diagram Name             | File Link                             |
|--------------------------|----------------------------------------|
| Gameplay Loop            | `Game_Loop_Flowchart.png`              |
| Combat Flow              | `Combat_Flowchart.png`                 |
| Promotion Flow           | `Promotion_Flowchart.png`              |
| Map Event Trigger Flow   | `Map_Event_Trigger_Flowchart.png`      |
| Skill Resolution Flow    | `Skill_Resolution_Flowchart.png`       |

---

📌 These diagrams help visualize core systems before development.