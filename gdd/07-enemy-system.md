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
