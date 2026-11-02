## 9. Difficulty and balance model

Difficulty is budgeted per stage against the power a player has if they simply clear everything once, and every stage is proven winnable by at least two loadout archetypes in a headless simulator before a human plays it. This is the mechanism behind the no-grind promise, not a slogan.

### 9.1 Player Power Index (PPI)

PPI at stage s is the level multiplier an 8-card core would have if the player had spent 70% of all XP earnable from first clears before s, spread evenly over 8 units.

```latex
\mathrm{PPI}(s) = 1 + 0.08\,\bigl(L^{*}(s) - 1\bigr), \qquad L^{*}(s) = \max\Bigl\{L : \sum_{k=1}^{L-1} 60\,k^{1.5} \le \tfrac{0.7\,X(s)}{8}\Bigr\}
```

where X(s) is cumulative first-clear XP before s (Section 10.3). The 30% slack is what lets players level units outside their core, try things and still be on curve. When the stage sheet was generated, two refinements proved necessary and are documented in its README: the level multiplier is multiplied by a per-world roster factor (1.0 to 4.5) for the stronger units unlocked by then, and the product is squared, because both HP and damage scale; ETI is likewise HP × DPS. Boss, mid-boss and elite anchors are excluded from ETI and tuned in the simulator.

### 9.2 Enemy Threat Index (ETI)

For each stage the tool sums, over every wave entry, count × effective HP × damage per second, divided by the stage's target duration, and normalises against World 1 Stage 1 = 1.0. Effective HP doubles for Armoured when the reference loadout has no Pierce, and Flying counts only against the reference loadout's anti-air damage. The result is a single number designers see in the stage editor next to the stage's beat.

### 9.3 Target ratios by beat

| Beat | ETI / PPI target | Meaning |
| --- | --- | --- |
| Introduce | 0.60 | On-curve player wins comfortably while learning |
| Test | 0.80 | Wins with a sensible loadout |
| Twist | 0.90 | Wins if the twist is read |
| Pressure | 1.00 | Wins with good timing and bank decisions |
| Checkpoint (boss) | 1.15 | Expected 1-3 attempts |
| Side campaign | 1.05-1.20 | Harder, optional |
| Trials 1-20 | 1.10-1.30 | Rule-bound, optional |
| Trials 21-30 | 1.30-1.50 at World 6 PPI with Form III | Endgame |

### 9.4 Headless simulation gate

Because battles are deterministic at a fixed 30 Hz step, the game's simulation runs without rendering. Every stage must pass this gate in CI before it ships:

1. Three reference loadouts per world: Balanced (2 Vanguard, 2 Striker, 2 Ranger, 1 Barrage, 1 Support), Cheap Spam (Scouts and low-cost Strikers), Siege (Vanguard-heavy with Breakers). Each uses a scripted deploy policy (deploy cheapest affordable counter to the current frontline tag, upgrade Bank when wallet is 80% full and no enemy in Zone 1).
2. Run 200 seeds per loadout at level L\*(s) and 200 at L\*(s) - 3.
3. Pass if: Balanced wins ≥ 70% at L\*; at least one other archetype wins ≥ 40% at L\*; Balanced wins ≥ 25% at L\* - 3; no loadout wins ≥ 98% (the stage is then too easy for its beat); median win time inside the stage's target duration ± 30%.
4. Boss stages additionally require two archetypes ≥ 50% at L\*.

A scripted policy is weaker than a human, so human win rates will sit above these floors. The gate catches one-solution stages and stat walls; it does not replace playtesting.

### 9.5 Playtest process

- Every world goes through two rounds of 8-10 external testers on real phones, portrait, one-handed, with the hand recorded. Metrics: first-clear rate per stage against the 8.2 targets, attempts per clear, time per stage, loadout diversity (distinct cards used across clears), and where fingers go.
- A stage is retuned if its first-clear rate is more than 15 points off target, if more than 60% of clears used the same 6-plus cards, or if the median attempts exceed 3.
- Testers are asked after each boss what they think the boss does. If fewer than 7 of 10 can describe phase 2 correctly, the telegraph is redesigned.

### 9.6 Assists for stuck players

- After 2 losses on one stage: the loss screen's hint becomes specific (names the enemy tag and the player's missing counter) and highlights the matching card in the collection.
- After 4 losses: optional Reinforced Base toggle (+25% base HP, cap of 2 stars for that clear). It is never on by default and never nagged.
- After 6 losses: a free one-time Cog voucher equal to one Armory level, so a player can buy a small permanent edge without grinding.

These assists are the only difficulty scaling in the game. There is no hidden rubber-banding.

## 10. Progression and economy

Four currencies, no energy system, no timers, and a first-clear budget that funds every required upgrade: 459,000 XP, 46 Cores and about 46,000 Cogs from clearing the 270 challenges once. The 30-hour figure is 180 main stages at 6 minutes plus 90 side stages and trials at 8 minutes.

### 10.1 Currencies

| Currency | Scope | Earned from | Spent on | Purchasable? |
| --- | --- | --- | --- | --- |
| Cash | Inside one battle only | Bank income, bounties, Zone 2 bonus, Surge | Units, Bank upgrades | No |
| XP | Persistent | Stage clears (100% first time, 30% on replay), quests, achievements | Unit levels | No |
| Cogs | Persistent | First clears, star thresholds, quests, side campaigns | Armory, 6 shop units, cosmetics | No |
| Cores | Persistent | Boss first clears, side-campaign completion, trials 21-30 | Form III evolutions (1 per unit) | No |

The real-money shop (Section 12) sells cosmetics and the game itself, never any of these currencies.

### 10.2 The 30-hour content budget

| Content | Stages | Minutes per first clear (incl. 1.4 attempts) | Hours | XP per stage | XP total | Cogs total |
| --- | --- | --- | --- | --- | --- | --- |
| World 1 main | 30 | 6 | 3.0 | 300 | 9,000 | 300 |
| World 2 main | 30 | 6 | 3.0 | 600 | 18,000 | 600 |
| World 3 main | 30 | 6 | 3.0 | 1,000 | 30,000 | 900 |
| World 4 main | 30 | 6 | 3.0 | 1,600 | 48,000 | 1,200 |
| World 5 main | 30 | 6 | 3.0 | 2,400 | 72,000 | 1,500 |
| World 6 main | 30 | 6 | 3.0 | 3,400 | 102,000 | 1,800 |
| Side campaigns | 60 | 8 | 8.0 | 1,500 avg | 90,000 | 12,000 |
| Trials | 30 | 8 | 4.0 | 3,000 | 90,000 | 9,000 |
| Star thresholds (30 × 25 stars) |  |  |  |  |  | 15,000 |
| Boss and chapter milestones |  |  |  |  |  | 3,700 |
| **Total** | **270** |  | **30.0** |  | **459,000** | **46,000** |

The 6- and 8-minute figures include the loadout and result screens and a 1.4 attempts-per-clear allowance. Daily and weekly quests (Section 11) add XP and Cogs on top; they are deliberately excluded from this budget so the 30 hours never depend on logging in.

### 10.3 Does the XP budget cover the campaign?

- 8-unit core to level 20 costs 8 × 40,280 = 322,000 XP (Section 6.5 curve, Appendix A). The campaign supplies 459,000, so after the core there are 137,000 XP (30%) for experimenting with other units. This is the 30% slack the PPI formula in Section 9.1 assumes.
- Levelling the full 40-unit roster to 30 would cost about 4.6 million XP. That is intentionally unreachable from first clears; it is the long tail for replayers, fed by 30% replay XP and quests, and the design never requires it.
- Cores: 6 world bosses × 3, 6 mid-bosses × 1, 6 side campaigns × 2, trials 21-30 × 1 = 46. All 40 Form III evolutions are fundable from one pass.

### 10.4 Cog sinks

| Sink | Cost | Total |
| --- | --- | --- |
| Armory, 30 levels | 100 at level 1 rising to 1,500 at level 10 of each track | \~18,000 |
| Shop units (6) | 1,500 / 2,000 / 2,500 / 3,000 / 3,500 / 4,000 | 16,500 |
| Cosmetics (base skins, unit palettes, lane themes) | 300-2,000 each | Open-ended |

Armory plus all shop units is about 34,500 Cogs against roughly 46,000 earned, so a completionist ends with cosmetics money and a player who ignores side content can still afford the shop units.

### 10.5 What is deliberately absent

- No energy or stamina. Stages are replayable without limit.
- No daily caps on XP or Cogs from stages.
- No loot tables for progression items. Every unit, Core and Command has a fixed, visible source shown in the collection screen.
- No stage gated on stars, level or Armory. Recommended power is a hint on the stage card, not a lock.

