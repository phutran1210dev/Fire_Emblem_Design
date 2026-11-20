# Combat System

> Merged from: `Combat_Mechanics.md`, `Combat_Flow.md`, `Diagram_Summary.md` (section 2).
> Diagram: [combat-flowchart.png](../diagrams/combat-flowchart.png)

> **Approved change (2026-11-21, [review](../reviews/2026-11-21-gameplay-differentiation.md)):** P2 Pincer (+15% hit, +2 dmg, no counter, +1 Momentum); counter if in range; follow-up AS ≥ foe AS + 4; combat forecast UI; clamp hit/crit 0–100; crit ×2.5 or Dagger crit 10%. P3 Momentum gains from combat.
> Not yet written into the sections below — next `/design-system` pass.

## Overview

One attacker strikes one target. The result depends on weapon stats, the
attacker's and defender's stats, weapon proficiency, the weapon triangle and
class weaknesses. Hit and crit are random rolls.

## Detailed Rules

### Combat sequence

```text
Start combat (player or enemy)
↓ Check range to target — move into range if needed; cancel if unreachable
↓ Choose action (Attack / Skill / Item)
↓ Calculate Hit / Crit / Damage
↓ Trigger reaction skills (counter, Miracle, ...)
↓ Apply damage
↓ Apply status effects (weapon / skill properties)
↓ Check defeat — HP ≤ 0 → unit removed from map
↓ Grant EXP / SP
↓ End combat
```

### Weapon triangle

| Attacker weapon | Strong against | Bonus |
|-----------------|----------------|-------|
| Sword | Axe | +15% Hit, +3 damage |
| Axe | Lance | +15% Hit, +3 damage |
| Lance | Sword | +15% Hit, +3 damage |

Only the attacker with the advantaged weapon gets the bonus. It stacks with class weakness.

### Class weakness

| Class type | Weak against | Bonus damage |
|------------|--------------|--------------|
| Cavalry | Spear, anti-cavalry weapons | +50% |
| Armored (Knight) | Magic, Hammer | +50% |
| Flying (Pegasus) | Bow, Wind Tome | +100% |
| Thief / Assassin | Heavy weapons | +20% |
| Mage | Silence, anti-magic | +30% |

### Weapon proficiency

Ranks: `E(0) → D(1) → C(2) → B(3) → A(4) → S(5) → S+(6)`.
Each weapon has a `requiredLevel`; each character has a rank per weapon type.

### Resolution order

1. Check weapon type and triangle bonus
2. Compute base damage
3. Apply class weakness multiplier
4. Roll hit — on miss, `damage = 0`
5. Roll crit — on crit, `damage *= 3`
6. Subtract damage from `defender.currentHP`
7. Clamp HP to `≥ 0`

### EXP

Granted for damage dealt or a kill; extra for high-tier or boss units.
(No formula yet — see open questions.)

## Formulas

```ts
// Damage
physical = (weapon.might + attacker.STR) - defender.DEF
magic    = (weapon.might + attacker.MAG) - defender.RES
damage   = base + triangleDamage                 // +3 if advantaged
if (defender.weakTo(weapon)) damage += floor(damage * bonusMultiplier)
finalDamage = max(0, damage)

// Proficiency (only if proficiency >= required)
profBonusHit  = (proficiencyLevel - requiredLevel) * 5   // %
profBonusCrit = (proficiencyLevel - requiredLevel) * 5   // %
// e.g. weapon needs C(2), unit has A(4) → +10% hit, +10% crit

// Hit
hitRate        = weapon.hit + attacker.SKL * 2 + profBonusHit + triangleHit
avoid          = defender.SPD * 2 + defender.LCK
finalHitChance = hitRate - avoid                 // roll 0–100 ≤ chance → hit

// Crit
critChance = weapon.crit + attacker.SKL / 2 - defender.LCK + profBonusCrit
critDamage = damage * 3
```

| Variable | Source |
|----------|--------|
| `weapon.might / hit / crit` | `weapons.md` |
| `STR, MAG, SKL, SPD, DEF, RES, LCK` | `character-data.md` |
| terrain avoid / DEF / RES | `terrain-and-maps.md` |

## Dependencies

`weapons.md`, `character-data.md`, `class-system.md` (weakness types),
`terrain-and-maps.md`, `skill-system.md` (reaction skills), `status-effects.md`,
`progression.md` (EXP).

## Open Questions

[open-questions.md](open-questions.md): Q3 counter-attacks, Q4 follow-up (double) attacks,
Q5 terrain in hit formula, Q6 Hammer / Wind Tome / heavy weapons undefined,
Q7 Spear vs Lance, Q8 EXP formula, Q9 clamp hit/crit to 0–100.
