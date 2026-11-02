## 7. Enemy system

Enemies are the questions the campaign asks; units are the answers. 72 enemy types at launch (12 per world) built from 6 tags, each world introducing one new tag or behaviour, plus 6 multi-phase world bosses and 12 side-campaign bosses.

### 7.1 Tags

Every enemy has 1-2 tags shown as an icon above its head and on the stage card. Tags are what unit traits key on.

| Tag | What it means mechanically | Intended answer | First seen |
| --- | --- | --- | --- |
| Fast | Speed 70-110; reaches your base before most units deploy | Scouts to block, Strong-vs-Fast Strikers, Slow | World 1 |
| Swarm | Spawns in groups of 4-12, low HP, 1 segment | Area units (Barrage), Reach | World 1 |
| Armoured | Takes 50% damage except from Pierce; 4-8 segments | Pierce, Strong-vs-Armoured, Breakers | World 2 |
| Flying | Melee units without the Anti-air flag cannot hit it; it ignores Bulwark | Rangers with Strong-vs-Flying, Anti-air Strikers | World 3 |
| Ranged | Attacks from 150-300 range; out-ranges your frontline | Fast Strikers, Reach, Rally | World 4 |
| Colossal | 10+ segments, knockback-immune until last 3 segments, pushes your frontline back on each hit | Stun, Frost, burst windows, Breakers | World 5 |

World 6 adds no tag; it combines all six in authored formations.

### 7.2 Enemy stat template

Same fields as units (Section 6.2) plus `value` (bounty is 25% of value), `tags[]`, `boss` flag, and `phases[]` for bosses. Enemy stats are authored per world, not per level; difficulty inside a world comes from composition, timing and zone triggers, not from HP inflation.

### 7.3 Families by world

| World | Setting | Family | Flavour | New mechanic the family teaches |
| --- | --- | --- | --- | --- |
| 1 | Scrapyard Foothills | Rustlings | Scrap-built critters, wobbling | Basics, Fast, Swarm, knockback |
| 2 | Fungal Hollows | Sporefolk | Mushroom cap soldiers, spore clouds | Armoured; Zone 2 income fights |
| 3 | Clockwork Terraces | Gearkin | Wind-up automata, airships | Flying; boss entrance shockwave |
| 4 | Frost Spires | Rimeborn | Ice-shelled beasts, archers | Ranged; frost hazard slows the lane |
| 5 | Ember Forges | Cinderbrood | Magma golems, forge hounds | Colossal; lava pulses damage Zone 2 |
| 6 | The Crown | Wardens | Elite mixed guard of the summit | Formations, all tags, two-boss stages |

### 7.4 Elite modifiers

Side campaigns and trials reuse the 72 base enemies with modifiers rather than new art. Modifiers stack at most two per enemy and always show as a coloured rune icon.

| Modifier | Effect |
| --- | --- |
| Hardened | +3 knockback segments |
| Hasty | +40% speed, +20% attack speed |
| Mending | Regenerates 2% HP per second while not attacked for 3 s |
| Warded | First 3 hits absorbed |
| Captain | Nearby allies +25% damage; dies first and the buff ends |
| Volatile | Explodes on death for 300 area damage to your units |

### 7.5 Boss design rules

1. Every world boss has 3 phases at 100 / 60 / 25% HP. Each phase adds one behaviour; it never only raises damage.
2. All boss attacks have a 2 s telegraph (posture change plus ground marker on the lane) so Frost, Stun or a Scout block are real answers.
3. Bosses enter with a shockwave that knocks every player unit back one segment (from World 3 on). The player sees this coming from the enemy base HP threshold shown on the stage card.
4. A boss stage has at least two viable loadout archetypes, verified in playtest (Section 9.5). If only one wins, the boss is retuned.
5. Boss stages drop a Core on first clear, guaranteed, which is the Form III material for the units that world introduces.

| Boss | World | Phase 1 | Phase 2 (60%) | Phase 3 (25%) |
| --- | --- | --- | --- | --- |
| The Compactor | 1 | Slow Colossal-lite, 8 segments, wide swing | Summons 6 Swarm Rustlings every 20 s | Charges: Fast for 5 s, then exhausted 5 s |
| Mother Cap | 2 | Armoured, spore cloud slows Zone 2 | Spawns 3 Armoured guards on each knockback | Heals 10% once at 30% |
| The Clockmaster | 3 | Ranged ticking shots | Airship drops 4 Flying bombers | Rewinds: teleports to Zone 3 and reclaims it |
| Glacier Hart | 4 | Ranged, freezes a zone for 4 s | Ice wall at Zone 2 (your side must break it) | Blizzard: all units -50% speed, 8 s |
| Furnace King | 5 | Colossal, pushes frontline | Lava pulse damages Zone 2 every 15 s | Overheat: +50% attack speed, takes 2x damage |
| The Twin Wardens | 6 | Two bosses, one Armoured one Flying, share no HP | Whichever is alive gains the other's tag | Formation: calls every family once |

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

