## Improved Autoresolve

This page describes a new algorithm for auto-resolving missions. It is
intended to replace the algorithm in use at the time of writing (as seen
in version 2.2.1).

Note: All calculations and values given in this proposal can (and
probably will) be revised.

## Algorithm

### Balance of power index

The balance of power index is a floating point value between 0 and 1
that indicates how strong PHALANX is compared to the aliens on this
mission. The balance of power is a function of the following factors:

- PHALANX and Alien numbers
- PHALANX and Alien equipment
- Difficulty setting

These factors can be determined as follows:

    numbers = #(soldiers on mission) / #(aliens in mission)


Note: wounded soldiers only count for (currentHP / maxHP), so two
soldiers with 50% HP equal 1 soldier at full HP for the purpose of this
calculation. UGVs and 2x2 aliens count for 1.5 (or another value between
1 and 2, as required).

<!-- -->

    equipment = (total equipment score PHALANX) / (total equipment score aliens)


Note: equipment score is not defined in the script files at present.
This score should be defined for each item separately and be the same as
the "purchase cost" in [Point-based
Multiplayer](Gameplay_Proposals/PointBasedMultiplay "wikilink").
Typically, the aliens should always have a score per soldier equal to or
higher than PHALANX, as alien equipment should have the highest
cost/scores.

<!-- -->

    difficulty = 1 for normal difficulty, <1 for higher difficulties, >1 for lower difficulties.

The index could then be calculated as follows (for example):

    BoPindex = min(1.0, numbers * equipment * difficulty).

The balance of power index shouldn't easily reach 1, as the aliens would
often outnumber PHALANX and out-gear them too. 1 could be reached on
missions where few aliens are present (such as scout missions).

The balance of power is a direct indication of whether or not a mission
is successful. If a mission is successful, all aliens are considered
killed or captured (more on this later), and a portion of their
equipment is recovered (ammo and one-time items such as grenades should
be reduced). If the mission is a failure, no equipment is recovered.

### Injuries and casualties

Each PHALANX soldier has a chance of being killed in action and a chance
of being wounded. The chance for injury is

    injuryChance = (1 - BoPindex)

The chance for death is

    deathChance = 0.5 * (1 - BoPindex)

Each soldier first "rolls" for injury. If successful, the soldier loses
a random amount of health varying between 25% and 75% of his/her max
health. If this reduction reduces the soldier's health to 0 (if the
soldier was wounded to begin with), the soldier dies. If the injury roll
is not successful there is a roll for death. If successful, the soldier
dies. Otherwise, the soldier survives the mission unhurt.

Each civilian has a chance of being killed by aliens:

    civilianDeathChance = (1 - BoPindex) ^ 0.5

If the mission is successful, a check is made for each non-robot alien
that determines whether or not that alien is captured alive. The chance
for this occurrence is

    liveCaptureChance = 0.1

All other aliens are considered killed.

If the mission is not successful, alien casualties are treated like
PHALANX casualties, with chance

    alienKilledChance = BoPindex

### Experience

Soldiers must gain experience even when autoresolving. There is no need
to model this in detail. Soldiers are expected to gain max experience
when participating actively on any mission. However, to prevent a 12-man
squad from leveling up on a 3-alien mission, experience should be scaled
to the numbers factor. For each stat the soldier will use on this
mission (strength, speed, (accuracy), HP and the skill corresponding to
whichever weapon the soldier has equipped), increase experience by

    increase = min(1.0, 1 / numbers) * maxExperience

### Scoring

A [Score](Gameplay_Proposals/Scoring "wikilink") must still be generated
for autoresolve missions. Several of the sub-scores can be obtained from
the calculations given in this article. Those that cannot should be
random or a function of those that can, for simplicity. For example,
aliens killed by PHALANX can be a small, fixed chance and civilians
infected can be a portion of civilians killed, depending on the alien
mission type.

The effect on nation happiness is then calculated from this score, as
(will eventually be) normal.