# Open Questions & Inconsistencies

Found while merging the original 27 design files. Each needs a decision before
the related system is built. Mark an item **DECIDED: ...** when resolved and
update the GDD it points to.

14 items were decided on 2026-11-21 by the [differentiation review](../reviews/2026-11-21-gameplay-differentiation.md).

## Core loop

| # | Topic | Question | GDD |
|---|-------|----------|-----|
| Q1 | Preparation Phase | Named in the loop, never defined. Unit selection? Deployment slots? Shop? | game-loop |
| Q2 | Win check timing | **DECIDED:** Seize / Boss Kill win immediately; other goals checked at end of round. | game-loop |
| Q43 | Phase vs timeline | **DECIDED:** Phase model kept; timeline stays optional / not planned. | game-loop, turn-order-timeline |

## Combat

| # | Topic | Question | GDD |
|---|-------|----------|-----|
| Q3 | Counter-attacks | **DECIDED:** Defender counters if the attacker is in its weapon range, unless Pincered. | combat-system |
| Q4 | Follow-up attacks | **DECIDED:** Follow-up when AS ≥ foe AS + 4; AS = SPD − max(0, weight − STR/2). | combat-system |
| Q5 | Terrain in hit | Terrain gives Avoid/DEF/RES bonuses, but the hit and damage formulas do not include them. | combat-system, terrain-and-maps |
| Q6 | Undefined weapons | **DECIDED:** Tomes get an element (fire / ice / thunder / wind). Other undefined weakness sources: rename or drop when class-system is rewritten. | combat-system |
| Q7 | Spear vs Lance | Two weapon types. Is Spear in the triangle? Does Lance get anti-cavalry? | weapons |
| Q8 | EXP formula | "Based on damage or kill" — no numbers. | combat-system, progression |
| Q9 | Clamping | **DECIDED:** Clamp hit and crit to 0–100. Crit multiplier ×2.5 (or Dagger crit 10%) — pick in tuning. | combat-system |

## Classes & progression

| # | Topic | Question | GDD |
|---|-------|----------|-----|
| Q10 | Rounding | **DECIDED:** Flat per-class promotion bonuses replace % scaling. | class-system |
| Q11 | Promotion skills | **DECIDED:** Replaced by Oath branches (P4); skill lists rewritten per Oath. | class-system, skill-system |
| Q12 | Base stats | Every Tier 1 class has identical base stats, and STR/MAG share one value. Per-class bases needed. | class-system |
| Q13 | Class tags | Which classes are Cavalry / Armored / Flying / Infantry? Needed for weakness and movement. | class-system, terrain-and-maps |
| Q14 | Branching | **DECIDED:** Branch (two Oaths) at Tier 2 and Tier 4. | class-system |
| Q15 | SKL growth mod | Class growth-mod table has no SKL column. | progression |
| Q16 | Stat caps | "Caps increase per tier" — no values. | progression |
| Q19 | Example tier | Lyra is a "Falcon Knight" with `tier: 3`; the tree puts Falcon Knight at Tier 2. | character-data |

## Data model

| # | Topic | Question | GDD |
|---|-------|----------|-----|
| Q17 | MP / SP | **DECIDED:** Shared team Momentum 0–10 replaces MP/SP. | character-data, skill-system |
| Q18 | Growth field | Units have no `growth` field in the template. | character-data |

## Weapons & items

| # | Topic | Question | GDD |
|---|-------|----------|-----|
| Q20 | Weight | **DECIDED:** Weight lowers Attack Speed (see Q4). | weapons |
| Q21 | Range | No attack range per weapon type (Bow 2, Tome 1–2, ...). | weapons |
| Q22 | Durability | Weapons have no uses/durability. Intentional? | weapons |
| Q23 | Weapon list | Individual weapons (Iron Sword, Steel Lance, Fire Tome) are referenced but not defined. | weapons |
| Q27 | Elixir | Item_System: full HP heal. StatusEffects: removes all buffs and debuffs. Both? | items, status-effects |
| Q29 | Gear slots | Item_System: Footwear / Armor / Accessory. Inventory UI: Weapon / Armor / Accessory. | items |
| Q30 | Item action | Does using an item end the unit's action? | items |
| Q31 | Convoy | Is there shared storage when a unit's 10 slots are full? | items |
| Q32 | Promotion items | Master Seal is needed for promotion but is not in the item list. | items, class-system |

## Skills & status

| # | Topic | Question | GDD |
|---|-------|----------|-----|
| Q24 | Brave Heart | Table: unlocked on promotion. Code sample: Hero Lv ≥ 5. | skill-system |
| Q25 | Burn | **DECIDED:** Burn = standing on a Burning tile or hit by a fire crit. | skill-system, status-effects |
| Q26 | "X" values | Many statuses use "+X" / "−X". Need numbers. | status-effects |
| Q28 | Tick timing | **DECIDED:** Status and terrain tick in the Environment Phase. | status-effects |

## AI, maps, save

| # | Topic | Question | GDD |
|---|-------|----------|-----|
| Q33 | AI scoring | "Damage potential" and "survive retaliation" have no point values. | enemy-ai |
| Q34 | Tie-break | **DECIDED:** Tie-break: can kill → lowest HP → nearest → lowest id. | enemy-ai |
| Q35 | Movement penalties | "Struggles with" has no numbers (extra cost? impassable?). | terrain-and-maps |
| Q36 | Desert | Move cost 2–3: which classes pay 3? | terrain-and-maps |
| Q37 | Ch.1 map | Only 4 of 12 rows drawn; no enemy positions. | terrain-and-maps |
| Q38 | Enemy triggers | Can enemy units fire position triggers? | map-events |
| Q39 | Wyvern Rider | Spawned in Ch.3 but not in the class tree. | map-events, class-system |
| Q40 | Save version | No schema version field for future migrations. | save-load |
| Q41 | RNG seed | Save the RNG seed? (Decides whether reloading re-rolls hits.) | save-load |
| Q42 | Slots | How many manual save slots? | save-load |
