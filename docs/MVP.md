# Minimum Viable Product

## 1. Objective

The MVP is the smallest complete version of Air Hockey that can be played, tested and prepared for publication on Yandex Games.

The MVP must provide a complete gameplay loop rather than a collection of disconnected mechanics.

---

# 2. Required Features

## Gameplay

* [ ] Player paddle
* [ ] AI paddle
* [ ] Puck
* [ ] Arena
* [ ] Walls
* [ ] Goals
* [ ] Collision physics
* [ ] Score system
* [ ] Win condition
* [ ] Lose condition
* [ ] Match restart
* [ ] Level progression
* [ ] Static obstacles

---

# 3. Controls

### Desktop

* [ ] Mouse control

### Mobile

* [ ] Touch control

Both control methods must provide usable gameplay.

---

# 4. Level System

The MVP must contain multiple playable levels.

Minimum target:

**5 levels**

Target if development remains fast:

**10 levels**

The levels should demonstrate progressive difficulty.

At least some levels must contain obstacles.

---

# 5. AI

The MVP requires a functional AI opponent.

The AI does not need advanced prediction or machine learning.

Minimum requirements:

* [ ] AI follows the puck
* [ ] AI is restricted to its own half
* [ ] AI has configurable movement speed
* [ ] AI has configurable reaction delay

---

# 6. UI

Required:

* [ ] Main menu
* [ ] Level selection or level progression
* [ ] Score display
* [ ] Victory screen
* [ ] Defeat screen
* [ ] Retry button
* [ ] Next level button
* [ ] Main menu button

---

# 7. Audio

Minimum:

* [ ] Puck collision sound
* [ ] Goal sound
* [ ] Victory sound
* [ ] Defeat sound
* [ ] Basic background music

Audio should remain lightweight and should not delay the first playable build.

---

# 8. Platform

The MVP must be capable of running as a WebGL build.

Target environments:

* Desktop browsers
* Mobile browsers

The game must be tested in a browser before publication.

---

# 9. Out of Scope

The following features are explicitly excluded from the MVP:

* Multiplayer
* Online matchmaking
* User accounts
* Authentication
* Inventory
* Currency
* Shop
* Character progression
* Skins
* Achievements
* Leaderboards
* Story mode
* Complex power-up system
* Advanced AI
* Procedural level generation

These features may be considered after the initial release.

---

# 10. MVP Success Criteria

The MVP is considered complete when:

1. A player can start a match.
2. The player can control the paddle.
3. The AI can control the opponent paddle.
4. The puck behaves consistently.
5. Goals are detected correctly.
6. The score is updated correctly.
7. A match can be won or lost.
8. The player can progress through multiple levels.
9. Obstacles work correctly.
10. The game can be built for WebGL.
11. The game can be played in a desktop browser.
12. The game can be played on a mobile browser.

---

# 11. MVP Philosophy

The MVP is not intended to represent the final version of the game.

Its purpose is to answer a more important question:

> **Is the core gameplay fun enough to justify further development?**

Additional features should only be added after the core gameplay has been validated.
