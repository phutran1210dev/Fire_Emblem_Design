# ⏳ Turn-Order Timeline (Optional System)

Describes a Final Fantasy Tactics-style initiative system.

---

## 🔄 Timeline Mechanics

- Each unit has **initiative score** based on `SPD`
- Turn order sorted dynamically each round

---

## 🧮 Initiative Formula

```ts
initiative = unit.SPD + random(0–3)
```

- High SPD = more frequent turns
- Can manipulate timeline using skills (e.g. "Slow", "Haste")

---

## 🧱 Timeline UI

- Timeline bar on screen edge
- Shows order of upcoming 10 actions
- Icons = unit portraits

---

## 💥 Timeline Effects

| Effect        | Description                       |
|---------------|-----------------------------------|
| Delay         | Push unit further down timeline   |
| Skip Turn     | Remove unit from next action slot |
| Interrupt     | Cancel current action             |

---

📌 Adds tactical depth, especially in 1v1 or boss battles