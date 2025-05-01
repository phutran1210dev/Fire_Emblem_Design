# 🧩 Map Event Trigger Flow

This document explains how tile-based triggers and map events are activated in the SRPG system.

---

## 🔁 Map Event Flow Overview

```text
Start Map
↓
Scan for Triggers
↓
Player Movement or Action
↓
Check if Trigger Zone Entered
↓
Determine Event Type
↓
Apply Event Effect (spawn, open, reward, etc.)
↓
Set Event Flag (prevent repeat)
↓
Resume Battle
```

---

## 🧠 Trigger Types

| Type           | Description                              |
|----------------|------------------------------------------|
| Enemy Spawn    | Reinforcements appear at specific tiles  |
| Dialogue       | Cutscene or story interaction triggers   |
| Item Grant     | Free item or treasure is awarded         |
| Door / Gate    | Unlocks a new path or tile               |
| Scripted Event | Trigger storyline branch or condition    |

---

## 🎯 Trigger Conditions

| Condition Type | Example                               |
|----------------|----------------------------------------|
| Position       | Player steps into (X, Y) tile          |
| Kill Count     | Enemy count < 3                        |
| Turn Number    | Turn ≥ 5                               |
| Unit Action    | Talk, Use Key, Wait on tile            |
| Flag Check     | Event not yet triggered                |

---

## 🧬 Flag System

Each trigger sets a flag to track if it’s already activated:

```ts
if !eventFlags["ch2_gate_open"]:
  openGate()
  eventFlags["ch2_gate_open"] = true
```

- Prevents repeat triggers
- Flags can affect win/lose conditions

---

## 📘 Event Example

> **Map:** Chapter 3 - Bridge Siege  
> **Trigger Tile:** (8, 4)  
> **Condition:** Player unit steps on tile  
> **Effect:** Spawns 3 Wyvern Riders from north  
> **Flag:** `ch3_wyverns_spawned`

---

## ✅ Summary

| Step               | Description                       |
|--------------------|-----------------------------------|
| Player acts        | Moves, waits, interacts           |
| Trigger activated  | Based on condition                |
| Effect applied     | Spawn, reward, door, or cutscene  |
| Flag set           | Prevent duplicate activation      |
| Game resumes       | Return to normal turn order       |

📌 Encourages dynamic maps and replayability via hidden triggers.