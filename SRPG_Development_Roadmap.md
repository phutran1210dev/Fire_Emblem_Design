# 🚀 SRPG Development Roadmap

This document outlines the suggested module implementation order and priority when starting development of your SRPG game.

---

## 🎯 Prioritization Key

| Priority | Description                  |
|----------|------------------------------|
| 🔴 High  | Must-have to start prototype |
| 🟡 Medium| Needed soon after core loop  |
| 🟢 Low   | Optional or polish phase     |

---

## 🧱 Phase 1: Core Gameplay Systems (🔴 High Priority)

| Module                 | Priority | Notes                                       |
|------------------------|----------|---------------------------------------------|
| Game Loop (Turn System)| 🔴 High  | Player → Enemy → Environment phases         |
| Character Template     | 🔴 High  | Base stats, inventory, skills, position     |
| Movement System        | 🔴 High  | Grid-based move + valid tile highlight      |
| Combat Resolver        | 🔴 High  | Hit/Crit/Damage calculation & execution     |
| Skill Execution Engine | 🔴 High  | Active skills, targeting, effects           |
| AI System (Basic)      | 🔴 High  | Enemy phase logic with basic targeting      |
| Map Loader & Terrain   | 🔴 High  | Load terrain and apply bonuses              |
| UI: Action Menu        | 🔴 High  | Choose Move, Attack, Skill, Item            |

---

## 🧠 Phase 2: Systems & Progression (🟡 Medium Priority)

| Module                    | Priority | Notes                                     |
|---------------------------|----------|-------------------------------------------|
| Promotion System          | 🟡 Medium| Class tier promotion, stat update         |
| EXP & Level Up System     | 🟡 Medium| Gain EXP and roll stat growth             |
| Inventory Management      | 🟡 Medium| Equip, use, trade, and discard items      |
| Buff/Debuff System        | 🟡 Medium| Status effects, resistances               |
| Save/Load System          | 🟡 Medium| Load and persist game state               |
| UI: Stats & Status Panel  | 🟡 Medium| Display unit info, conditions             |

---

## 🗺️ Phase 3: Content & UX (🟢 Low Priority)

| Module                      | Priority | Notes                                   |
|-----------------------------|----------|-----------------------------------------|
| Map Events & Triggers       | 🟢 Low   | Hidden events, reinforcements, scripts |
| Class Skill Tree UI         | 🟢 Low   | View/assign skills per class            |
| Timeline System (optional)  | 🟢 Low   | FFT-style turn order display            |
| Cutscene / Dialogue Engine  | 🟢 Low   | Narrative moments                       |
| Audio: BGM / SFX            | 🟢 Low   | Music, skill sounds, attack SFX         |
| Animation / VFX Integration | 🟢 Low   | Skill, move, attack animations          |

---

## 🧪 Suggested First Sprint

1. Grid-based map + movement
2. Character rendering + stat overlay
3. Basic attack (no skill) + damage resolve
4. One enemy AI type (Aggressive)
5. One map with 3 units vs 5 enemies
6. Simple win condition (defeat all)

---

## 📌 Tips

- Build each module standalone but modular
- Use JSON for static data (unit, map, class, skill)
- Keep prototype small to validate system flow

---

🎉 You’re now ready to plan and execute development in manageable chunks!