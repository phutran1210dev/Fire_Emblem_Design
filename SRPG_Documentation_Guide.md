# 📚 SRPG Game Design Documentation – Reading Guide

This document provides an organized reading order for all SRPG design files. It helps developers and designers understand the system step-by-step.

---

## 1. 🎮 Gameplay Overview

| File | Description |
|------|-------------|
| `Gameplay_Loop.md` | Describes the main turn-based loop: Player → Enemy → Environment → Victory Check |
| `Victory_Conditions.md` | Lists mission types and win/lose scenarios |

---

## 2. 🧬 Character & Class System

| File | Description |
|------|-------------|
| `CharacterClass_Tree.md` | Full class progression from Tier 1 to Tier 5 |
| `Promotion_Flow.md` | How class promotion works, requirements, skill unlocks |
| `Promotion_Stats_Scaling.md` | Stat bonuses gained per promotion tier |
| `ClassSkillTree.md` | Skills each class learns by level and tier |
| `LevelUp_Growth_System.md` | Stat growth chance per level |
| `Character_Template.md` | Complete JSON schema for a character |

---

## 3. ⚔️ Combat System

| File | Description |
|------|-------------|
| `Combat_Mechanics.md` | Hit/Crit/Damage formulas, triangle advantage, weaknesses |
| `Combat_Flow.md` | Step-by-step combat resolution flow |
| `StatusEffects.md` | Buffs, debuffs, durations, resistances |
| `Skill_System.md` | Active/Passive/Reaction skill logic + JSON structure |
| `Skill_Resolution_Flow.md` | Skill casting and execution steps |

---

## 4. 🗡️ Weapons & Items

| File | Description |
|------|-------------|
| `WeaponClass_Tree.md` | List of weapon types, stats, pros/cons |
| `Character ↔ Weapon Mapping.md` | Which class uses which weapons |
| `Item_System.md` | Healing, buffs, debuffs, key items, gear |

---

## 5. 🧠 AI & Enemy Behavior

| File | Description |
|------|-------------|
| `Enemy_AI.md` | AI logic, behavior types, targeting rules, scripted events |

---

## 6. 🗺️ Map & Event Triggers

| File | Description |
|------|-------------|
| `Map_Terrain_Bonus.md` | Terrain types and their combat effects |
| `Map_Design_Examples.md` | Sample map layouts and enemy placement |
| `Map_Event_Trigger_Flow.md` | Event activation based on tiles and triggers |
| `Diagram_Summary.md` | Overview of all system flowcharts (PNG format) |

---

## 7. 🧾 UI & Technical Systems

| File | Description |
|------|-------------|
| `Inventory_UI_Design.md` | Inventory structure, equip/use/trade logic |
| `Save_Load_System.md` | Save data schema and autosave handling |

---

## 8. 🧠 Optional Systems

| File | Description |
|------|-------------|
| `Turn_Order_Timeline.md` | Optional FFTactics-style initiative system |

---

## ✅ Summary

You now have:
- A complete class and combat system
- AI logic, item/skill system, and map trigger design
- Flowcharts for key gameplay systems
- JSON templates to begin development

Use this documentation to:
- Prototype your first battle map
- Assign tasks across teams (UI, AI, Map, Combat)
- Translate directly into Unity, Godot, or Canvas/JS projects

📌 You are fully ready to begin development!