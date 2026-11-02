## 15. Production plan

About 13 months from a 6-week portrait prototype to global launch with a core team of 8, provided the prototype gate passes; the single biggest schedule risk is the vertical lane itself, which is why it is tested before anything else is built. Estimates assume the stage editor and CI balance gate exist before content production starts.

![Production timeline](production_timeline.png)

The dashed line is the only gate that can kill the concept; everything after it is schedule risk, not design risk.

### 15.1 Phases and gates

| Phase | Weeks | Delivers | Gate to leave the phase |
| --- | --- | --- | --- |
| 0. Portrait prototype | 6 | Grey-box vertical lane, 6 units, 8 enemies, 5 stages, zones, Blast, Bank; playable one-handed on device | 10 external testers: 8 of 10 can play 1-5 one-handed without instruction; 7 of 10 say they would play more; median first-win under 2 min |
| 1. Vertical slice | 12 | World 1 complete with final art for 12 units and the Rustlings, tutorial, FTUE, results, map, save, stage editor, headless gate in CI | World 1 first-clear rates within 15 points of Section 8.2 targets across 10 testers; 60 fps on reference devices |
| 2. Production | 28 | Worlds 2-6, side campaigns, trials, 40 units with forms, all bosses, retention layer (P0), Armory, shop, cloud save, localization | All 270 stages pass the CI gate; two playtest rounds per world done; P0 list complete |
| 3. Soft launch | 8 | Live in 2-3 test markets (e.g. Canada, Philippines, Finland); analytics, A/B on tutorial length and Day-7 reward; balance patches | D1 ≥ 28%, D7 ≥ 6% in soft-launch cohorts; crash-free ≥ 99.5%; World 2 boss conversion to Full Campaign measured |
| 4. Global launch | 2 | Store launch, first monthly event ready, LiveOps calendar for 6 months |  |

### 15.2 Team

| Role | Count | Notes |
| --- | --- | --- |
| Producer / game director | 1 | Owns this document and the balance targets |
| Gameplay engineer | 2 | Simulation core, presentation, platform |
| Tools engineer | 1 | Stage editor, CI gate, content pipeline; joins Phase 1 |
| Level designer | 2 | One from Phase 1, two in Phase 2 |
| Character artist and animator | 1 + 1 (contract) | 40 units × 3 forms, 72 enemies, 18 bosses |
| Environment and UI artist | 1 | 6 worlds, HUD, map, collection |
| Audio | contract | 14 tracks, SFX library |
| QA | 1 | Device matrix, regression, playtest coordination |

### 15.3 Content velocity assumptions

- Stages: with the editor and gate, one level designer tunes about 8 main stages or 5 boss/trial stages per week. 180 main stages at 8 per week is 22.5 designer-weeks; 60 side stages and 30 trials at 5 per week is 18 designer-weeks; bosses and retunes add roughly 10. That is about 50 designer-weeks against 56 available from two designers over the 28-week production phase, so only 10% slack; a third designer for the final 12 weeks restores about 25%.
- Units: a fully animated base unit takes about 2.5 artist-days; Form II about 0.5 day; Form III about 1.5 days. 40 units is roughly 180 artist-days, or 36 weeks for one artist, so the contract animator is on the critical path from Phase 1.
- Enemies: 72 enemies at 1.5 days plus 18 bosses at 5 days is about 200 artist-days, split between the character artist and the animator.

### 15.4 Playtest cadence

Weekly internal play sessions from Phase 0; external one-handed device tests at every gate and after each world in production; a standing panel of 20 testers recruited from the prototype cohort. Every test records the holding hand and a screen capture so reach problems are seen, not reported.

### 15.5 Post-launch

The first six months follow the LiveOps cadence in Section 11.4 with one quarterly content drop (a 7th world or two side campaigns) already in production during soft launch, so that launch week does not drain the pipeline.

## 16. KPIs and success criteria

Two tiers of targets: floors that must be met in soft launch to proceed to global launch, and stretch targets taken from the brief that sit in the top quartile to top decile of public benchmarks (Section 2.4). Public Roblox statistics say nothing about 30-hour retention, so the depth metrics below are the only evidence that will.

### 16.1 Retention and engagement

| Metric | Floor (soft launch) | Stretch (brief) | Public median for context |
| --- | --- | --- | --- |
| D1 retention | 28% | 30-35% | \~22% |
| D7 retention | 6% | 8-10% | \~4% |
| D30 retention | 1.5% | 2-3% | \~0.7% |
| Session length | 6 min | 8 min | 3.1-3.5 min (strategy 5.3-5.6) |
| Sessions per day | 3 | 4 | 3.8-3.9 |
| Crash-free sessions | 99.5% | 99.7% | Android bad-behaviour threshold 98.9% |

### 16.2 Funnel and depth

| Metric | Target |
| --- | --- |
| Install to first deploy | 95% within 60 s |
| Stage 1-1 completion | 90% of installs |
| Tutorial (1-5) completion | 75% of installs |
| World 1 boss cleared | 35% of installs |
| World 2 boss cleared (paywall reached) | 18% of installs |
| Full Campaign conversion | 8% of players who reach the paywall (open question; set from soft launch) |
| Players reaching 5 / 10 / 20 / 30 h | 20% / 10% / 4% / 1.5% of installs |
| Attempts per first clear, campaign average | 1.3-1.6 |
| Stages with first-clear rate off target by more than 15 points | 0 at global launch |
| Loadout diversity | No single card in more than 70% of winning loadouts per world; at least 25 distinct units in winning loadouts by World 4 |
| Daily quest completion among D7 players | 40% (a measure of routine, not a goal to force) |

### 16.3 Instrumentation (minimum event set)

`install`, `tutorial_step`, `stage_start`, `stage_end` (result, duration, attempts, loadout, bank level reached, zones captured, commands used, cause of loss), `unit_unlock`, `unit_level`, `unit_evolve`, `armory_buy`, `cog_spend`, `quest_complete`, `login_reward_claim`, `paywall_view`, `purchase`, `assist_toggle`, `session_start` with holding-hand estimate, `crash`. Every `stage_end` carries the stage's beat and target ETI/PPI so balance dashboards can be built without joins.

### 16.4 Decision rules

- A floor missed in soft launch by more than 20% relative (D1 under 22%, say) delays global launch by one balance cycle (4 weeks) and triggers a tutorial and World 1 review.
- If fewer than 10% of installs reach 10 hours, the content budget is the problem, not the retention layer; the review starts at Section 8.2 targets and loss causes, not at rewards.

## 17. Risks and open questions

### 17.1 Risks

| Risk | Likelihood | Impact | Mitigation |
| --- | --- | --- | --- |
| The vertical lane does not read or feel good in portrait; no shipped game proves it | Medium | Fatal to the concept | Phase 0 is only this; a failed gate means revisiting a 3-lane Castle Crush layout or a landscape-with-portrait-menus fallback, before any art is made |
| Momentum zones add complexity without changing decisions | Medium | Hook becomes decoration | Prototype with zones off versus on; keep only if testers describe zone fights unprompted |
| 270 stages ship under-tuned | Medium | Breaks pillars 2 and 3 | CI gate blocks untested stages; velocity assumptions hold 10-25% slack depending on a third designer (Section 15.3) |
| Players perceive the Full Campaign unlock as a paywall on a "free" game | Medium | Reviews, conversion | Show the full remaining content list on the paywall; keep Worlds 1-2 complete; test price points in soft launch |
| Genre is small outside Japan; Battle Cats earns 68% of its revenue there | High | Revenue | Japanese localization and culturally neutral art from day one; evaluate Japan as a soft-launch market |
| Solo-only with no social features limits organic growth | High | Acquisition | Asynchronous challenge sharing (seed codes for trials) as a P1 feature; no multiplayer dependency ever |
| Art pipeline is the critical path (40 units × 3 forms) | Medium | Schedule | Contract animator from Phase 1; Form II is a recolour by design |
| Content looks like a Battle Cats clone | Medium | Store rejection or press framing | Original IP rules in Section 13.4; the hook and portrait layout are visible in the first screenshot |

### 17.2 Open questions

- [ ] Engine decision (Unity 6 recommended) and the owner of that decision
- [ ] Monetization model sign-off: Full Campaign unlock versus premium up-front
- [ ] Analytics vendor
- [ ] Loadout size: 8 is inherited from the brief; the prototype should test 6 and 8 in portrait, since 8 cards cost 20% of screen height
- [ ] Whether tablets and foldables are supported at launch or deferred
- [ ] Trademark checks on PUSHLINE and the world and unit names
- [ ] Soft-launch markets and whether Japan is one of them
- [ ] Target launch window

