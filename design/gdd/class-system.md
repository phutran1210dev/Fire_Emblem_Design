# Class & Promotion System

> Merged from: `CharacterClass_Tree.md`, `Promotion_Flow.md`, `Promotion_Stats_Scaling.md`,
> `Character_Weapon Mapping.md`, `Diagram_Summary.md` (section 3).
> Diagram: [promotion-flowchart.png](../diagrams/promotion-flowchart.png)

## Overview

Nine class lines, each with five tiers. A unit at the level cap with a
promotion item moves up one tier: new class name, stat boost, possibly new
weapons, skills and movement type. Promotion is permanent.

## Detailed Rules

### Class tree (Tier 1 → Tier 5)

| Tier 1 | Tier 2 | Tier 3 | Tier 4 | Tier 5 |
|--------|--------|--------|--------|--------|
| Knight | General | Great Knight | Aegis Lord | Eternal Sentinel |
| Mercenary | Hero | Vanguard | Warlord | Godslayer |
| Fighter | Warrior | Berserker King | Blood Champion | Abyss King |
| Archer | Sniper | Marksman | Phantom Archer | Star Piercer |
| Mage | Sage | Archsage | Elemental Avatar | Arcane Genesis |
| Cleric | Bishop | Saint | Divine Oracle | Miracle Saint |
| Thief | Assassin | Whisper | Shadow Walker | Void Phantom |
| Cavalier | Paladin | Gold Knight | Holy Commander | Radiant Emperor |
| Pegasus Knight | Falcon Knight | Seraph Knight | Celestial Valkyrie | Elysian Flame |

### Base stats (all Tier 1 classes)

| HP | STR / MAG | SKL | SPD | DEF | RES | LCK |
|----|-----------|-----|-----|-----|-----|-----|
| 20 | 4 | 3 | 4 | 3 | 2 | 5 |

### Usable weapons

| Class (line / tiers) | Weapons |
|----------------------|---------|
| Knight / General | Lance, Axe |
| Great Knight → Aegis Lord | Axe, Lance, Sword |
| Mercenary / Hero | Sword, Axe |
| Fighter / Warrior | Axe |
| Archer / Sniper | Bow |
| Mage / Sage | Tome |
| Archsage / Elemental Avatar | Tome, Arcane |
| Cleric / Bishop | Staff |
| Saint → Miracle Saint | Staff, Arcane |
| Thief / Assassin | Dagger, Sword |
| Whisper / Shadow Walker (Phantom) | Dagger, Bow |
| Cavalier / Paladin | Sword, Lance |
| Gold Knight → Radiant Emperor | Spear, Sword |
| Pegasus Knight | Lance |
| Falcon Knight | Lance, Staff |
| Seraph Knight → Celestial Valkyrie | Lance, Tome |

### Promotion flow

```text
Check eligibility → Level at cap? → Has promotion item?
→ Choose new class (if branching) → Update stats & tier
→ Unlock class skills → Done
```

- Requirements: level cap (usually Lv 20) **and** a promotion item (e.g. Master Seal).
  Story flags may block promotion.
- Effects: new class & tier, instant stat boost, possible new weapon types,
  class skill unlocks, higher stat caps, and possibly new appearance,
  movement type and growth rates.
- Some classes may branch. Promotion cannot be undone.

### Promotion skill examples

| Tier | Skill |
|------|-------|
| 2 | Brave Heart |
| 3 | Rally Defense |
| 4 | Sword Focus |
| 5 | Godstrike (ultimate) |

## Formulas

Stat increase on promotion, as % of the previous tier's value:

| Tier | HP | STR/MAG | SKL | SPD | DEF | RES | LCK |
|------|----|---------|-----|-----|-----|-----|-----|
| 2 | +30% | +25% | +20% | +20% | +25% | +20% | +10% |
| 3 | +20% | +15% | +10% | +10% | +15% | +10% | +5% |
| 4 | +20% | +15% | +10% | +10% | +15% | +10% | +5% |
| 5 | +15% | +10% | +10% | +10% | +10% | +10% | +5% |

Example (Mercenary line):

| Tier | STR | SPD | DEF |
|------|-----|-----|-----|
| 1 | 4 | 4 | 3 |
| 2 | 5 | 5 | 4 |
| 3 | 6 | 5.5 | 4.5 |
| 4 | 7 | 6 | 5 |
| 5 | 8 | 6.5 | 5.5 |

## Dependencies

`progression.md` (level cap, growth), `skill-system.md`, `weapons.md`,
`items-and-inventory.md` (promotion items), `terrain-and-maps.md` (movement types).

## Open Questions

[open-questions.md](open-questions.md): Q10 rounding, Q11 promotion skill lists disagree,
Q12 per-class base stats, Q13 class → movement type / weakness mapping, Q14 branching paths.
