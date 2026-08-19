# Game Design Document

## 1. Overview

**Working title:** Air Hockey

**Genre:** Casual Arcade / Sports

**Engine:** Unity

**Target platform:** WebGL

**Distribution platform:** Yandex Games

### High-level concept

Air Hockey is a short-session arcade game based on classic air hockey.

The player competes against an AI opponent. Each match takes place on a rectangular arena with two goals.

The main progression mechanic is the gradual modification of the arena.

Early levels provide a simple air hockey experience. Later levels introduce obstacles that interfere with the puck and create new possible trajectories.

---

# 2. Design Goals

The game should be:

* easy to understand within a few seconds;
* easy to control on both desktop and mobile;
* difficult to master;
* suitable for short gameplay sessions;
* visually clear;
* lightweight enough for browser distribution;
* fast to develop and iterate.

The game should prioritize **gameplay clarity and responsiveness over visual complexity**.

---

# 3. Core Gameplay

A match consists of two players:

* Human player
* AI opponent

Each player controls one paddle.

The objective is to score goals by hitting the puck into the opponent's goal.

### Core gameplay loop

```text
Start Match
     ↓
Move Paddle
     ↓
Hit Puck
     ↓
Defend Goal
     ↓
Score Goal
     ↓
Match Result
     ↓
Next Level / Retry
```

---

# 4. Player

The player controls the paddle located on their side of the arena.

### Desktop

The paddle follows the mouse position.

### Mobile

The paddle follows the player's touch position.

The paddle must remain inside the player's allowed area.

The player must never be able to move the paddle directly into the opponent's half of the arena.

---

# 5. Puck

The puck is the central physics object.

It moves around the arena and interacts with:

* walls;
* paddles;
* obstacles.

The puck should maintain a sufficiently high speed throughout the match.

Repeated collisions should not cause the puck to gradually lose all of its energy.

The game should avoid situations where the puck becomes almost stationary without player interaction.

---

# 6. Arena

The arena is divided into two halves.

```text
┌──────────────────────────────────────┐
│                  │                   │
│      PLAYER      │        AI         │
│                  │                   │
│                  │                   │
│                  │                   │
│      [GOAL]      │       [GOAL]      │
│                  │                   │
│                  │                   │
└──────────────────────────────────────┘
```

The exact visual design is subject to change during development.

The arena should remain visually readable even when multiple obstacles are present.

---

# 7. Goals and Scoring

Each side has one goal.

When the puck enters a goal:

1. The current player scores.
2. The score is updated.
3. The puck and paddles are reset.
4. The match continues or ends according to the current match rules.

The exact win condition will be finalized during Sprint 1.

---

# 8. AI

The AI controls the opponent paddle.

The first implementation should be intentionally simple and deterministic.

The AI observes the puck position and moves its paddle toward the predicted or current puck position.

### Main parameters

* `movementSpeed`
* `reactionTime`
* `accuracy`

These parameters can later be used to implement difficulty levels.

### Difficulty

Potential difficulty levels:

* Easy
* Normal
* Hard

Difficulty should primarily affect the AI's reaction and movement rather than introducing artificial advantages.

---

# 9. Level System

The game uses a level-based progression system.

The initial level progression is:

| Level | Main change               |
| ----: | ------------------------- |
|     1 | Basic arena               |
|     2 | One static obstacle       |
|     3 | Multiple static obstacles |
|     4 | Central obstacle          |
|     5 | Narrow passages           |
|     6 | Moving obstacle           |
|     7 | Multiple moving obstacles |
|     8 | Combined obstacle layouts |
|     9 | High-complexity arena     |
|    10 | Final challenge           |

This list is a design proposal rather than a fixed production requirement.

The final number of levels will depend on the amount of content required to make progression meaningful.

---

# 10. Obstacles

Obstacles are the primary gameplay modifier.

## Static obstacle

A stationary object that changes the puck's trajectory.

## Moving obstacle

An object that moves according to a predefined pattern.

Moving obstacles introduce a timing component and make the puck trajectory less predictable.

### Future possibilities

The following mechanics are currently outside the MVP but may be considered later:

* rotating obstacles;
* destructible obstacles;
* teleporters;
* speed zones;
* temporary obstacles;
* power-ups.

---

# 11. Difficulty Progression

Difficulty should increase gradually.

The preferred progression is:

```text
Simple arena
     ↓
More obstacles
     ↓
More complex trajectories
     ↓
Moving obstacles
     ↓
Combined layouts
     ↓
High-skill challenge
```

The game should not rely exclusively on increasing AI difficulty.

The arena itself should be an important part of the challenge.

---

# 12. Controls

## Desktop

Primary input:

```text
Mouse
```

The paddle follows the mouse position within the allowed player area.

## Mobile

Primary input:

```text
Touch
```

The paddle follows the player's finger.

The control system should provide similar gameplay behavior on both platforms.

---

# 13. Game Flow

```text
Bootstrap
    ↓
Main Menu
    ↓
Level Selection
    ↓
Game
    ↓
┌───────────────┐
│               │
Victory       Defeat
│               │
↓               ↓
Next Level    Retry
```

---

# 14. Technical Architecture

The planned high-level components are:

```text
GameManager
├── LevelManager
├── ScoreManager
└── UIManager
```

Gameplay:

```text
PlayerController
AIController
PaddleController
PuckController
Goal
Obstacle
```

The architecture should remain intentionally lightweight.

New abstractions should only be introduced when they solve an actual problem in the project.

---

# 15. Prefabs

Planned prefabs:

```text
PlayerPaddle
AIPaddle
Puck
Goal
Obstacle
```

Potential future prefabs:

```text
MovingObstacle
BreakableObstacle
```

---

# 16. Design Principles

The project follows several principles:

### 1. Gameplay first

The game should be fun before significant visual polish is added.

### 2. Simple controls

The player should understand the controls immediately.

### 3. Short sessions

A player should be able to complete a level in a short session.

### 4. Progressive complexity

New mechanics should be introduced gradually.

### 5. Small scope

The project is intentionally small so that it can reach publication quickly.

### 6. Data-driven iteration

After publication, player behavior and game metrics should influence future development decisions.
