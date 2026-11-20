# Development Roadmap

> From: `SRPG_Development_Roadmap.md`.

Priority: **High** = needed for the first prototype · **Medium** = right after the core loop · **Low** = content / polish.

## Phase 1 — Core gameplay (High)

| Module | Notes | GDD |
|--------|-------|-----|
| Game loop (turn system) | Player → Enemy → Environment | game-loop |
| Character template | Stats, inventory, skills, position | character-data |
| Movement | Grid move + reachable-tile highlight | terrain-and-maps |
| Combat resolver | Hit / crit / damage | combat-system |
| Skill execution | Active skills, targeting, effects | skill-system |
| Basic AI | Enemy phase with basic targeting | enemy-ai |
| Map loader & terrain | Load terrain, apply bonuses | terrain-and-maps |
| UI: action menu | Move, Attack, Skill, Item | — |

## Phase 2 — Systems & progression (Medium)

Promotion · EXP & level up · Inventory · Buffs/debuffs · Save/load · UI: stats & status panel.

## Phase 3 — Content & UX (Low)

Map events & triggers · Class skill tree UI · Timeline (optional) · Cutscenes / dialogue ·
Audio (BGM / SFX) · Animation / VFX.

## Suggested first sprint

1. Grid map + movement
2. Character rendering + stat overlay
3. Basic attack (no skills) + damage resolve
4. One enemy AI type (Aggressive)
5. One map: 3 player units vs 5 enemies
6. Win condition: defeat all

Tips: keep modules standalone; store static data (units, maps, classes, skills) as JSON; keep the prototype small.
