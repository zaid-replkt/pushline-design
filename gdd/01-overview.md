## 1. Overview

**PUSHLINE (working title)** is an original, portrait-only, one-thumb 2D lane battler for iOS and Android: you deploy units from the bottom of the screen, they march up a vertical lane, and the stage is won when the enemy base at the top falls before yours at the bottom does. It takes the proven structure of The Battle Bricks (Roblox) and The Battle Cats (mobile) and rebuilds it as a single-player, level-based campaign with at least 30 hours of first-clear content and no mandatory grinding.

### Constraints this document is built to satisfy

These come from the brief and are treated as hard requirements, not preferences.

| # | Constraint | How it shows up in this design |
| --- | --- | --- |
| C1 | Portrait-only, playable one-handed | Vertical lane; every tappable control inside the bottom 40% of the screen; no gestures that need two fingers |
| C2 | Fully playable solo; no multiplayer dependency | No co-op, no PvP, no social gates; leaderboards are asynchronous and optional |
| C3 | Level / wave / world based, not creative or open-world | Fixed world map, authored stages, authored waves; no sandbox or building |
| C4 | 30+ hours of meaningful first-clear content | 270 authored challenges (180 main stages, 60 side stages, 30 trials) budgeted at 30.0 h; grinding does not count |
| C5 | No pop-culture IP, no brainrot, no gambling loops | Original characters, art and names; no gacha for core units; no loot-box RNG gating progress |
| C6 | Roblox-grade retention design plus Battle Bricks' gameplay standards | Section 11 (retention) and Section 6-9 (gameplay depth) implement the checklists agreed in the brief |
| C7 | Mobile quality bar | 60 fps target, 44 pt touch targets, 99.5% crash-free sessions, auto-save and instant retry (Section 14) |

### Design pillars

1. **Read the lane, not the manual.** Every enemy's threat and every unit's role is legible from its silhouette and behaviour on screen. If a player needs the encyclopedia to survive, the stage is misdesigned.
2. **Every stage asks a new question.** A stage exists only if it introduces, tests or twists a mechanic. Stat-inflated repeats are cut, not shipped.
3. **Progress by clearing, not farming.** Clearing the campaign at its intended pace must fund all required upgrades. Replaying a stage is a choice, never a toll.
4. **One thumb, full control.** Deployment, abilities, speed and pause are all reachable by the right or left thumb without re-gripping the phone. Switching hands is supported with a mirror layout.

### What this document is and is not

This is a buildable v0.1 design: systems, formulas, content budgets, schemas and production plan. It is not a balance sheet of final numbers; every tunable value is marked as a starting point to be validated in playtests (Section 9.5). Figures taken from outside sources are cited inline and gathered in Section 18.
