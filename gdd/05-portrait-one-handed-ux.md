## 5. Portrait one-handed UX

The rule is simple: everything the player must tap during a battle lives in the bottom 40% of the screen, inside the thumb arc of the hand holding the phone, and nothing in the top 60% is ever required. The reference device is a 6.1-inch phone at 390 × 844 pt; layouts are defined as percentages of safe-area height so they scale from 16:9 tablets to 20:9 phones.

### 5.1 Screen zones (portrait, bottom to top)

| Zone | Height | Contents | Required taps? |
| --- | --- | --- | --- |
| Card bar | 20% (2 rows × 4 cards, each ≥ 64 × 64 pt) | 8 unit cards: portrait, cost, cooldown sweep, dimmed when unaffordable | Yes, primary |
| Command row | 10% | 2 Command buttons (72 pt) flanking the Bank upgrade button (72 pt), meter and wallet readouts between them | Yes |
| Status strip | 6% | Cash counter (large), Bank level, speed toggle, pause | Speed and pause only |
| Battlefield | 58% | Lane viewport, lane bar on the right edge (full lane, zones, base HPs) | No. Optional drag to peek |
| Top safe area | 6% | Enemy base HP bar, stage name, star-condition tracker | No |

### 5.2 Hand and reach

- Default layout is for the right thumb: Command buttons and Bank sit left-of-centre so the thumb's natural arc covers cards first, Commands second. A one-toggle mirror layout flips it for the left hand. Detected automatically from the first three taps' positions, overridable in settings.
- All required targets are ≥ 64 pt; speed and pause are 44 pt (the Apple minimum) because they are infrequent. No required target sits within 24 pt of a screen edge, so palm rejection and gesture bars do not interfere.
- No gesture is required beyond single tap. Long-press on a card opens its stat sheet as a read-only overlay; releasing closes it. No drag-to-deploy, no swipe, no pinch.
- Card order in the loadout is the player's choice, so the two cards they spam most can sit in the bottom-right corner, the easiest reach.

### 5.3 Readability on a narrow screen

- Lane width on screen is 70% of the display width; units are drawn at 48-96 pt tall so a stack of 12 still reads. Beyond 12 units in one spot, extras are drawn behind with a counter badge.
- Enemies carry a trait icon above their head (Section 7.1) and a colour-independent silhouette rule: armoured enemies are wide, fliers are raised with a shadow, fast enemies lean. Colour is never the only signal.
- Health bars appear only for bosses, elites and the two bases; ordinary units flash on hit and show knockback pips. This keeps the lane clean at 2x speed.
- Damage numbers are off by default (toggle in settings) because they obscure the lane in portrait.
- The lane bar on the right edge is the portrait replacement for seeing the whole stage: 8 pt wide, with zone segments, two frontline markers, boss icon and both base HP fills.

### 5.4 Interruption and resume

- Incoming call, app switch or lock: battle pauses instantly and the state is written to disk. Returning restores the exact simulation tick. Battles are deterministic (seeded RNG, fixed 30 Hz simulation step) so this is a state save, not a replay.
- A battle abandoned for more than 24 hours is forfeited with no penalty beyond a retry.

### 5.5 Out-of-battle screens

World map, loadout, upgrade shop, collection, quests and rewards are all scrolling portrait lists with the primary action pinned to the bottom 15% of the screen. Horizontal carousels are avoided except the world map's world selector, which also has a tap-to-advance arrow. Every screen is reachable in at most two taps from the map, and "Next stage" on the result screen goes straight to the loadout of the next stage.
