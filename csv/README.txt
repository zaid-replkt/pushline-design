PUSHLINE stage sheet v0.1 (2 Nov 2026)

Companion to the Game Design Document (Sections 6-10 and 14.3). One row per stage for all 270 challenges; Units and Enemies tabs are the full launch rosters the stages reference.

How to read the Stages tab

Waves: 'at seconds  Enemy xCount gap seconds [modifiers]'. Triggers: 'condition -> action (once)'. Both map 1:1 to the JSON schema in GDD 14.3; pushline_content.json carries the same data machine-readably.

ETI: Enemy Threat Index = sum over waves of count x HP x damage/interval x tag factor (Armoured 1.6, Flying 1.3, Colossal 1.3, Ranged 1.2, Fast 1.1), triggers at 50% weight, divided by target duration, normalised so stage 1-1 = 0.6 (its beat target). Elite, mid-boss and world-boss anchors are EXCLUDED from ETI and listed in the Anchor column; their tuning is done in the simulator (GDD 9.4).

PPI: Player Power Index = (level multiplier x roster factor)^2. Level multiplier assumes 70% of all first-clear XP from MAIN stages before this one, spread over 8 units (GDD 9.1). Roster factor by world = 1.0 / 1.5 / 2.1 / 2.8 / 3.6 / 4.5 is a designer assumption for how much stronger unlocked units are than the starters; the square is because both HP and damage scale. This refines GDD 9.1, which omitted the roster factor.

Ratio = ETI / PPI; Target ratio is the beat's target from GDD 9.3. Rows are generated to land within about +/-20% of target; the CI simulation gate, not this sheet, decides final numbers.

Side campaigns reuse the matching world's Pressure and Checkpoint stages with the campaign rule, modifiers and counts +5-20%. Trials are rule-driven; their composition is described in words and authored by hand in the editor.

Cells to edit

Everything in blue on the Stages, Units and Enemies tabs is an authored input. Budget tab is formulas only. Enemy base HP = 6,000 + 114,000 x ((index-1)/179)^1.3, x1.5 on world-boss stages. XP per stage by world: 300/600/1,000/1,600/2,400/3,400; side 700-2,400; trials 3,000. Cogs: 10-60 per main stage, 200 per side stage, 300 per trial (star thresholds and milestones in GDD 10.2 are on top of these).

All names are placeholders pending trademark check (GDD 13.4).

