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
