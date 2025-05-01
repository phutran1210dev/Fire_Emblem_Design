# 💾 Save / Load System Design

Design plan for saving and loading player progress in the SRPG.

---

## 📂 Save Structure

| Field         | Description                        |
|---------------|------------------------------------|
| Player State  | All character stats, items, EXP    |
| Map State     | Tile layout, units on grid         |
| Turn State    | Whose turn, phase, round           |
| Event Flags   | Triggers, decisions made           |
| Timestamp     | When save was created              |

---

## 💬 Save Types

- **Manual Save**: via menu
- **Auto Save**: after chapter, turn, or battle
- **Quick Save**: temporary mid-battle save

---

## 📘 File Format Example (JSON)

```json
{
  "map": "chapter3_castle",
  "turn": 4,
  "phase": "player",
  "units": [...],
  "flags": { "boss_escaped": false },
  "timestamp": "2025-05-02T12:00:00Z"
}
```

---

📌 Useful for long battles, branching choices, and persistence