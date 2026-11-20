# SRPG Design Wiki

A grid-based tactical RPG with a 5-tier class system, weapon triangle,
phase-based turns, terrain bonuses and skill builds.

## Where to start

1. [Systems index](gdd/systems-index.md) — every system, priority, status
2. [Game loop](gdd/game-loop.md) — how a battle plays
3. [Combat](gdd/combat-system.md) — all the formulas
4. [Open questions](gdd/open-questions.md) — decisions still needed
5. [Roadmap](../production/roadmap.md) — build order and first sprint

## Systems

| Area | Pages |
|------|-------|
| Battle | [Game loop](gdd/game-loop.md) · [Combat](gdd/combat-system.md) · [Turn-order timeline (optional)](gdd/turn-order-timeline.md) |
| Units | [Character data](gdd/character-data.md) · [Classes & promotion](gdd/class-system.md) · [Level-up & growth](gdd/progression.md) |
| Equipment | [Weapons](gdd/weapons.md) · [Items & inventory](gdd/items-and-inventory.md) |
| Abilities | [Skills](gdd/skill-system.md) · [Status effects](gdd/status-effects.md) |
| World | [Terrain & maps](gdd/terrain-and-maps.md) · [Map events](gdd/map-events.md) · [Enemy AI](gdd/enemy-ai.md) |
| Tech | [Save / load](gdd/save-load.md) |

## Diagrams

| Flow | File |
|------|------|
| Game loop | [game-loop-flowchart.png](diagrams/game-loop-flowchart.png) |
| Combat | [combat-flowchart.png](diagrams/combat-flowchart.png) |
| Promotion | [promotion-flowchart.png](diagrams/promotion-flowchart.png) |
| Map events | [map-event-trigger-flowchart.png](diagrams/map-event-trigger-flowchart.png) |
| Skill resolution | [skill-resolution-flowchart.png](diagrams/skill-resolution-flowchart.png) |

Proposed flows from the [2026-11-21 differentiation review](reviews/2026-11-21-gameplay-differentiation.md)
(interactive HTML, open in a browser; approved 2026-11-21, being written into the GDDs):

| Flow | File |
|------|------|
| Combat resolution (Pincer, counter, follow-up, Momentum) | [combat-resolution.html](diagrams/combat-resolution.html) |
| Battle round loop (living battlefield, instant win) | [battle-round.html](diagrams/battle-round.html) |
| Unit progression (Oath branches, Wounded / Classic) | [unit-progression.html](diagrams/unit-progression.html) |

## Reviews

- [2026-11-21 · Gameplay differentiation](reviews/2026-11-21-gameplay-differentiation.md): 4 proposed pillars + gameplay gaps

## Where the old files went

| Old file | New page |
|----------|----------|
| Gameplay_Loop, BattleFlow, Victory_Conditions | gdd/game-loop.md |
| Combat_Mechanics, Combat_Flow | gdd/combat-system.md |
| CharacterClass_Tree, Promotion_Flow, Promotion_Stats_Scaling, Character_Weapon Mapping | gdd/class-system.md |
| LevelUp_Growth_System | gdd/progression.md |
| Character_Template | gdd/character-data.md |
| WeaponClass_Tree | gdd/weapons.md |
| Skill_System, Skill_Resolution_Flow, ClassSkillTree | gdd/skill-system.md |
| StatusEffects | gdd/status-effects.md |
| Item_System, Inventory_UI_Design | gdd/items-and-inventory.md |
| Enemy_AI | gdd/enemy-ai.md |
| Map_Terrain_Bonus, Map_Design_Examples | gdd/terrain-and-maps.md |
| Map_Event_Trigger_Flow | gdd/map-events.md |
| Save_Load_System | gdd/save-load.md |
| Turn_Order_Timeline | gdd/turn-order-timeline.md |
| SRPG_Development_Roadmap | ../production/roadmap.md |
| SRPG_Documentation_Guide | this page |
| Diagram_Summary | split into each system page + the Diagrams table above |

The originals are in git history (commit `42e366c`).
