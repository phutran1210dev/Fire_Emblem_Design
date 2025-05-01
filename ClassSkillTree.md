# 🌲 Class-Specific Skill Tree

Defines which skills each class can unlock across tiers.

---

## 🧱 Structure

Each class has a pool of learnable skills by:

- Tier (1 → 5)
- Level milestone (e.g., Lv5, Lv10, Lv20)
- Promotion bonus

---

## 🔹 Example: Mercenary → Hero → Vanguard → Warlord → Godslayer

| Tier | Level | Skill Name     | Type     | Notes                    |
|------|-------|----------------|----------|--------------------------|
| 1    | 5     | Quick Slash    | Active   | Light sword attack       |
| 1    | 10    | Counter Posture| Passive  | Counter when hit         |
| 2    | Promo | Brave Heart    | Passive  | +2 STR if HP < 50%       |
| 3    | 5     | Rally Speed    | Active   | +SPD to nearby allies    |
| 4    | 10    | Sword Focus    | Passive  | +10 Hit/Crit with Sword  |
| 5    | Promo | Godstrike      | Active   | Massive AoE slash        |

---

## 📘 Skill Unlock Logic

```ts
if unit.class === 'Hero' and level >= 5:
  unlock('Brave Heart')
```

- Skills are auto-learned or require SP depending on design

---

📌 Builds unique class identities and tactical progression