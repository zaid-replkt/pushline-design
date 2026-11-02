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
