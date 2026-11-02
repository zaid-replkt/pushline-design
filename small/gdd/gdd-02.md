## 2. Research summary

Three findings change the earlier brief: The Battle Bricks does run a gacha and stat-multiplied replays, so it is a looser reference than assumed; no shipped Battle Cats-like plays in portrait, so the vertical lane is unproven and must be prototyped first; and the brief's retention targets sit in the top decile of published mobile benchmarks, so they are stretch goals, not baselines. Figures below are as of 2 November 2026; access caveats are noted where a source could not be opened directly.

### 2.1 The Battle Bricks (Roblox, Tumore / solo developer)

| Fact | Value | Source |
| --- | --- | --- |
| Scale | 147.2 M visits, 320.7 K favourites, 6.94 M unique players, typical concurrency 1.9-2.1 K, average session 20.5 min, all-time peak 40,066 on 19 Jun 2026 (Chapter 5 launch) | [rowatcher](https://rowatcher.com/games/3913007563/the-battle-bricks), [rotrends](https://rotrends.com/game/3913007563) |
| Rating | 186,260 likes / 33,817 dislikes (84.6%) | [Rolimon's](https://www.rolimons.com/game/10834586502) |
| Campaign | 5 main chapters of 30 stages (6 and 7 planned), challenge stages at 5/15/25, bosses at 10/20, final boss at 30; 13 sub-chapters totalling 226 stages; replays pay 35% XP | [namu wiki, main chapters](https://www.namu.moe/w/The%20Battle%20Bricks/%EB%A9%94%EC%9D%B8%20%EC%B1%95%ED%84%B0) |
| Difficulty | Star tiers multiply enemy stats, base HP and unit costs by 1x / 1.5x / 2x; Casual, Normal and Tumore modes; 1x-6x enemy multiplier slider for bonus XP | same |
| Battle economy | In-battle bank levels to 8, six bank types (Investment, Powerhouse, Detonator, Ignition, Bloodaltar); eight cannon types on a 45 s recharge; out-of-battle base upgrades bought with XP | [namu wiki, banks](https://www.namu.moe/w/The%20Battle%20Bricks/%EC%9D%80%ED%96%89), [cannons](https://www.namu.moe/w/The%20Battle%20Bricks/%ED%94%8C%EB%A0%88%EC%9D%B4%EC%96%B4%EC%9D%98%20%EB%8C%80%ED%8F%AC) |
| Units | About 90-100 battlers in five rarities, each with an alt form at level 10; +20% of base stat per level; level cap rises +5 per chapter cleared; anti-trait units deal +25% / take -25% versus Red, Death, Angel, Zombie | [namu wiki, battlers](https://www.namu.moe/w/The%20Battle%20Bricks/%EB%B0%B0%ED%8B%80%EB%9F%AC) |
| Gacha | 100-200 Bricks per pull at 70% Rare / 25% Super Rare / 5% Uber; Uberfest doubles Uber odds; no game passes, 5 developer products | [namu wiki, systems](https://www.namu.moe/w/The%20Battle%20Bricks/%ED%8A%B9%EC%A7%95%20%EB%B0%8F%20%EA%B2%8C%EC%9E%84%20%EC%8B%9C%EC%8A%A4%ED%85%9C), [Roblox game-pass API](https://apis.roblox.com/game-passes/v1/universes/3913007563/game-passes) |
| Anti-farm rules | Boss alive = your base cannot be damaged; since 13 Sep 2025 the enemy base is invulnerable until the scripted spawn cycle finishes | same |
| Retention systems | Daily login streak paying Bricks (resets after 20 h since Chapter 5), badges, anniversary and Uberfest events; no quest system found | same |

Two earlier claims in the brief do not survive this: Battle Bricks is not gacha-free, and its star system is stat inflation of the same stages. We keep its loadout, bank, cannon, trait and chapter structure and drop those two. Loadout size (8) appears only in secondary sources and is unverified on the fan wiki.

### 2.2 The Battle Cats (PONOS)

- Structure: Empire of Cats is 3 chapters of 48 stages that reuse the same stage designs at rising difficulty; Into the Future and Cats of the Cosmos repeat that pattern; Stories of Legend, Uncanny Legends and Zero Legends add dozens of sub-chapters ([Wikipedia](https://en.wikipedia.org/wiki/The_Battle_Cats)).
- In-battle economy: Worker Cat with 8 levels per battle, cost rising per level; Cat Cannon with a 10-bar charge and infinite range; hitting the enemy base often triggers stronger spawns ([Worker Cat](https://battle-cats.fandom.com/wiki/Worker_Cat), [Cat Cannon](https://battle-cats.fandom.com/wiki/Cat_Cannon)).
- Monetisation: Cat Food premium currency for gacha (150 per roll), energy refills and continues; energy gates stage attempts ([Cat Food](https://battle-cats.fandom.com/wiki/Cat_Food)).
- Scale: over $700 M lifetime revenue by Aug 2024, 68% from Japan; 78 M downloads ([Sensor Tower via WN Hub](https://wnhub.io/news/finance/item-44495)). Landscape-only; the orientation is visible in store screenshots but we found no text source stating it.

### 2.3 Portrait precedents

- Clash Royale gives the player's half of the arena and the card hand the bottom roughly three-quarters of the screen and was built for one-thumb play ([Game Developer](https://www.gamedeveloper.com/design/breaking-down-supercell-s-next-hit-clash-royale)). Castle Crush rotates the lane battler vertical with three lanes and castles at each end ([Level Winner](https://www.levelwinner.com/?p=8275)). Rush Royale puts the player's board at the bottom and the opponent's mirrored at the top ([Pocket Gamer](https://www.pocketgamer.com/rush-royale/rush-royale-hands-on-mixing-a-bunch-of-great-genres-together)).
- No shipped single-lane, base-versus-base auto-battler in the Battle Cats mould uses a vertical lane. PUSHLINE's layout is therefore a design bet to be validated in the first prototype (Section 15).

### 2.4 Retention benchmarks

| Metric | All-genre median | Top 25% | Top 10% | Strategy median (2024 data) |
| --- | --- | --- | --- | --- |
| D1 | \~22% | just over 30% | \~40% | 19-21% |
| D7 | just under 4% | 6-7% | \~12% | 3.2-3.6% |
| D30 (D28 for genre) | 0.7-0.8% | 1.6-1.8% | \~4% | 0.66-0.77% |
| Session length | 3.1-3.5 min | \~5.2 min |  | 5.3-5.6 min |
| Sessions per day | 3.8-3.9 | 5.3-5.7 |  | 4.2-4.4 |

Sources: [GameAnalytics 2026 Mobile & PC Gaming Benchmarks](https://investgame.net/wp-content/uploads/2026/01/2026-01-27-2026-mobile-pc-benchmarks_compressed.pdf) (2025 data, 16,262 games), [GameAnalytics Mobile retention benchmarks 2026](https://investgame.net/wp-content/uploads/2026/01/2026-01-20-Mobile_retention_benchmarks_2026.pdf), [GameAnalytics 2025 benchmarks](https://gameanalytics.com/reports/2025-mobile-gaming-benchmarks) for the genre split. GameAnalytics notes that top studios keep data private, so public figures skew low. The brief's targets (D1 30-35%, D7 8-10%, D30 2-3%) are top-quartile to top-decile; Section 16 keeps them as stretch targets and adds floor targets.

### 2.5 Platform guidelines used in this design

- Apple: 44 × 44 pt default control size, 28 pt minimum, frequent controls near the thumbs, secondary controls at the top, respect safe areas, teach through play ([HIG: Designing for games](https://developer.apple.com/design/human-interface-guidelines/designing-for-games), [HIG: Game controls](https://developer.apple.com/design/human-interface-guidelines/game-controls)).
- Android: core loop at a minimum of 30 fps and 60 fps or more for reaction-based games on capable devices; keep game state across rotation and resize ([Android game quality](https://developer.android.com/quality/technical)). Android vitals flags user-perceived crash rates above 1.09% and ANR above 0.47% ([Android vitals](https://developer.android.com/games/optimize/vitals)).

### 2.6 Level-design references

The campaign template in Section 8.2 is built from three sources: Nintendo's four-step introduce / develop / twist / conclude structure ([Nintendo Life on Hayashida's GDC talk](https://www.nintendolife.com/news/2015/03/video_nintendos_four_step_stage_design_is_why_you_love_super_mario_games_so_much)), George Fan's tutorial rules from Plants vs. Zombies ([Game Developer](https://gamedeveloper.com/design/gdc-2012-10-tutorial-tips-from-i-plants-vs-zombies-i-creator-george-fan)), and the Kingdom Rush campaign analysis of one-concept-per-level with each new enemy targeting a known weakness ([Game Developer](https://gamedeveloper.com/design/kingdom-rush---the-wonderful-campaign-level-design)).

