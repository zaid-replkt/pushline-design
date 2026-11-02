## 14. Technical design

The architecture has one non-negotiable: a deterministic, fixed-step battle simulation with no dependency on rendering, so the same code runs the game on a phone, the headless balance gate in CI (Section 9.4), and pause/resume state saves. Everything else is conventional mobile 2D.

### 14.1 Engine

Recommendation: **Unity 6 (C#), 2D URP**, for its 2D skeletal animation tooling, addressables for content delivery, mature iOS/Android pipeline and the size of the hiring pool. Godot 4 is the fallback if licensing or team preference argues for it; nothing in this design depends on Unity-specific features. Decision owner and date are open (Section 17).

### 14.2 Simulation core

- Fixed 30 Hz tick; all gameplay values are integers or fixed-point; RNG is a seeded xorshift per battle. Rendering interpolates between ticks at the display rate.
- The `Battle` object takes `(StageDefinition, Loadout, UnitLevels, Armory, seed)` and exposes `Tick(input)`; input is a list of `{tick, action, cardIndex|commandIndex|bank}`. A recorded input list replays a battle exactly, which is also the bug-report format.
- Entities are arrays of structs (units, enemies, projectiles, zones) iterated by system (movement, targeting, attack, knockback, status, zones, triggers, economy). No per-entity allocations during a battle.
- Headless mode compiles the same assembly without the presentation layer; the CI gate runs about 1,200 battles per stage in under a minute on a build agent.

### 14.3 Data-driven content

All content is data; the only code per stage is the shared trigger interpreter. Designers edit in an in-engine stage editor with a live ETI readout and a "simulate 50" button.

```json
{
  "id": "w2_s07",
  "world": 2,
  "beat": "twist",
  "enemyBaseHp": 24000,
  "startCash": 0,
  "startBankLevel": 1,
  "targetDurationS": 240,
  "stars": ["win", "baseAbove50", {"type": "maxCards", "value": 6}],
  "waves": [
    {"at": 5,   "spawn": "rustling_runner", "count": 3, "gapS": 1.0},
    {"at": 25,  "spawn": "sporefolk_capguard", "count": 2, "gapS": 4.0, "mods": ["hardened"]},
    {"at": 60,  "spawn": "rustling_swarm", "count": 10, "gapS": 0.4}
  ],
  "triggers": [
    {"when": {"zoneCaptured": {"zone": 2, "by": "player"}}, "do": {"spawn": "sporefolk_capguard", "count": 4, "gapS": 2.0, "mods": ["armoured_swarm"]}},
    {"when": {"enemyBaseHpBelow": 0.5}, "do": {"spawn": "sporefolk_elder", "count": 1}},
    {"when": {"zoneLost": {"zone": 1}}, "do": {"spawn": "rustling_runner", "count": 3, "gapS": 0.5}, "once": true}
  ],
  "hints": {
    "lossToTag": {"armoured": "Capguards shrug off normal hits. Hammerhead pierces armour."}
  },
  "rewards": {"xp": 600, "cogs": 20, "firstClear": {"unit": null, "cores": 0}}
}
```

Units, enemies, Commands, modifiers, quests, achievements and the login calendar follow the same pattern: one JSON (or ScriptableObject) per record, validated by schema in CI, hot-reloadable in the editor. Content ships through addressables so a world or event can be added without a store update.

### 14.4 Save and cloud

- Local save is a versioned JSON blob (profile, unlocks, levels, stars, currencies, quests, settings, in-progress battle state) written atomically on every reward screen and on app background. Migrations are forward-only with a schema version field.
- Cloud sync through Game Center / Google Play Games with last-write-wins and a conflict screen that shows both saves' progress. No account creation required.
- An in-progress battle is saved as `(StageDefinition id, seed, input list, tick)` and resumed by replaying; the save is small and cannot desync.

### 14.5 Performance and device targets

| Target | Value |
| --- | --- |
| Frame rate | 60 fps on iPhone 12 / Pixel 6 class and newer; 30 fps floor on iPhone SE 2 / 3 GB Android devices (Android's stated minimum for the core loop) |
| Battle entities | 80 units plus 60 enemies plus 200 particles at 2x speed without frame drops on the floor devices |
| Cold start to map | under 4 s on target devices; under 8 s on floor devices |
| Install size | under 150 MB at launch; worlds 3-6 as addressable downloads of about 25 MB each |
| Memory | under 600 MB peak on floor devices |
| Crash-free sessions | 99.5% internal target; Android vitals bad-behaviour thresholds (1.09% crash, 0.47% ANR) are hard release blockers |
| Battery | one 10-minute session under 4% on reference devices; frame cap drops to 30 fps in menus |

### 14.6 Analytics and telemetry

Events (Section 16.3) go to a single analytics pipeline (GameAnalytics or Firebase; decision open) with a 1% sampled full-battle input log for balance work. Crash reporting through Crashlytics or equivalent. All telemetry respects platform tracking consent; no third-party ad SDK in the paid tier.

### 14.7 Platform specifics

- Portrait lock on phones. On tablets and Android 16+ large screens the OS may ignore orientation locks ([Android form factors](https://developer.android.com/games/develop/multiplatform/make-your-game-compatible-with-all-form-factors)), so the layout is defined by size class: the lane keeps its 70%-width rule and the card bar pins to the bottom in any aspect ratio, with letterboxing only beyond 2.4:1.
- Safe areas (Dynamic Island, home indicator, camera cut-outs) are respected by anchoring HUD elements to edges rather than scaling, per Apple's guidance.
- Localization from day one: all strings in tables, no text in textures, 8 launch languages (EN, JA, KO, DE, FR, ES, PT-BR, ZH-Hans), given Battle Cats' revenue concentration in Japan.
