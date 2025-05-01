# ⚔️ Combat Mechanics

Detailed formulas and rules for combat resolution, including damage, proficiency, triangle bonuses, class weaknesses, and critical hits.

---

## 🔸 Damage Calculation Formula

### 📌 Physical Attack:

```ts
damage = (weapon.might + attacker.STR) - defender.DEF
```

- `weapon.might`: Base power of the weapon (e.g., 10)
- `attacker.STR`: Strength stat of the attacker
- `defender.DEF`: Defense stat of the target

### 📌 Magic Attack:

```ts
damage = (weapon.might + attacker.MAG) - defender.RES
```

- Uses `MAG` (Magic) and `RES` (Resistance)

### 🧮 Final HP Deduction:

```ts
finalDamage = max(0, totalDamage)
defender.currentHP -= finalDamage
```

- Always clamps to a minimum of 0 (no healing the enemy)
- HP cannot go below 0

---

## 🧠 Weapon Proficiency System

- Each **weapon** has a `requiredLevel`: `E → D → C → B → A → S → S+`
- Each **character** has a `proficiencyLevel` for each weapon type

### ✅ Bonus Calculation

```ts
if character.proficiency >= weapon.required:
  hitBonus  = (proficiencyLevel - requiredLevel) * 5%
  critBonus = (proficiencyLevel - requiredLevel) * 5%
```

- Example: Weapon requires **C (2)**, character has **A (4)**
→ `+10% Hit`, `+10% Crit`

---

## 🔺 Weapon Triangle Advantage (Rock-Paper-Scissors System)

| Attacker Weapon | Strong Against | Bonus Effect              |
|------------------|----------------|----------------------------|
| **Sword**        | Axe            | +15% Hit, +3 Damage        |
| **Axe**          | Lance          | +15% Hit, +3 Damage        |
| **Lance**        | Sword          | +15% Hit, +3 Damage        |

- This bonus is **only applied if attacker uses correct counter weapon**
- Bonus stacks with class weakness

---

## 🧨 Class Weakness Multiplier

| Class Type        | Weak Against             | Bonus Damage Multiplier |
|-------------------|--------------------------|--------------------------|
| **Cavalry**       | Spear, Anti-cav weapons  | +50%                     |
| **Armored (Knight)** | Magic, Hammer         | +50%                     |
| **Flying (Pegasus)** | Bow, Wind Tome        | +100%                    |
| **Thief / Assassin** | Heavy weapons         | +20%                     |
| **Mage**          | Silence, Anti-magic      | +30%                     |

📌 **Bonus damage is added to the total `damage` before HP is reduced.**

### 🧮 Weakness Formula:

```ts
if defender has weakness:
  damage += floor(damage * bonusMultiplier)
```

---

## 💥 Critical Hit Formula

### 📌 Crit Chance:

```ts
critChance = weapon.crit + (attacker.SKL / 2) - defender.LCK
```

- `weapon.crit`: Base crit stat of the weapon
- `SKL`: Attacker's Skill
- `LCK`: Defender's Luck

### 📌 Crit Damage:

```ts
critDamage = damage * 3
```

- Only applied if random roll <= `critChance`

---

## 🎯 Hit Rate Formula

### 📌 Calculation:

```ts
hitRate = weapon.hit + (attacker.SKL * 2) + proficiencyBonus
avoid = (defender.SPD * 2) + defender.LCK
finalHitChance = hitRate - avoid
```

- `proficiencyBonus` comes from Weapon Proficiency rules above
- Random roll (0–100) must be ≤ `finalHitChance` for attack to land

---

## ❤️ Combat Resolution Flow

1. Check weapon type and triangle bonus
2. Compute base damage
3. Apply class weakness multiplier (if any)
4. Check hit chance → if missed: `damage = 0`
5. Check crit chance → if crit: `damage *= 3`
6. Subtract `damage` from `defender.currentHP`
7. Clamp defender HP to `≥ 0`

---

💡 This system encourages:
- Strategic class matchups
- Tactical weapon selection
- Mastery & promotion planning
