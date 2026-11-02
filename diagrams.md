# Diagrams as text

## Battle loop (GDD Section 4)

Two rows. The top row repeats many times inside one stage; the bottom row runs once per clear.

In a stage: Earn cash -> Deploy units -> Fight up the lane -> Capture zones -> Break the base.
Loop back: Capture zones -> Earn cash (Zone 2: +20% income; Zone 3: Command Meter charges 50% faster).
On win: Break the base -> Rewards (XP, Cogs, unlocks) -> Upgrade units, pick loadout -> Next stage -> Earn cash.

## Production timeline (GDD Section 15)

Weeks from project start, 56 in total. The gate under each phase is the condition to leave it.

| Phase | Weeks | Gate |
| --- | --- | --- |
| 0. Portrait prototype | 0-6 | 8 of 10 testers play one-handed unaided; 7 of 10 would play more; median first win under 2 min |
| 1. Vertical slice | 6-18 | World 1 first-clear rates within 15 points of target; 60 fps on reference devices |
| 2. Production | 18-46 | All 270 stages pass the CI balance gate; two playtest rounds per world; P0 retention list complete |
| 3. Soft launch | 46-54 | D1 >= 28%, D7 >= 6%, crash-free >= 99.5% |
| 4. Global launch | 54-56 | Store launch; first monthly event ready |

The week-6 gate is the only one that can kill the concept; everything after it is schedule risk.
