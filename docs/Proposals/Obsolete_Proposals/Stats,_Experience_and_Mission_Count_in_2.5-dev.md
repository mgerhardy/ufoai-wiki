*This has been implemented.* --[H-hour](User:H-hour "wikilink") 11:24,
13 August 2013 (CEST)

## Introduction

This is a proposal for improving soldier development for 2.5 or 2.6. It
addresses the slow pace with which soldier stats increase and the way in
which some improved stats are pointless or not significant enough.

## Background

Soldiers gain experience in each stat for participating in battle and
performing certain actions (such as shooting an alien) relevant to that
stat. The game then converts this experience into stat points which are
added onto the soldier's initial stat.

The factors effecting soldier development consist of the following:

- The number of missions they participate in.
- The number and type of actions they perform in those missions.
- The experience they get for each of these actions. (See:
  [Skills/Improvement](Skills/Improvement "wikilink")
- The equation which converts experience into stat points.
- The soldier's initial stat points.
- The equations which use a soldier's stat points to effect actions on
  the battlefield (ie - how the Accuracy stat effects a soldier's actual
  accuracy).

## Number of Missions

Currently a game takes place over the course of more than 120 missions.
This was considered excessive and now players should face 60-100. In
addition this change in the number of overall missions, I hope to later
improve the incentives for players to field more than one squad, which
will spread the experience over more soldiers.

*All numbers in this proposal assume that a veteran soldier is likely to
see 30 missions, but may see around 40-50 in exceptional circumstances.*

## Conversion of Experience to Stat Points

Currently, the game converts experience points into stats with the
following equation:

`New Skill = Original Skill + (Experience/100)^0.6`

This should be changed to the following equation:

`New Skill = Original Skill + (Experience/10)^0.6`

This will dramatically increase the rate of stat gain, converting fewer
experience points into more stats. In addition, it will create a sharp
curve so that soldiers will gain quickly in their first missions, making
new recruits still worth keeping alive past the middle of the game.

*All experience adjustments below assume this new equation.*

## Power (Strength)

Experience gain for power should be cut to 1/3 [its current
rate](Skills/Improvement/v2.5 "wikilink"). This would keep the current
growth rates (which seem appropriate) in the new experience conversion
equation.

- Estimated increase \~30 missions: 13-19
- Estimated stat \~30 missions: 48-54

## Speed

Experience gain for speed should be increased 3x [its current
rate](Skills/Improvement/v2.5 "wikilink"). This stat should not increase
TU too much or it would quickly become the most powerful stat.

- Estimated increase \~30 missions: 35-53
- Estimated TU increase \~30 missions: 8-10
- Estimated stat \~30 missions: 55-73
- Estimated TU \~30 missions: 38-41

### Cause for experience gain

Currently this is based on walking, crouching and using weapons. This
provides adverse incentives to always move your guys fully each turn.
After some discussion, we've decided to use a cumulative stat growth
mechanism, so that speed experience gain represents a percentage of all
other experience gain.

## Accuracy

Experience gain for accuracy should be increased 2x [its current
rate](Skills/Improvement/v2.5 "wikilink"). This stat should not increase
as quickly as the weapon skills, but if it increases too slowly it will
be a drag on the improvement of any weapon skill because the two are
combined when computing accuracy.

- Estimated increase \~30 missions: 21-41
- Estimated stat \~30 missions: 46-66

### Utility of stat

Accuracy, along with weapon skills, doesn't improve effective accuracy
enough. After some discussion, we've decided to try a new accuracy
equation:

`accuracy = 1 - ((accuracy_ability - 10) / 50 + (weapon_skill - 10) / 50) / 2`

## Mind

Experience gain for mind should be kept at [its current
rate](Skills/Improvement/v2.5 "wikilink"). This stat is highly dependent
on our psionic warfare, so it is difficult to set good rates now. The
cause for experience gain is likely to change with psionic warfare.
Soldiers will need to compete against alien mind stats, so we will need
a large range in the Mind stat. In addition, our panic system hasn't
been looked at in a long while and would also factor into this stat.
Keeping the current rate, alongside the new equation, will give us a
good range of values for future tweaking.

- Estimated increase \~30 missions: 39-50
- Estimated stat \~30 missions: 66-77

### Cause for experience gain

This should be more closely related to fear and panic, but I haven't yet
thought of a good mechanism. Ideas include getting wounded, seeing a new
alien, seeing teammates killed or wounded.

### Ranks

Rank requirements may need to be adjusted to fit this new profile. I
haven't looked into that.

### Note

After adjusting the XP-\>stat equation and testing a late-stage saved
game, I found the Mind stat was far too high, so I have reduced the
XP-per-kill from 200 to 100 as an approximate measure. This will have to
be revisited in the future. --[H-hour](User:H-hour "wikilink") 11:50, 8
August 2013 (CEST)

## Health (HP)

Experience gain for hp should be reduced to 4/10 [its current
rate](Skills/Improvement/v2.5 "wikilink"). I think this shouldn't grow
too much because it could unbalance a lot of weapon details in the
late-game.

- Estimated increase \~30 missions: 27-34
- Estimated stat \~30 missions: 127-134

## Weapon Skills

Experience gain for all weapon skills should be increased by 20% in
general. However, we should adjust [individual
rates](Skills/Improvement/v2.5 "wikilink") to equalize the typical gain.

- Estimated increase \~30 missions: 34-66
- Estimated stat \~30 missions: 54-86

*Note: estimates range from 3600 to 10,800 exp. Most vets will range
from 3600-6000, but the estimates above take into account players'
tendency to focus exp on a few vets.*

### Cause for experience gain

The experience for weapon stats varies a lot because some roles are
cross-trained more (Assault), some are less frequently used (Close) and
some get fewer points per kill. After looking at the data, my sense is
that the difference in experience given for different stats is
unnecessary. The two highest-experience skills (Explosives and Sniper)
each given 200 exp per kill. Assault, which gives just 100 exp per kill,
typically lags behind. Close, which gives 150 exp per kill, also lags
behind, but that is likely because this skill is more specialized and
used less often. Accuracy doesn't matter as much for Close specialists,
so it's okay to lag behind.

*I think all weapon skills should get 180 exp per kill, which is the
original 150 + 20%.*

## TODO

Here is a list of items that need to be changed to implement this
proposal.

- Change the equation which converts experience points to stat points:
  *New Skill = Original Skill + (Experience/10)^0.6*

- Change the experience-per-mission formula for strength. Reduce
  modifier to 1/3 its current rate: *50 \* (weight / strength) /
  ENCUMBRANCE_MODIFIER*

- Change the cause of speed gain. It should work like HP, where 0.2 XP
  are gained for every 1 XP accumulated elsewhere.

  - Can someone check the math on this for me? I think if it uses 0.5,
    the same rate that HP has now, before the change, it should be about
    3x it's current rate. But something in my head is giving me a
    nagging doubt. I'm basing the assumption on the ability points
    improvement graph in the talk page.
    --[H-hour](User:H-hour "wikilink") 11:12, 7 August 2013 (CEST))
    - Actually I think that would closer to 5x, but there would be wider
      variation, using the data from your spreadsheet the HP XP gained
      is about 2x to 7x the speed XP gained (with an exceptional 13x
      case), but if we'll increase the XP gain across the board...
      --[DarkRain](User:DarkRain "wikilink") 02:52, 8 August 2013 (CEST)
      - Your right. If XP gained is generally increasing across the
        board, it will affect this as well. I've reduced the speed and
        HP rate to 0.2. Better to be too low than too high for these
        particular stats, as they can unbalance things more than other
        stats. We can always increase it later.
        --[H-hour](User:H-hour "wikilink") 10:27, 8 August 2013 (CEST)
        - Just one more thing, since both HP and speed will be based on
          the total XP gained elsewere, do we factor speed XP into the
          HP XP calculation or do we factor HP into the speed XP
          calculation, or neither?
          --[DarkRain](User:DarkRain "wikilink") 00:50, 9 August 2013
          (CEST)
          - Good point! I'd say neither? Just to avoid any potential
            recursive stat bonus problems...
            --[H-hour](User:H-hour "wikilink") 10:32, 9 August 2013
            (CEST)
            - That's fine with me --[DarkRain](User:DarkRain "wikilink")
              01:04, 10 August 2013 (CEST)

- Increase the experience gained for accuracy to 40 per enemy hit.

  - Increase the experience gained for accuracy per hit while using the
    sniper skill to 60 per enemy hit.

  - Change the equation which calculates accuracy.

- Adjust soldier rank thresholds to ensure it works properly with new
  mind stat growth.

  - I made some adjustments to the best of my ability, based on the
    changes to the stat growth and some minimal existing data on exp
    gained per-mission. Hopefully, the middle ranks will be accessible,
    but the highest rank will be rare. Overall, I lowered the threshold
    for enemy kill count, as the little data I had on kills per mission
    suggested it would be very difficult to reach middle and upper ranks
    with new UFO rate. --[H-hour](User:H-hour "wikilink") 11:01, 12
    August 2013 (CEST)

- Reduce the experience gained for HP to 0.2 experience for each
  experience point earned elsewhere.

- Set the experience gained for all weapon skills to 180.

- Check if we need to adjust max experience gain per mission.

  - I'm thinking specially of speed, which's max gain per mission is
    currently 91, but having a look at the other stats won't hurt.
    --[DarkRain](User:DarkRain "wikilink") 19:42, 10 August 2013 (CEST)
    - If a soldier gets the max per mission (91) for 30-60 missions,
      they will gain 28-43 ability points, according to my calculations.
      Using this TU calculation:

`(md) = normal weight TU modifier`
`(ab) = ability points`
`MIN_TU = 39`
`MAX_SKILL = 100`
`#define G(MIN_TU * (md) + (ab) * 20 / MAX_SKILL)`

- I found that a rookie (20 speed points) would get 27.3 TU. After 30
  missions of max gain per mission, they would get 36.9 TU. After 60
  missions of max gain per mission, they would get 39.9 TU. That sounds
  about right to me. Any more might be too overpowering (it's nearly as
  much as the low-weight speed bonus).
  --[H-hour](User:H-hour "wikilink") 21:03, 10 August 2013 (CEST)
  - For the weapon stats, I don't think the numbers were changed very
    much (150-200 =\> 180). Strength has no cap. Mind is still in this
    world of uncertainty (how it's used, etc). Accuracy is the only one
    that might be a problem. My general theory was that Accuracy should
    increase at about 2/3 the rate of weapon skills, so perhaps this
    should be set to 2/3 the weapon max (680 / 3 \* 2 = \~450).
    Thoughts? --[H-hour](User:H-hour "wikilink") 21:03, 10 August 2013
    (CEST)
    - OK,that leave only HP, AFAIR the max for this (which is huge),
      even with the old formula was nearly impossible to reach, as it
      would have required to max every other stat experience, including
      all 5 weapon skills; now with the new formula, only 4 weapon
      skills and taking out speed it becomes impossible anyway, even
      maxing every usable stat would only yield \~750 points, so, two
      choices leave it at that (which pretty much means no max) or cap
      it (somewhere between 350 and 375 seems right to me)
      --[DarkRain](User:DarkRain "wikilink") 01:37, 11 August 2013
      (CEST)
      - It's a tough one, because even if the max is at 350, I think a
        soldier would only rarely hit it. This is good, and how it
        should be, but it makes it hard to calculate what the cumulative
        effect will be. If a soldier gets the 350 max for 30 missions,
        they'll have 156 HP. But how many of those missions will they
        actually max out? If they max on 10 and get 100 exp on 20,
        they'll have 137 HP. If they do 60 missions and max out 20 of
        them and get 100 exp on 40 of them, they'll have 159 HP. This
        sounds significant but reasonable. But to be honest these
        numbers are pure speculation. I really don't know how much of a
        soldier's exp is earned in big-mission bursts and how much is
        earned through grinding. This is all a long, convoluted way of
        saying: I don't have a good opinion. I say it's your call.
        --[H-hour](User:H-hour "wikilink") 10:22, 11 August 2013 (CEST)

- Have a look at FR