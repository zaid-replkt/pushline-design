## 6. Unit system

40 units at launch across 6 roles, every one earned by playing, levelled with XP, and evolved twice into forms that change what it does rather than how hard it hits. The 8-card loadout is the main strategic decision outside battle.

### 6.1 Roles

| Role | Job in the lane | Stat signature | Share of roster |
| --- | --- | --- | --- |
| Scout | Cheap, fast chaff: absorbs a hit, buys time, blocks a boss wind-up | Cost 50-150, cooldown 2-4 s, 1-2 knockback segments | 5 |
| Vanguard | Holds the frontline | Very high HP, 6-10 knockback segments, low damage, slow | 7 |
| Striker | Melee damage, trades with enemy frontliners | High damage, medium HP, 2-3 segments | 8 |
| Ranger | Single-target ranged damage from behind the Vanguard | Range 200+, low HP, 1 segment | 7 |
| Barrage | Area ranged damage against crowds | Area flag, slow attack interval, long range | 6 |
| Breaker | Anti-base and anti-boss burst | Rush trait, 3x damage to bases, long cooldown, expensive | 3 |
| Support | Auras and debuffs: slow, weaken, shield | Little or no damage, medium range | 4 |

### 6.2 Stat model

Every unit is one data row (Section 14.2). Level-1 stats are authored; level L multiplies HP and damage by `1 + 0.08 × (L - 1)`, so level 30 is 3.32x level 1. Cost, cooldown, range, speed and attack interval never change with level; they change only on evolution. This keeps level-ups legible (bigger numbers) and evolutions meaningful (new behaviour).

| Field | Meaning | Typical range |
| --- | --- | --- |
| cost | Cash to deploy | 50-3,000 |
| cooldown\_s | Seconds before the card can be used again | 2-60 |
| hp | Level-1 hit points | 100-6,000 |
| kb | Knockback segments (hp is split evenly) | 1-10 |
| dmg | Level-1 damage per hit | 10-1,200 |
| interval\_s | Seconds between attacks, including wind-up | 0.8-5.0 |
| windup\_s | Portion of interval before the hit lands; interruptible by knockback | 0.2-2.0 |
| range | Attack reach in lane units | 40-320 |
| speed | Lane units per second | 20-80 |
| area | Hits all enemies in range if true | bool |
| traits | List of trait ids with parameters | 0-3 |

### 6.3 Traits

Traits are the counter system. Each enemy carries 1-2 tags (Section 7.1); each unit trait references a tag or applies unconditionally.

| Trait | Effect | Reads on screen as |
| --- | --- | --- |
| Strong vs \[tag\] | 1.5x damage dealt to, 0.5x damage taken from, tagged enemies | Tag icon on the card with a sword |
| Resist \[tag\] | 0.4x damage taken from tagged enemies | Tag icon with a shield |
| Knockback (p%) | Each hit has p% chance to knock the target back one segment regardless of HP | Target lurches |
| Slow (p%, t s) | Hit targets move and attack 30% slower for t s | Blue trail |
| Stun (p%, t s) | Hit targets cannot act for t s; bosses resist to 0.3 s | Stars |
| Pierce | Ignores the Armoured tag's damage reduction | Cracked-shield icon |
| Reach | Attack hits every enemy between the unit and its max range (a line) | Beam |
| Rush | Immune to knockback while in its first HP segment | Charging posture |

### 6.4 Launch roster, starter set and World 1 (level-1 stats)

The first 12 units are fully specified here because the tutorial and World 1 are balanced on them. The remaining 28 are specified in the unit data sheet during production using the same template and the role shares above.

| Unit | Role | Cost | CD s | HP | KB | Dmg | Int s | Range | Speed | Traits | Unlock |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Scrap | Scout | 50 | 2 | 100 | 1 | 20 | 1.0 | 40 | 60 | none | Tutorial |
| Brute | Striker | 150 | 6 | 400 | 2 | 90 | 1.5 | 45 | 50 | none | Tutorial |
| Boulder | Vanguard | 300 | 10 | 1,800 | 6 | 25 | 2.0 | 40 | 30 | none | Tutorial |
| Slinger | Ranger | 250 | 8 | 180 | 1 | 70 | 1.8 | 220 | 45 | none | Stage 1-3 |
| Mortar | Barrage | 600 | 18 | 220 | 2 | 160 | 3.0 | 300 | 30 | area | Stage 1-6 |
| Chanter | Support | 400 | 15 | 300 | 2 | 10 | 2.0 | 180 | 35 | area, Slow 100%, 2 s | Stage 1-10 |
| Ram | Breaker | 900 | 25 | 1,200 | 3 | 400 | 4.0 | 60 | 55 | Rush, 3x vs base | Stage 1-15 |
| Ironhide | Vanguard | 800 | 22 | 4,000 | 8 | 40 | 2.5 | 45 | 25 | Resist Armoured | Stage 1-20 |
| Lancer | Striker | 350 | 9 | 350 | 2 | 150 | 2.2 | 90 | 60 | Strong vs Fast | Stage 1-24 |
| Skyhook | Ranger | 450 | 12 | 200 | 1 | 90 | 1.6 | 240 | 45 | Strong vs Flying | Stage 1-27 |
| Hammerhead | Striker | 700 | 20 | 900 | 3 | 320 | 3.0 | 50 | 40 | Pierce | World 1 boss |
| Lantern | Support | 500 | 16 | 250 | 2 | 0 | 2.0 | 200 | 35 | aura: enemies in range deal -30% | Cog shop |

Unlock sources for all 40: 24 from first clears of specific main stages (fixed, never random), 6 from the Cog shop (earned currency, Section 10), 6 from completing side campaigns, 2 from trials, 2 from the achievement track. No unit is sold for money and no unit comes from a random draw.

### 6.5 Levels, XP and evolutions

- Levels 1-30. XP cost to go from level L to L+1 is `60 × L^1.5` rounded to 10 (level 1→2: 60; 10→11: 1,900; 20→21: 5,370; 29→30: 9,370). Levelling one unit from 1 to 30 costs about 113,000 XP. Section 10 shows the campaign supplies roughly 460,000 XP, enough for an 8-unit core at level 20 plus a third of the roster at mid levels.
- **Form II** unlocks automatically at level 10: +15% HP and damage and one added trait. Example: Boulder II gains Knockback 20%.
- **Form III** unlocks at level 20 plus one Core, a guaranteed first-clear drop from the matching world boss. Form III changes the unit's behaviour: Boulder III becomes an Area attacker that taunts (enemies in range target it first). Form III is where the roster's "new decisions after hour 20" come from.
- No unit is ever obsolete: level scaling is linear, and enemy tags are distributed so early units with the right trait stay useful in Worlds 5-6.

### 6.6 Loadouts

8 unit cards and 2 Commands per loadout, 5 saved presets, and the stage card suggests a preset ("Last used", "Anti-armour") without forcing it. The stage card also shows a coverage check: which enemy tags in the stage your loadout has a Strong-vs or Pierce answer to. That is the main anti-"one solution" tool: the player can see the gap before the loss.

### 6.7 Armory (global upgrades, bought with Cogs)

| Upgrade | Levels | Per level | Max total |
| --- | --- | --- | --- |
| Base plating | 10 | +5% player base HP | +50% |
| Opening purse | 5 | +100 starting cash | +500 |
| Meter coils | 5 | +5% Command Meter charge rate | +25% |
| Cheaper vaults | 5 | -3% Bank upgrade cost | -15% |
| Scavenging | 5 | +5% enemy bounty | +25% |

Armory upgrades are small on purpose: they smooth difficulty for players who are stuck, but the design never assumes them when computing a stage's recommended power.
