# PUSHLINE design bundle (v0.1, 2 Nov 2026)

Everything needed to build the game. All names are placeholders pending trademark check (GDD 13.4).

| File | What it is |
| --- | --- |
| `pushline_gdd.md` | Game Design Document (Markdown export of the live doc) |
| `pushline_content.json` | 40 units, 72 enemies, 270 stages with waves and triggers, in the GDD Section 14.3 schema |
| `pushline_stage_sheet.xlsx` | Same content as a workbook: README, Budget, Stages, Units, Enemies, Bosses, Side campaigns, Trials |
| `battle_loop.png` | GDD Section 4 diagram |
| `production_timeline.png` | GDD Section 15 diagram |

## Direct download (raw)

```
https://raw.githubusercontent.com/zaid-replkt/pushline-design/main/pushline_gdd.md
https://raw.githubusercontent.com/zaid-replkt/pushline-design/main/pushline_content.json
https://raw.githubusercontent.com/zaid-replkt/pushline-design/main/pushline_stage_sheet.xlsx
https://raw.githubusercontent.com/zaid-replkt/pushline-design/main/battle_loop.png
https://raw.githubusercontent.com/zaid-replkt/pushline-design/main/production_timeline.png
```

Or `git clone https://github.com/zaid-replkt/pushline-design`.

## Schema notes (for an agent)

- A stage's `waves[]` entries are `{at, spawn, count, gapS, mods?}`; `spawn` resolves against `enemies[].id`.
- `triggers[]` are `{when, do, once?}`; `when` is one of `zoneCaptured{zone,by}`, `zoneLost{zone}`, `enemyBaseHpBelow`; `do` is `spawn{...}`, `hazard` or `shockwave`.
- Threat (ETI) and power (PPI) definitions are in the workbook's README tab and GDD 9.1-9.3. Boss, mid-boss and elite anchors are excluded from ETI and tuned in the simulator (GDD 9.4).
