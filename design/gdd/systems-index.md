# Systems Index

Every game system, its GDD, build priority and status. Priority comes from the
original development roadmap ([production/roadmap.md](../../production/roadmap.md)).

**Status of all GDDs: `Draft (imported)`.** They were merged from the original
design files and keep their content. Sections the framework standard expects but
the originals did not have (Player Fantasy, Edge Cases, Tuning Knobs, Acceptance
Criteria) are still to be written — use `/design-system <file>` one system at a
time, starting with Foundation.

| Layer | System | GDD | Category | Priority | Status |
|-------|--------|-----|----------|----------|--------|
| Foundation | Character data model | [character-data.md](character-data.md) | Core | High | Draft (imported) |
| Foundation | Game loop & battle flow | [game-loop.md](game-loop.md) | Core | High | Draft (imported) |
| Foundation | Terrain, movement & maps | [terrain-and-maps.md](terrain-and-maps.md) | Gameplay | High | Draft (imported) |
| Core | Combat | [combat-system.md](combat-system.md) | Gameplay | High | Draft (imported) |
| Core | Weapons | [weapons.md](weapons.md) | Gameplay | High | Draft (imported) |
| Core | Skills | [skill-system.md](skill-system.md) | Gameplay | High | Draft (imported) |
| Core | Enemy AI | [enemy-ai.md](enemy-ai.md) | Gameplay | High | Draft (imported) |
| Feature | Classes & promotion | [class-system.md](class-system.md) | Progression | Medium | Draft (imported) |
| Feature | Level-up & growth | [progression.md](progression.md) | Progression | Medium | Draft (imported) |
| Feature | Items & inventory | [items-and-inventory.md](items-and-inventory.md) | Economy | Medium | Draft (imported) |
| Feature | Status effects | [status-effects.md](status-effects.md) | Gameplay | Medium | Draft (imported) |
| Feature | Save / load | [save-load.md](save-load.md) | Persistence | Medium | Draft (imported) |
| Feature | Map events & triggers | [map-events.md](map-events.md) | Gameplay | Low | Draft (imported) |
| Polish | Turn-order timeline (optional) | [turn-order-timeline.md](turn-order-timeline.md) | Gameplay | Low | Draft (imported) |

Not yet designed (named in the roadmap): Cutscene / dialogue, Audio, Animation / VFX, HUD & menus.

Approved changes waiting to be written in: see the note at the top of each affected GDD and the [differentiation review](../reviews/2026-11-21-gameplay-differentiation.md).

Cross-cutting decisions: [open-questions.md](open-questions.md) (43 items).
