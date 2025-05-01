# 🤖 Enemy AI System

This document outlines the logic, behavior modes, and evaluation systems for enemy units in the SRPG game.

---

## 🎯 AI Goals

Enemy units aim to:
- Maximize threat to the player
- Prioritize objectives (attack, defend, retreat)
- Use terrain and formation intelligently

---

## 🧠 AI Behavior Types

| Type        | Description                                     | Example Behavior                  |
|-------------|--------------------------------------------------|-----------------------------------|
| Aggressive  | Always move and attack if in range              | Bandits rushing nearest target    |
| Defensive   | Hold position until player is near              | Guards in forts                   |
| Patrol      | Move in a fixed path, attack if encountered     | Castle patrols                    |
| Ambush      | Hidden until triggered, then attack             | Units in forests or behind doors  |
| Boss        | Wait until attacked or scripted activation      | Final boss stands on gate         |
| Support     | Use buffs, healing, or reposition allies        | Healers and buffers               |

---

## 📏 Targeting Priority

Enemies evaluate player units by score:

```ts
priorityScore =
  (low HP bonus) +
  (damage potential) +
  (unit class priority) +
  (objective proximity)
```

### Example Weights

| Factor                  | Bonus |
|-------------------------|--------|
| Target HP < 50%         | +20    |
| Can kill target         | +50    |
| Target is healer        | +30    |
| Blocking objective tile | +40    |

---

## 🧮 Threat Evaluation

Each enemy simulates:
- Can I reach a target?
- Can I survive retaliation?
- Can I block or delay objectives?

They pick the highest-score option unless scripted.

---

## 🔁 AI Turn Flow

```text
Start AI Turn
→ Evaluate visible units
→ Score possible moves
→ Move toward or attack best target
→ End turn or wait
```

---

## 📦 AI Custom Parameters

| Parameter       | Description                            |
|------------------|----------------------------------------|
| aggroRadius     | Distance in tiles before activation     |
| moveLimit       | Max tiles AI will move from origin      |
| targetBias      | Focus on healers / tanks / weak units   |
| scriptTrigger   | Event-driven control                   |

---

## ⚠️ AI Scripted Triggers

Used for special maps and boss fights.

| Trigger Type     | Example                              |
|------------------|---------------------------------------|
| Player enter zone| Ambush enemies activate               |
| Ally dies        | Boss becomes enraged                  |
| Turn count       | Reinforcements spawn at turn 5        |
| Objective reached| AI fallback or retreat                |

---

## 🧩 Advanced Options

- AI can adapt if leader dies
- Coordinate with other AI (formations)
- React to terrain control loss
- Use skills/items if enabled

---

📌 Smart AI = challenging but fair gameplay.