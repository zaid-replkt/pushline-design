# PUSHLINE design bundle (v0.1, 2 Nov 2026)

Everything needed to build the game. All names are placeholders pending trademark check (GDD 13.4).

| File | What it is |
| --- | --- |
| `pushline_gdd.md` | Game Design Document (Markdown export of the live doc, 79 KB) |
| `gdd/` | The same GDD split into one file per section (see `gdd/INDEX.md`) for readers that truncate long documents |
| `diagrams.md` | Both diagrams as text, so nothing depends on viewing the PNGs |
| `pushline_content.json` | 40 units, 72 enemies, 270 stages with waves and triggers, in the GDD Section 14.3 schema |
| `csv/stages.csv` | One row per stage, all 270 (waves, triggers, stars, rewards, unlocks, threat index) |
| `csv/units.csv` | 40 units with stats, unlock source, Form II and Form III |
| `csv/enemies.csv` | 72 enemies with stats, tags, intro stage |
| `csv/bosses.csv` | 12 bosses with phases |
| `csv/side_campaigns.csv`, `csv/trials.csv` | Rules and rewards |
| `csv/budget.csv` | XP / Cogs / Cores / hours totals per world |
| `csv/README.txt` | How to read the stage data (ETI, PPI, generation rules) |
| `battle_loop.png` | GDD Section 4 diagram |
| `production_timeline.png` | GDD Section 15 diagram |

## Direct download (raw)

```
https://raw.githubusercontent.com/zaid-replkt/pushline-design/main/pushline_gdd.md
https://raw.githubusercontent.com/zaid-replkt/pushline-design/main/pushline_content.json
https://raw.githubusercontent.com/zaid-replkt/pushline-design/main/csv/stages.csv
https://raw.githubusercontent.com/zaid-replkt/pushline-design/main/csv/units.csv
https://raw.githubusercontent.com/zaid-replkt/pushline-design/main/csv/enemies.csv
https://raw.githubusercontent.com/zaid-replkt/pushline-design/main/csv/bosses.csv
https://raw.githubusercontent.com/zaid-replkt/pushline-design/main/csv/side_campaigns.csv
https://raw.githubusercontent.com/zaid-replkt/pushline-design/main/csv/trials.csv
https://raw.githubusercontent.com/zaid-replkt/pushline-design/main/csv/budget.csv
https://raw.githubusercontent.com/zaid-replkt/pushline-design/main/battle_loop.png
https://raw.githubusercontent.com/zaid-replkt/pushline-design/main/production_timeline.png
```

**Recommended for agents:** `git clone https://github.com/zaid-replkt/pushline-design` and read from disk. Web readers often truncate `pushline_gdd.md` and `pushline_content.json`; the clone does not.

## Schema notes (for an agent)

- A stage's `waves[]` entries are `{at, spawn, count, gapS, mods?}`; `spawn` resolves against `enemies[].id`.
- `triggers[]` are `{when, do, once?}`; `when` is one of `zoneCaptured{zone,by}`, `zoneLost{zone}`, `enemyBaseHpBelow`; `do` is `spawn{...}`, `hazard` or `shockwave`.
- Threat (ETI) and power (PPI) definitions are in `csv/README.txt` and GDD 9.1-9.3. Boss, mid-boss and elite anchors are excluded from ETI and tuned in the simulator (GDD 9.4).
