## 8. Campaign structure

270 authored challenges: 6 worlds of 30 main stages (180), 6 side campaigns of 10 stages (60), and 30 trials. Main stages are linear within a world; side campaigns and trials are optional and open as the player climbs. Nothing is gated on stars or on replaying. Every one of the 270 stages is specified row by row (waves, triggers, stars, rewards, unlocks) in the companion stage sheet, pushline\_stage\_sheet.xlsx, with the same data as pushline\_content.json in the Section 14.3 schema; that sheet also carries the full 40-unit and 72-enemy rosters.

### 8.1 Structure and gates

| Content | Count | Unlocks when | Gate to next |
| --- | --- | --- | --- |
| World N main stages 1-30 | 30 per world | World N-1 boss cleared | Stage N-30 (world boss) cleared |
| Mid-boss | Stage 15 of each world | Linear | Linear |
| World boss | Stage 30 of each world | Linear | Opens next world and that world's side campaign |
| Side campaign N | 10 stages | World N boss cleared | None; rewards units, Cogs, cosmetics |
| Trials 1-10 | 10 | World 2 boss cleared | None |
| Trials 11-20 | 10 | World 4 boss cleared | None |
| Trials 21-30 | 10 | World 6 boss cleared | None; these are the endgame |

### 8.2 Level pacing template (every block of 10 stages)

Each block of 10 main stages follows the same rhythm so designers build to a template and players feel a cadence without noticing the pattern.

| Stages in block | Beat | What the stage does | Target first-clear rate |
| --- | --- | --- | --- |
| 1-2 | Introduce | New enemy or mechanic shown alone, in a safe stage; the counter unit unlocks here or just before | 90% |
| 3-5 | Test | New element mixed with known ones; one zone trigger | 80% |
| 6-7 | Twist | Known element used against expectation (Swarm that is Armoured, Fast that spawns at Zone 2) | 65% |
| 8-9 | Pressure | Full composition, two zone triggers, bank decisions matter | 60% |
| 10 | Checkpoint | Mid-boss (stage 15) or world boss (stage 30); stage 10 and 20 are elite-formation stages | 50% first attempt, 85% within 3 |

### 8.3 Mechanic introduction schedule

| World | Stages 1-10 | Stages 11-20 | Stages 21-30 |
| --- | --- | --- | --- |
| 1 Scrapyard Foothills | Deploy, Bank, Blast, knockback, Fast (1-5 are the tutorial) | Swarm, Area units, Zone 2 income, Bulwark | Mixed waves, zone-loss triggers, The Compactor |
| 2 Fungal Hollows | Armoured, Pierce, spore slow in Zone 2 | Rally, bank-denial stages (enemy raids your Zone 1 early) | Armoured Swarm, Mother Cap |
| 3 Clockwork Terraces | Flying, Anti-air, Surge | Boss-entrance shockwave on elites, Zone 3 meter bonus stages | Flying plus Armoured, The Clockmaster |
| 4 Frost Spires | Ranged, Reach units, Frost command | Frozen-zone hazard, out-ranging fights | Ranged behind Armoured walls, Glacier Hart |
| 5 Ember Forges | Colossal, Stun, Beacon | Lava pulse hazard, burst-window timing | Two Colossals, Furnace King |
| 6 The Crown | Formations: authored 3-tag waves | Double-trigger stages (zone and HP) | Two-boss stages, The Twin Wardens |

### 8.4 Side campaigns (10 stages each, unlocked by the matching world boss)

| Side campaign | Rule | Reward on completion |
| --- | --- | --- |
| Scrap Rush (W1) | Only Scouts and Strikers allowed | Unit: Tinker (Support) |
| Deep Hollows (W2) | All enemies Hardened or Mending | Unit: Sporeknight (Vanguard) |
| Night Shift (W3) | Lane viewport darkened; enemies visible only in Zones 1-2 | Unit: Lamplighter (Ranger) |
| Whiteout (W4) | Command Meter disabled; Bank starts at level 4 | Unit: Icebreaker (Breaker) |
| Slag Pits (W5) | Volatile on every enemy | Unit: Ashwalker (Striker) |
| Warden's Gauntlet (W6) | Every stage is a boss from Worlds 1-5 with two modifiers | Unit: Crownbearer (Vanguard) |

### 8.5 Trials (30 unique challenges)

Trials are single stages with a bespoke rule, never a stat-inflated repeat. Examples from the launch list: "Six cards" (loadout of 6), "Flatline" (no Bank upgrades), "Mirror" (enemies use your last loadout as their roster), "Sprint" (enemy base HP 5,000, your base HP 1,000), "Long March" (lane length 2,000), "Silence" (no Commands, Zone bonuses doubled), "Rust Tide" (endless Swarm, win by surviving 4 minutes). Trials 21-30 require Form III units to be realistic and are the intended endgame.

### 8.6 Stars and completion

- 3 stars per main and side stage, 1 per trial: 750 stars in total.
- Stars unlock cosmetic rewards and Cogs at thresholds (every 25 stars) and nothing else. No world is gated on stars.
- Completion tracker on the world map shows stages, stars, units found and Cores collected per world so completionists have a visible 100%.
