## 3. Positioning and differentiation

A faithful Battle Bricks or Battle Cats port is not a product: Battle Cats already owns the landscape, gacha-driven version of this genre, and Battle Bricks is free on Roblox. PUSHLINE's slot is **the portrait, one-thumb, solo, gacha-free, campaign-complete lane battler**, and it earns that slot with one original tactical hook rather than a longer feature list.

### Competitive frame

| Game | Orientation | Core model | Progress gated by | What we take | What we reject |
| --- | --- | --- | --- | --- | --- |
| The Battle Cats (PONOS) | Landscape | Side-view lane battler, auto-combat | Gacha units, energy, treasure RNG | Deploy-timing economy, unit roles, chapter structure | Gacha as the main unit source, energy timers |
| The Battle Bricks (Roblox) | Landscape (2.5D) | Battle Cats structure, single-player | XP grind, stage drops | Loadouts, bank upgrade, cannon, traits, bosses, daily track | XP grinding, one-solution late stages |
| Castle Crush | Portrait | Vertical lane, card deployment, PvP | Card rarity, ladder | Vertical-lane readability, bottom card bar | Multiplayer dependency, card chase |
| Grow Castle | Portrait | Base defense, enemies walk in from one side | Idle upgrades | Portrait idle-friendly HUD | Idle/AFK economy |
| Plants vs. Zombies 2 | Landscape | Lane defense, grid placement | Level unlocks, some premium plants | World-based mechanic introduction, mechanic-per-world | Grid placement (needs precision taps) |

### The hook: Momentum zones

The lane is divided into three visible zones between the two bases. Whichever side's frontline occupies a zone for 4 seconds captures it. Captured zones change the battle:

- **Zone 1 (yours by default):** no effect. Losing it means the enemy is at your gate.
- **Zone 2 (middle):** holder gains +20% cash income. This is the fight most stages revolve around.
- **Zone 3 (enemy's by default):** holder's Command Meter charges 50% faster. Taking it is how you set up the kill on the enemy base.

Stage scripts can hang events on zone captures: "when the player captures Zone 2, spawn the elite", "when the player loses Zone 1, spawn 3 reinforcements". That gives level designers a second axis of pacing (space) on top of waves (time), and it gives the player a readable mid-stage goal other than "survive". It is also what makes a single vertical lane, which could feel thin, read as a tug-of-war.

### Secondary hook: Command Meter with a choice

Battle Cats has one timed cannon; Battle Bricks lets you pick one of eight cannon types before a battle (Section 2.1). PUSHLINE goes one step further: one meter and two equipped Commands (chosen before the stage from a pool that grows through the campaign). Spending the meter on a wall instead of a blast is a decision, and which two Commands to bring is a loadout decision. Both hooks are built entirely from single taps, so they cost nothing against constraint C1.

### What we deliberately keep simple

Units are never micro-controlled. There are no sub-lanes, no grid, no drag placement. The player's whole input vocabulary is: tap a unit card, tap a Command, tap bank upgrade, tap speed, tap pause.
