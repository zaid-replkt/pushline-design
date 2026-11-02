## 11. Retention and meta systems

The core loop creates the wish to play the next stage; the systems below give the player reasons to come back tomorrow and goals past the credits. Every item here is additive: nothing in this section is required to finish the 30 hours. Priorities follow the brief: P0 ships at launch, P1 in the first two updates, P2 if data supports it.

### 11.1 First-time experience (P0)

Stages 1-1 to 1-5 are the tutorial and play like real stages. Teaching follows George Fan's PvZ rules: teach by doing, one idea per stage, at most 8 words on screen at once, and visuals that signal function ([GDC 2012 summary](https://gamedeveloper.com/design/gdc-2012-10-tutorial-tips-from-i-plants-vs-zombies-i-creator-george-fan)).

| Stage | Teaches | How | Time from install |
| --- | --- | --- | --- |
| 1-1 | Tap a card to deploy; base HP | Only Scrap and Brute available; enemy base 3,000 HP; cash starts at 600 | First deploy at \~25 s, first win at \~90 s |
| 1-2 | Cash is earned over time; waiting is a choice | Boulder unlocks; enemies arrive in two pulses with a visible gap | \~3 min |
| 1-3 | Bank upgrade | Bank button pulses once when affordable; enemy pressure is low; Slinger unlocks after | \~5 min |
| 1-4 | Blast and the Command Meter | Meter starts at 90%; a Swarm wave arrives that Blast clears in one tap | \~7 min |
| 1-5 | Knockback and the Fast tag; Zone 2 | One Fast Rustling runs past the frontline unless blocked; capturing Zone 2 shows the income bonus | \~9 min |

After 1-5: first daily reward is granted, the collection screen opens once to show the 40 silhouettes and where the next unit comes from, and the next three stages' rewards are visible on the map. Every tutorial prompt is skippable with one tap for returning players (a "Skip tutorial" option appears if the save shows a prior completion of 1-5).

### 11.2 Daily and repeat engagement

| Feature | Priority | Spec |
| --- | --- | --- |
| Daily login calendar | P0 | 7-day track, resets each week: Day 1 200 Cogs; Day 2 1,500 XP; Day 3 300 Cogs; Day 4 Armory voucher (1 level, any track); Day 5 3,000 XP; Day 6 500 Cogs; Day 7 one unit choice from a rotating pair that is also earnable in the campaign |
| Streak | P0 | Consecutive-day counter with one free missed day per week; a 14-day streak grants a cosmetic, 30-day another; streaks never reset XP or Cogs already earned |
| Daily quests | P0 | 3 per day, all completable in one 10-minute session: "Win 2 stages", "Deploy 15 Vanguards", "Capture Zone 3 once". Reward 100 Cogs + 500 XP each |
| Weekly quests | P0 | 3 per week, larger: "Earn 20 stars", "Win a stage with 6 cards", "Clear a side-campaign stage". Reward 600 Cogs + 3,000 XP each |
| First win of the day | P0 | 2x XP on the first victory each day |
| Reward hub | P0 | One screen listing claimable rewards and the next unlock in each track; a badge on the map, never a popup on launch |
| Daily challenge stage | P1 | A rotating main stage with one elite modifier and a bespoke star condition; Cogs reward; 24 h rotation |
| Return bonus | P1 | Away 7+ days: a catch-up pack of XP scaled to the player's current world and a "what changed" card |
| Push notifications | P2 | Opt-in only, asked after the first boss kill, at most 2 per week, only for new content or a claimable reward |

### 11.3 Long-term goals

| Feature | Priority | Spec |
| --- | --- | --- |
| Achievements | P0 | 120 at launch across campaign, mastery ("Win 1-30 without Commands"), collection and quirk categories; each pays Cogs; two award units (Section 6.4) |
| Collection | P0 | All 40 units with silhouettes, source, forms and a "try in sandbox" button that opens a practice lane against a dummy wave |
| Enemy codex | P0 | Every enemy met: tags, behaviour in plain words, which of your units counter it |
| Stage mastery | P1 | Revisit any stage with a random bonus condition for Cogs; no XP, so it is never a grind path |
| Completion tracker | P0 | Per-world percentage: stages, stars, units, Cores, achievements |

### 11.4 LiveOps cadence (post-launch)

| Cadence | Content | Priority |
| --- | --- | --- |
| Weekly | Rotating challenge set (3 stages with modifiers), fresh daily challenge seeds | P1 |
| Monthly | Themed event: 8-10 stages, a new enemy variant, one event unit earnable by playing, a free reward track with 20 tiers | P1 |
| Quarterly | New world or side campaign (30 or 10 stages), 4-6 units, new Command | P1 |
| Any time | Balance patches driven by Section 16 metrics | P0 |

Event units return in later events or move to the Cog shop within 6 months, so missing an event never locks content permanently.

### 11.5 First week, as designed

- Day 1: tutorial, 10-15 stages, 4-6 units, first daily reward, Zone 2 understood, Mortar unlocked.
- Days 2-3: daily quests become routine, Armoured appears, first Cog spend in the Armory, mid-boss of World 1.
- Days 4-7: The Compactor killed, first Core, side campaign opens, Day 7 unit chosen, World 2.
- Day 30 and after: Worlds 4-5, Form III evolutions, trials, the first monthly event.

### 11.6 What we do not copy from Roblox or the genre

- No AFK or idle rewards. Playtime rewards are tied to stages won, not minutes open.
- No streak punishment beyond losing the cosmetic pace; one missed day per week is free.
- No quests that require spending or watching ads.
- No mandatory daily chores: a player who never opens the quest screen still gets the full 30 hours.
- No notification before opt-in and no "your base is under attack" fiction.
- No gacha, no paid units, no random progression drops (Section 12).

## 12. Monetization

Recommended model: free download with a one-time **Full Campaign** unlock after World 2, plus cosmetics; no ads inside battles, no currency sales, no gacha, no energy. This is the only model consistent with C5 and with the no-grind guarantee, and it is a business decision the team should confirm before production (Section 17).

| Item | Price (USD, indicative) | What it is | What it is not |
| --- | --- | --- | --- |
| Full Campaign | 6.99 one-time | Worlds 3-6, side campaigns 3-6, trials 11-30 | Not a power purchase; Worlds 1-2 (60 stages, \~6 h) are free and complete |
| Cosmetic packs | 1.99-4.99 | Base skins, lane themes, unit palettes, victory animations | No stats |
| Supporter pack | 9.99 | All launch cosmetics plus a name in the credits | No stats |
| Rewarded ad (optional) | free | One per day, outside battle, for 100 Cogs; off entirely in the paid tier | Never required for a quest or a stage |

Rules that bind every future offer:

1. Nothing that changes a stat, a unit, a Core, XP or Cogs is sold for money, including "time savers".
2. No interstitial ads anywhere. No ad can be placed between a loss and a retry.
3. Event units are earned by playing the event; the event's cosmetics may be sold.
4. The paywall is a stage card like any other, shown after the World 2 boss with the full remaining content list, and it never interrupts a battle or a reward screen.

Alternative considered: premium up-front at 4.99. Rejected because the free first two worlds are the acquisition funnel and double as the retention test (Section 16).

