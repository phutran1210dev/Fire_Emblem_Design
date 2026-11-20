# Level-Up & Growth

> Merged from: `LevelUp_Growth_System.md`, parts of `Character_Template.md`.

> **Approved change (2026-11-21, [review](../reviews/2026-11-21-gameplay-differentiation.md)):** 10 levels per tier (promotion about every 5 chapters). Promotion requires Lv 10 + Oath Sigil.
> Not yet written into the sections below — next `/design-system` pass.

## Overview

Units earn EXP; at 100 EXP they level up and roll each stat against a growth
rate. Growth = personal rate + class modifier. Levels run 1–20 per tier.

## Detailed Rules

- `level`: 1–20 per tier; `exp`: 0–100 per level.
- On level up, each stat is rolled once; several stats can rise in one level.
- Growth can be modified by class or items.

Example personal growth rates (%):

```json
{ "hp": 60, "str": 45, "mag": 20, "skl": 40, "spd": 35, "def": 30, "res": 25, "lck": 50 }
```

Class growth modifiers (added to personal rate, percentage points):

| Class | HP | STR | MAG | SPD | DEF | RES | LCK |
|-------|----|-----|-----|-----|-----|-----|-----|
| Knight | +20 | +10 | 0 | -5 | +20 | 0 | 0 |
| Mage | +5 | 0 | +20 | +10 | -5 | +10 | 0 |
| Thief | +5 | +5 | 0 | +15 | 0 | 0 | +10 |

## Formulas

```ts
levelUp(unit):
  for stat in stats:
    growth = unit.growth[stat] + unit.class.growthMod[stat]
    if random(0, 100) < growth: unit[stat] += 1
```

## Dependencies

`combat-system.md` (EXP source), `class-system.md` (caps, promotion at Lv 20).

## Open Questions

[open-questions.md](open-questions.md): Q8 EXP formula, Q15 SKL missing from growth-mod table,
Q16 stat caps per tier.
