Most of the data for this is available at the following URL:

## Calculating Accuracy

Accuracy and weapon skills, don't improve effective accuracy enough. The
below chart shows the accuracy (as displayed in % chance to hit when
aiming) of various weapons with various stats (45/40 = 45 weapon stat /
40 accuracy).

- 20/20 = average rookie
- 45/40 = low vet
- 60/50 = high vet
- 80/60 = superstar (unexpected, definitely not more than 1 or 2 per
  game)

![<File:accuracy-with-weapons.png>](accuracy-with-weapons.png "File:accuracy-with-weapons.png")

The gain between an average rookie and a high vet is just not enough, I
think. Especially not between an average rookie and a low vet. I'd like
to see a high vet achieve the accuracy gains of a superstar, maybe even
a little more. But its not easy to figure this out. The chart is based
on % chance to hit, but this is probably not even related to the
calculations done to actually fire the weapon, which are more
complicated.

The following description of the math from DarkRain is useful:

`accuracy = 1 - (accuracy_ability / 100 + weapon_skill / 100) / 2`
`(which equals to: take the average of both, divide it by 100 and then rest that from one)`

`first for parabolic throws (grenades and such):`
`first, the angle (pitch, yaw, roll) for a perfect throw to the intended target is calculated, then   it is modified this way: `
`pitch += <random number  between -1 and 1> * 2 * (spread1 * (0.5 + 1 * accuracy))`
`yaw += <another random number between -1 and 1> * 2 * (spread2 * (0.5 + 1 * accuracy))`

`now for straight shots (bullets, beams, knives, anything travelling in a straight line):`
`again the pitch, yaw, roll angles for a perfect shot is calculated, and then modified:`
`first get two Gaussian distributed random numbers with median at 0 and standard deviation of 1,   let them be gauss1 and gauss2, `
`then calculate a secondary injury multiplier (this one was here before wounds were implemented and  I haven't touched it):`
`if HP / maxHP < 0.5 injurymultiplier2 = 1 + 0.2 * ((1 / (HP / maxHP + 0.5)) - 1) * 100 / mind`
`else injurymultiplier2 = 1`
`then:`
`pitch += gauss1 * (spread1 * ((0.5 + 1 * accuracy) * injurymultiplier2))`
`yaw += gauss2 * (spread2 * ((0.5 + 1 * accuracy) * injurymultiplier2))`
`if the shooter is crouched, each of the above two is additionally multiplied by the crouch factor  from the fireDef`

Thanks to DarkRain's spreadsheet, I think I've got an idea of how to
adjust the accuracy calculation to dramatically increase the improvement
of veteran soldiers. Currently, the accuracy calculation is:

`accuracy = 1 - (accuracy_ability / 100 + weapon_skill / 100) / 2`

If we modify this to:

`accuracy = 1 - ((accuracy_ability - 10) / 50 + (weapon_skill - 10) / 50) / 2`

Then we end up with regular vets (50 skill, 40 accuracy) getting a
significant bonus to accuracy, equivalent to the bonus we'd get with a
super vet (80 skill, 60 accuracy) using the existing formula.

See the spreadsheet called "Scratch Sheet" .

You can change the values at the top and see the old equation accuracy
versus the new equation accuracy. This is a pretty dramatic change, and
SuperVets (those who manage to get 80 skill and 60 accuracy) will really
be extraordinary shots. I expect this to be pretty rare, though, and I
think players will really notice soldier improvement (not just assume it
based on stat improvement) Any thoughts?
--[H-hour](User:H-hour "wikilink") 18:10, 6 August 2013 (CEST)


I third this proposal! I say we give it a try.
--[DarkRain](User:DarkRain "wikilink") 05:15, 7 August 2013 (CEST)

## Speed Growth Mechanisms

I'm not really a fan of [how speed is
improved](Skills/Improvement/v2.5 "wikilink"). It encourages tedious
maxing out movement wherever possible, even using the last 4 or 6 TU of
each soldier. Maybe that's fine and not a big deal, but I wonder if we
should consider some alternatives. Here are two:
--[H-hour](User:H-hour "wikilink") 00:02, 19 March 2013 (SAST)

- **Large Movements**: Give a soldier bonus points for moving with more
  than 75% of his TU in a turn. We could also give a lot of bonus for
  using 75% of his TU and getting a kill in the same turn. This would
  not eliminate the tedious maxing, but would at least eliminate all the
  using up of any tiny excess TU. This may be more difficult to track
  and code, though, and would be less reliable for balancing stat gain.
  - This is too complicate and impossible to explain to the player. I
    like the cumulative aproach much more.
    --[ShipIt](User:ShipIt "wikilink") 07:53, 19 March 2013 (CET)
- **Cumulative Growth**: Like HP, we could just make this one a function
  of all the total XP accumulated elsewhere.

## Stat Maximum

- I am in favour of this. The gain is too slow atm. But I still think
  there should be a limit to what stats a human physically can reach.
  This limit should depend on the starting value instead being an
  absolute number, to reflect the physical conditions of the soldier.
  --[ShipIt](User:ShipIt "wikilink") 08:49, 19 March 2013 (SAST)
  - With a maximum number set it should be possible to tweak the values
    in a way to make it possible to get to the max within \~30 missions.
    --[ShipIt](User:ShipIt "wikilink") 10:24, 19 March 2013 (SAST)
    - Stats will max at 100, but I don't think this is what you want.
      I'm not entirely sure I agree with you on this. If soldiers hit an
      absolute max cap regularly, this could create too much of a
      disincentive to keep the soldier at home, as further experience
      would be wasted on them. It would also probably render meaningless
      the bragging rights you get with your top soldier (remember when
      you and I traded screenshots of our top soldiers?) if the player
      ends up with several soldiers all topped out around the same
      numbers. HOWEVER, I would be in favor of tapering the experience
      curve more, so that after a certain amount of stat gain the
      soldier must get a lot more exp for further development. This
      would still provide that incentive to spread the exp around but
      would be a softer limit, allowing top soldiers to still develop
      some (albeit slowly) and players to play how they want (note that
      some skills, like strength, will really not be able to get to 100
      even if they go in \~60 missions). If you look at the first graph
      below, the equation I've proposed is the orange line. I like how
      this equation tapers early -- the first 2,500 exp gives twice as
      much of a stat boost as the next 2,500 exp. But it really
      straightens out around 5,000. Maybe DarkRain knows some math that
      would taper the post-5,000 more so that it flattens out a bit? Or
      maybe we just use some code that calculates the bonus for the
      first 5,000 exp differently from the second 5,000 exp? What do you
      think about this? --[H-hour](User:H-hour "wikilink") 14:22, 19
      March 2013 (SAST)
      - Note: with the system I describe the soft max will be different
        based on initial stats. --[H-hour](User:H-hour "wikilink")
        14:22, 19 March 2013 (SAST)
      - The most direct way of altering the curve is changing the
        exponent: moving it closer to 1 will make the soldier improve
        less quickly at the start compared to later stages, but he will
        reach higher values more easily. On the other hand, moving it
        closer to 0 will make the soldier improve more rapidly at the
        start, but almost not at all once he becomes a veteran. If a
        good growth rate can be achieved changing this, fine, if not
        then we can think of a new method for calculating the stats
        growth. --[DarkRain](User:DarkRain "wikilink") 19:07, 19 March
        2013 (SAST)

![<File:exp-to-stat-curves.png>](exp-to-stat-curves.png "File:exp-to-stat-curves.png")

- - Here are a couple of curve options. They don't seem to flatten out
    quite as much as I would like and I wonder with the other equations
    if the stat gain is too quick at the start. But I'm not sure...
    opinions? --[H-hour](User:H-hour "wikilink") 23:44, 19 March 2013
    (SAST)
  - I just updated the image with another curve that uses a flatter
    equation for all exp over 5000. It doesn't look like such a dramatic
    difference, to be honest. THoughts?
    --[H-hour](User:H-hour "wikilink") 00:04, 20 March 2013 (SAST)
    - Is that the right image? I don't seem to see *any* difference at
      all --[DarkRain](User:DarkRain "wikilink") 19:45, 23 March 2013
      (SAST)
      - The caching in the wiki is severe. Try clicking on the image,
        then CTRL-R refreshing the image page. It should update with the
        new image. --[H-hour](User:H-hour "wikilink") 21:03, 23 March
        2013 (SAST)

- - On a related note: should we look into adjusting the max experience
    per mission? I noticed that some of the averages in your games were
    way below what the max per mission would allow, will this provide an
    incentive for players to grind to max experience? On the other hand,
    the stats with the larger difference between the average and the max
    are also the hardest to grind efficiently -weapon skills- due to
    limited ammo and targets, so maybe this isn't such a concern after
    all? --[DarkRain](User:DarkRain "wikilink") 19:07, 19 March 2013
    (SAST)
    - I thought I had responded to this but I guess it was just in my
      head. I think this is a really difficult thing to know in advance
      and plan properly for. This is because I don't know if stat gain
      for any particular stat is based on a few missions with high
      values or based on receiving low values every mission. In the
      first case, increasing the max gain could lead to a large increase
      in overall exp received during a campaign. In the latter case,
      increasing the max gain wouldn't change much. I think it's worth
      separating which skills might be which. The following is just
      guesses: --[H-hour](User:H-hour "wikilink") 16:54, 3 April 2013
      (SAST)
      - More exp comes from a smaller subset of the missions where the
        soldier performs very well:
        - *accuracy* I think it would make sense for this skill to max
          at 2/3 the max of the weapon skills, so that it couldn't grow
          as fast as a weapon skill but wouldn't grow too slowly.
        - *mind* This stat is still a bit up in the air until psionics
          is invented. I suggest leaving it as it is for now.
        - *weapon skills* If we set all weapon skills to 150-per-kill,
          that means the 4 kills will hit the 600 max (actually 680, but
          would need 5 kills for that I guess). I don't know about
          others, but it was pretty rare for any individual soldier to
          get more than 4 kills in a mission, so I'm guessing we're not
          hitting the max here. My feeling is that the max could be kept
          at 600 for this, simply because it's really not that easy to
          get more than 4 kills in a mission, so the incentive for
          grinding has a strong counter-balance.
        - *hp* (maybe) Health might be getting a big bonus from some
          missions if a soldier reaches their weapon skill max. The max
          on this seems huge, and HP is already growing pretty well
          compared with other abilities. I'd need to check a graph that
          shows exp-per-mission for it, but maybe this max can be
          reduced.
      - Exp is fairly consistent from mission to mission:
        - *strength* Strength seems fairly good as it is, and would just
          need to be adjusted to fit the new formula as the proposal
          page specifies.
        - *speed* I think I need to generate a new graph for this one,
          to show exp per mission, to know if we're vastly under the
          max-per-mission or hitting it. The max will obviously need to
          be adjusted if we follow the current proposal to raise its
          rate by 3x.

## Ability calculations

In /game/q_shared.h I found the following:

`#define GET_HP( ab )        (std::min((80 + (ab) * 90/MAX_SKILL), 255))`
`#define GET_ENCUMBRANCE_PENALTY(weight, max)   (1.0f - ((weight) > (max) * WEIGHT_HEAVY ? WEIGHT_HEAVY_PENALTY : (weight) > (max) * WEIGHT_LIGHT ? WEIGHT_NORMAL_PENALTY : 0.0f))`
`/** @todo Skill-influence needs some balancing. */`
`#define GET_ACC( ab, sk )   ((1 - (((float)(ab) - 10) / (MAX_SKILL / 2) + ((float)(sk) - 10) / (MAX_SKILL / 2)) / 2))`
`#define GET_MORALE( ab )        (std::min((100 + (ab) * 150/MAX_SKILL), 255))`
`#define GET_TU( ab, md )       (MIN_TU * (md) + (ab) * 20 / MAX_SKILL)`

This suggests that the EXP-\>points equation is different than for the
skills. I'm noting this here to investigate precisely where and how
these numbers are used, to see if refinement is needed after the changes
(with, ie, morale-\>panic/rage, etc). --[H-hour](User:H-hour "wikilink")
18:59, 8 August 2013 (CEST)


GET_HP calculates HP from strength and this macro is used only in one
place (G_Damage(), g_combat.cpp) to calculate the max HP an unit will
have after being healed in combat, TBH I'm not really sure what this is
supposed to achieve, it seems that this number will be higher than the
soldier's max HP most of the time anyway, I would like to remove this
macro. --[DarkRain](User:DarkRain "wikilink") 01:08, 9 August 2013
(CEST)

## Useful Graphs

![<File:exp-to-stat-equations.png>](exp-to-stat-equations.png "File:exp-to-stat-equations.png")

![<File:skill-exp-per-mission.png>](skill-exp-per-mission.png "File:skill-exp-per-mission.png")

![<File:skill-stat-per-mission.png>](skill-stat-per-mission.png "File:skill-stat-per-mission.png")

![<File:ability-stat-per-mission.png>](ability-stat-per-mission.png "File:ability-stat-per-mission.png")