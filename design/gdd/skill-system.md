# Skill System

> Merged from: `Skill_System.md`, `Skill_Resolution_Flow.md`, `ClassSkillTree.md`,
> `Diagram_Summary.md` (section 5). Diagram: [skill-resolution-flowchart.png](../diagrams/skill-resolution-flowchart.png)

> **Approved change (2026-11-21, [review](../reviews/2026-11-21-gameplay-differentiation.md)):** P3 Momentum: shared team pool 0–10 replaces MP/SP. Active skills cost 2–6, Tier 5 ultimate costs 10; passives and reactions free; cooldowns stay.
> Not yet written into the sections below — next `/design-system` pass.

## Overview

Skills are learned through levels, promotion, scrolls and events. A unit can
equip up to 4. Skills are Active, Passive, Reaction, Terrain-based or
Class-specific, and have rarity, cost, cooldown and targeting.

## Detailed Rules

### Categories

| Type | When it works | Examples |
|------|---------------|----------|
| Active | Used manually on the unit's turn | Power Strike, Heal, Fireball |
| Passive | Always on once learned, no cost | Evasion Boost, Crit Boost |
| Reaction | Triggers on a condition | Counterattack, Miracle |
| Terrain-based | Active on certain tiles | Forest Camouflage |
| Class-specific | Unique to a class or tier | Pegasus Blessing, Mage Focus |

### Rarity

| Rarity | Description | Example |
|--------|-------------|---------|
| Common | Small effect, widely available | +5% Crit |
| Rare | Moderate or limited use | Counterattack |
| Epic | High utility / strong passive | Nullify Terrain Penalty |
| Legendary | Class-defining | Heal All, Dragon Wrath |

### Learning & equipping

- Learned by level-up, promotion, scrolls/tomes, events.
- Auto-learned or bought with **SP** (gained per combat action or battle; cost by tier).
- Max **4** equipped (tunable).

### Targeting

| Target | Examples |
|--------|----------|
| Self | Heal, buff |
| Ally | Heal, revive, buff |
| Enemy | Damage, debuff |
| AoE | Flame Circle, Rally |
| Conditional | Based on HP, distance, etc. |

### Cost & cooldown

| Field | Meaning |
|-------|---------|
| Cost | MP, SP or HP |
| Cooldown | Turns before reuse |
| Duration | Turns an effect lasts |
| Charge | Some skills take several turns to fire |

### Resolution flow

```text
Skill activated → check type → select target → check MP/SP cost
→ apply primary effect (damage / heal / buff / debuff)
→ secondary effects (status, AoE chain, trigger another skill)
→ apply cooldown & pay cost → end
```

- Offensive skills compute damage like a normal attack (`combat-system.md`).
- Heals restore HP up to max. Buffs/debuffs apply stat modifiers for a duration.

Example — **Flame Nova**: Active, 8 MP, fire AoE radius 2, 10 base damage, 30% Burn.

### Data examples

```json
{ "id": "fireball", "name": "Fireball", "type": "active",
  "range": 2, "power": 12, "cost": 3, "effect": "magic_damage", "cooldown": 0 }

{ "id": "dodge_plus_10", "name": "Evasion Boost", "type": "passive",
  "effect": "increase_avoid", "value": 10 }

{ "id": "miracle", "name": "Miracle", "type": "reaction",
  "trigger": "lethal_damage", "effect": "survive_with_1hp", "chance": 20 }
```

### Class skill tree example (Mercenary line)

| Tier | Level | Skill | Type | Effect |
|------|-------|-------|------|--------|
| 1 | 5 | Quick Slash | Active | Light sword attack |
| 1 | 10 | Counter Posture | Passive | Counter when hit |
| 2 | Promo | Brave Heart | Passive | +2 STR if HP < 50% |
| 3 | 5 | Rally Speed | Active | +SPD to nearby allies |
| 4 | 10 | Sword Focus | Passive | +10 Hit/Crit with swords |
| 5 | Promo | Godstrike | Active | Massive AoE slash |

```ts
if (unit.class === 'Hero' && unit.level >= 5) unlock('Brave Heart')
```

## Dependencies

`combat-system.md`, `status-effects.md`, `class-system.md`, `character-data.md`.

## Open Questions

[open-questions.md](open-questions.md): Q11 promotion skill lists, Q17 MP/SP pool,
Q24 Brave Heart unlock (promo vs Lv 5), Q25 "Burn" is not in status-effects.
