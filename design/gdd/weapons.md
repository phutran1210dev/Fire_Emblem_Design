# Weapons

> From: `WeaponClass_Tree.md`. Class ↔ weapon mapping lives in `class-system.md`.

> **Approved change (2026-11-21, [review](../reviews/2026-11-21-gameplay-differentiation.md)):** Tomes get an element (fire / ice / thunder / wind). Weight lowers Attack Speed: AS = SPD − max(0, weight − STR/2).
> Not yet written into the sections below — next `/design-system` pass.

## Overview

Nine weapon types. Sword / Axe / Lance form the triangle (`combat-system.md`);
the others have niche strengths.

## Detailed Rules

| Type | Role | Strength | Weakness |
|------|------|----------|----------|
| Sword | Balanced melee | Beats Axe | Weak to Lance |
| Axe | High power, low accuracy | Beats Lance | Weak to Sword |
| Lance | Reach, defensive | Beats Sword | Weak to Axe |
| Bow | Long-range physical | Strong vs flying | Vulnerable in melee |
| Dagger | Fast, high crit | Good vs low DEF | Weak to heavy armour |
| Tome | Magic offense | Targets RES, not DEF | High RES, anti-magic |
| Staff | Healing & support | — | Cannot attack |
| Spear | Advanced lance type | Strong vs cavalry | Heavy, costly |
| Arcane | Legendary spells | High power | Rare, needs high proficiency |

### Base stat ranges

| Type | Might | Hit | Crit | Weight |
|------|-------|-----|------|--------|
| Sword | 5–10 | 85% | 5% | 2–4 |
| Axe | 9–15 | 70% | 0–5% | 4–7 |
| Lance | 7–12 | 75% | 0% | 3–6 |
| Bow | 5–11 | 80% | 5–10% | 2–4 |
| Dagger | 4–8 | 90% | 15% | 1–3 |
| Tome | 6–12 | 80% | 5% | 3–5 |
| Staff | — | 100% | — | 1–2 |
| Spear | 10–16 | 70% | 5% | 5–7 |
| Arcane | 12–18 | 85% | 10% | 6–8 |

## Dependencies

`combat-system.md`, `class-system.md`, `items-and-inventory.md`.

## Open Questions

[open-questions.md](open-questions.md): Q7 Spear vs Lance, Q20 what Weight does,
Q21 attack ranges per weapon, Q22 durability, Q23 individual weapon list (Iron Sword, Steel Lance...).
