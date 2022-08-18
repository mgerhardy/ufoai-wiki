Hacked off the first round of brainstorm due to refinement and inclusion
in main article. --[Wanderer](User:Wanderer "wikilink") 05:36, 13 May
2007 (CEST)

## Zoning the Geoscape

Instead of actually zoning the geoscape into regions, I had a brainstorm
I'm not sure of it's feasibility. If you put 'Location Markers' on the
map, say, center of Antarctica, Eastern Europe, Western Europe,
North/South America, so on, and then when a mission occurs use whichever
marker is closest as an indicator. Associate each map or random build
with a point of origin, and when a mission occurs near that PoO, it can
read through the list and find the correct map.

The nice part about this is you could be as specific or generic as you
want. Surround New York City, London, Paris, whatnot with more generic
'Woodlands', 'Farmland' markers. Use a Marker type once or many times,
to help control more specific areas.
--[Wanderer](User:Wanderer "wikilink") 18:46, 11 May 2007 (CEST)

--[BTAxis](User:BTAxis "wikilink") 14:10, 12 May 2007 (CEST):


It's probably easier to do it that way from an implementation point of
view, but I think it might be hard to define specific areas that way
because it's hard to tell exactly when one marker takes priority over
another marker. For example, take the Sahara desert. Missions inside of
it should be desert-themed, but missions outside of it should not. Using
markers, it's going to be a very hard job to get the desired behavior
because the Sahara desert isn't shaped very conveniently.

## Choosing the Interest Events

    The event with the highest number that is still smaller than CategoryInterest
    will be the event that is selected, with a small random modifier applied to
    prevent all multiple instances of the category type to be duplicate.
    For example, CategoryInterest + (RAND() - 0.5) * SQRT(CurrentInterest).

This is definately different then what I remember discussing as being
the selector. At early game this modifier isn't enough to even move the
CategoryInterest (CurrentInterest of 50, say, so we're looking at \~7 \*
.0-.5, an average difference of around 1.5-2.), and in late game still
not really much to move it (CI 1000 = 100 \* .0-.5, average .25, 25
points). There is almost no variability in this functionality for the
selector. Especially when you consider according to the older
selectivity method, you'd need, at 1000 CategoryInterest, a 100 point
gap for a mission for it to have 10% selectivity.

I know you'd like a more effective way of selecting off the mission list
to weight it at the top, but (CategoryInterest \* RAND() ) still seems
like the most effective way to go. If you really want to weight it, how
about a function like:

( ( CategoryInterest \* .5) \* RAND() ) + ( CategoryInterest \* .5).
This keeps you in the upper half of the category mission list while
providing more volatility in the mission selection.
--[Wanderer](User:Wanderer "wikilink") 17:37, 14 May 2007 (CEST)


--[BTAxis](User:BTAxis "wikilink") 19:39, 14 May 2007 (CEST): Changed
it. Thanks.

EDIT: How about this one: CategoryInterest \* SQRT( (RAND() \* .7) +
.3)? You're basically limiting the event range to 30%-100% of
CategoryInterest, and the root skews it to the top. A cube root would
skew it even more.


You'd actually be more around 54%-100%, which wouldn't be so bad either.
(Square Root of 0.3 is .547722). It would definately weight towards the
top though, very very heavily. I haven't done the complete math but if
I'm guessing right about 30% of your missions will be in the top 3%, and
60% of your missions in the top 10%. That's a LOT of weight. Is that
your intent? --[Wanderer](User:Wanderer "wikilink") 20:06, 14 May 2007
(CEST)


I just realized the first point myself, but you beat me to it. The skew
can be adjusted by weaking the power: ((RAND() \* .7) + .3) ^ (0.7)
would result in a weaker skew than a SQRT, and would allow for lower
level events as well. The "hard" skew by the multiplication and addition
within the power can, of course, also be adjusted or discarded if that
is the better choice. with these values, a RAND() of 0.5 gives us ((0.5
\* 0.7) + 0.3) ^ (0.7) = 0.74, so 50% of the missions would be in the
top 25%. a RAND() of 0.8 gives us ((0.8 \* 0.7) + 0.3) ^ (0.7) = 0.9, so
about 20% of the missions appear in the top 10%. How's that?
--[BTAxis](User:BTAxis "wikilink") 20:18, 14 May 2007 (CEST)


This would work pretty well, actually, and would be tweakable in the
long run if necessary to a more effective rate if needed. It would max
off the bottom at around 43%, giving more variety. Now, if we really
want a top weighted value with a lower bound of 30%, we need to work the
calculation to simply adjust the 70% part.

So, if we start off with a base of (CurrentInterest \* .3) + weighting,
and then play with the weighting part to create a bell curve. So, we
work off a base value of (CurrentInterest \* .7) and then give it a
multiplier of weighting as above. So we could use something like the
calculation of ( (CI \* 0.3) + ( ( CI \* 0.7) \* ( RAND() ^ 0.8) ).

So with a RAND() of 1, we end up at 100%, obviously. At RAND() 0.8, we'd
get .83 of the *difference*. Working off 100 CategoryInterest, This
would be .83 of 70 + 30, for 58.6, for a total of 88.6. Pretty close to
20% of missions in top 10%. At Rand() 0.5, we get a weighting of .57,
for about 40+30, 70. This means 50% still in top 30%. However, as we
drop, the curve steepens faster. At 0.25 Rand(), We get a .32 weight,
for an additional 23, equating out to 53. 75% of missions in top 47%. At
0 RAND(), we get a flat 30, meaning 100% in top 70%.

I'd like to see the bottom 50% of RAND() have more volatility, but at
least this can give us a good variable base to start from. You could
almost increase the Rand()'s exponential modifier to 0.85 or so and
really steepen the lower end of the curve without significantly
affecting the upper portion.

One thing to keep in mind with this method is that the widening spread
as you go higher in the mission files needs to be not quite as large, or
your volatility here won't be enough to keep 'repeating missions' out of
the queue where the law of averages is not necessarily always going to
apply.

--[Wanderer](User:Wanderer "wikilink") 21:31, 14 May 2007 (CEST)


I'm not entirely sure what you mean by that last part. But I like the
rest of it, and I think an exponent of 0.85 would probably give us
better results in this scheme. --[BTAxis](User:BTAxis "wikilink") 21:49,
14 May 2007 (CEST)


Good, I like the 0.85 too. That eases that. What I was mentioning in the
end was regarding the 'selection value' climb in the CategoryMission
files. In the original method, I was expecting the 'most recently
available' mission to have about a 15% selectivity rate, somewhere
between 10-20%, anyway. So, at 10 Interest, it'd only be 2 selections
wide. At 100 Interest, however, it'd be 15-20 points wide. With this
weighting method, to make sure we can clear the lower bound of the
uppermost mission so at least in the top 25% of selection we'd have two
that would be chosen from, we'll have to tighten this range, and perhaps
mix up the missions more. My comment about the Law of Averages is that
we can only count on it with a very large sample. In a short run, it's
very easy to hit the same mission in the top 25% two or three times in a
row, especially when we include weighted event category selectivity and
we hit a couple of recons/harvests in mid-late game.
--[Wanderer](User:Wanderer "wikilink") 23:05, 14 May 2007 (CEST)


It's going to be pretty impossible to come up with a unique event for
every single entry in the event table anyway, so as long as the nulls
get hit at a satisfactory rate, I'm not too worried about the chance
that the same event might be selected a couple of times in a row. The
important thing to me is that they won't *necessarily* get selected
twice. So providing the event tables are sane, I foresee no major
problems. --[BTAxis](User:BTAxis "wikilink") 23:45, 14 May 2007 (CEST)

## Base attacks

When a base attack is spawned, the UFO or UFO group should fly to a base
that is randomly picked, the selection being modified by the bases'
weights. A base's weight is a function of how well-known that base is to
the aliens (the base will make itself more known the more it attacks
nearby UFOs) and the degree of alien infiltration and/or XVI infection
of the area the base is located in. --[BTAxis](User:BTAxis "wikilink")
16:10, 27 July 2007 (CEST)

should a base be 100% known if it has taken out an enemy ship with
missiles--[Rioting pacifist](User:Rioting_pacifist "wikilink") 00:48, 8
July 2008 (CEST)

## 2012 Adjustment Considerations

The following is the beginning of an attempt to prevent too many UFOs
from spawning and getting the balance a bit better.

1\. Our current setup seems to increase the number of UFOs during the
campaign according to a . Y-axis controls the likelihood of a mission
spawning (roughly) and X-axis controls alien interest (consider it the
progression of time).

The main problem with this is that there is no way to properly balance
the number of UFOs in a given period of time if we rely only on this
equation. No matter what we decide is the right UFOs-per-month balance,
the game will always progress from not enough to too many. The equation
used is important for the early game, where we want to ease the player
in with fewer missions, and the late game, where we want to overwhelm
the player. But the majority of the campaign should take place in some
kind of sweet spot where there are not too many missions to overwhelm
the player. The game should become more difficult during this period not
because of an increase in UFOs, but because of an increase in the
weaponry/number of aliens that each UFO carries.

This is just a preliminary comment. I am still looking into other
aspects of the system to find good numbers, but I wanted to get comments
from the devs about this structural change. Would we agree that the
mid-game needs to occur with about the same number of UFOs per month?
--[H-hour](User:H-hour "wikilink") 23:33, 6 January 2012 (CET)

I haven't played campaign for 2 years, so I don't feel too competent as
far as balancing goes. But as all formulas seem to rely on interest
level, we should start with a complete list of all the things that
interest level has an effect on imho. Secondly, we need a list of
everything that can not be achieved with a simple formula like "0.5 ufos
per day. In other words: let's collect the requirements before talking
about the implementation.--[Duke](User:Duke "wikilink") 04:26, 7 January
2012 (CET)

I feel that a simple formula for number of UFOs could work in the
mid-game. But here is a list of things that we need that complicates it:

- UFOs should increase slowly at the beginning before they reach a
  standard rate.
- UFOs should increase dramatically at the "end" (a certain alien
  interest level) to overwhelm a player that has not progressed quickly
  enough.
- Random UFOs should come in bursts, not just a single chance each day.
  Could probably be solved by something like (3 possible UFOs, each has
  a 10% chance of being an actual UFO). So we could have bursts of 3
  UFOs in a day, but it would be uncommon. (This is basically the
  current implementation, except that many more UFOs can be spawned in a
  day.)
- Selecting the UFO mission type. There's already a complex system
  involved that chooses what type of mission to spawn when a UFO is
  actually spawned, based on specific alien interest levels in certain
  mission types. See the section below.
- Selecting the UFO mission difficulty. This is the most important.
  Higher interest levels should trigger larger alien parties and bigger
  ships to make it more difficult.
- anything else I'm missing?

We do face one problem with using the saves data: there doesn't appear
to be any historical data on increase of alien interest levels. So I can
pull out how many UFOs are being spotted throughout the course of the
game, but I can't match that to specific alien interest levels
--[H-hour](User:H-hour "wikilink") 10:55, 7 January 2012 (CET)

![Image:graphs_on_campaign.png](graphs_on_campaign.png "Image:graphs_on_campaign.png")

## Alien Interest

Overall alien interest is set to increase once every 18-22 hours
depending on game difficulty. On a very hard game save near the end of
the current campaign (226 days) the total interest was only 319. Our
current max alien interest is set to 1000. I think there is a problem
here. It should be set lower, or research progress needs to happen more
slowly. This is complicated by the fact that an alien base ends the game
at the moment, so the campaign might progress farther at some point. But
this number can be adjusted then.

If the save data is correct about the alien interest, then
equipment_missions.ufo needs to be adjusted as well because many of the
advanced equipment sets only occur at interest levels above 400.

Also, if we reduce max alien interest, we will want to reduce the number
50 in line 268 of cp_missions.c. At 400 interest it will create only 7-9
aliens:

`   numAliens = max(4, 4 + (int) ccs.overallInterest / 50 + (rand() % 3) - 1);`

### Individual Mission Interest

Numbers accurate as of 2012-01-07

     /* successful base attack */
        INT_ChangeIndividualInterest(0.3f, INTERESTCATEGORY_RECON);
        INT_ChangeIndividualInterest(0.1f, INTERESTCATEGORY_HARVEST);
        INT_ChangeIndividualInterest(-0.5f, INTERESTCATEGORY_TERROR_ATTACK);
        INT_ChangeIndividualInterest(-0.5f, INTERESTCATEGORY_INTERCEPT);
     /* unsuccessful base attack */
        INT_ChangeIndividualInterest(0.05f, INTERESTCATEGORY_BUILDING);
        INT_ChangeIndividualInterest(0.1f, INTERESTCATEGORY_BASE_ATTACK);
     /* alien base constructed */
        INT_ChangeIndividualInterest(0.1f, INTERESTCATEGORY_TERROR_ATTACK); /* only if it is a subversion mission */
        INT_ChangeIndividualInterest(0.4f, INTERESTCATEGORY_XVI);
        INT_ChangeIndividualInterest(0.4f, INTERESTCATEGORY_SUPPLY);
        INT_ChangeIndividualInterest(0.1f, INTERESTCATEGORY_HARVEST);
     /* alien base mission failed */
        INT_ChangeIndividualInterest(0.5f, INTERESTCATEGORY_BUILDING);
        INT_ChangeIndividualInterest(0.05f, INTERESTCATEGORY_BASE_ATTACK);
     /* alien base destroyed */
        INT_ChangeIndividualInterest(+0.1f, INTERESTCATEGORY_BUILDING);
        INT_ChangeIndividualInterest(+0.3f, INTERESTCATEGORY_INTERCEPT);
     /* successful harvest mission */
        INT_ChangeIndividualInterest(-0.3f, INTERESTCATEGORY_HARVEST);
        INT_ChangeIndividualInterest(0.2f, INTERESTCATEGORY_RECON);
        INT_ChangeIndividualInterest(0.05f, INTERESTCATEGORY_BUILDING);
        INT_ChangeIndividualInterest(0.1f, INTERESTCATEGORY_XVI); /* only if XVI researched */
     /* unsuccessful harvest mission */
        INT_ChangeIndividualInterest(0.1f, INTERESTCATEGORY_INTERCEPT);
        INT_ChangeIndividualInterest(0.03f, INTERESTCATEGORY_BASE_ATTACK);
        INT_ChangeIndividualInterest(0.03f, INTERESTCATEGORY_TERROR_ATTACK);
     /* successful intercept mission */
        INT_ChangeIndividualInterest(0.3f, INTERESTCATEGORY_RECON);
        INT_ChangeIndividualInterest(-0.3f, INTERESTCATEGORY_INTERCEPT);
        INT_ChangeIndividualInterest(0.1f, INTERESTCATEGORY_HARVEST);
        INT_ChangeIndividualInterest(0.1f, INTERESTCATEGORY_XVI); /* only if XVI researched */
     /* unsuccessful intercept mission */
        INT_ChangeIndividualInterest(0.1f, INTERESTCATEGORY_INTERCEPT);
        INT_ChangeIndividualInterest(0.05f, INTERESTCATEGORY_BUILDING);
        INT_ChangeIndividualInterest(0.05f, INTERESTCATEGORY_BASE_ATTACK);
        INT_ChangeIndividualInterest(0.05f, INTERESTCATEGORY_TERROR_ATTACK);
     /* successful recon mission */
        INT_ChangeIndividualInterest(-0.2f, INTERESTCATEGORY_RECON);
        INT_ChangeIndividualInterest(0.1f, INTERESTCATEGORY_HARVEST);
        INT_ChangeIndividualInterest(0.1f, INTERESTCATEGORY_SUPPLY); /* if base exists */
        INT_ChangeIndividualInterest(0.1f, INTERESTCATEGORY_XVI); /* only if XVI researched */
     /* unsuccessful recon mission */
        INT_ChangeIndividualInterest(0.05f, INTERESTCATEGORY_RECON);
        INT_ChangeIndividualInterest(0.1f, INTERESTCATEGORY_INTERCEPT);
        INT_ChangeIndividualInterest(0.05f, INTERESTCATEGORY_TERROR_ATTACK);
     /* successful base supply mission */
        INT_ChangeIndividualInterest(-0.2f, INTERESTCATEGORY_SUPPLY);
     /* unsuccessful base supply mission */
        INT_ChangeIndividualInterest(0.1f, INTERESTCATEGORY_SUPPLY);
        INT_ChangeIndividualInterest(0.1f, INTERESTCATEGORY_INTERCEPT);
        INT_ChangeIndividualInterest(0.05f, INTERESTCATEGORY_BASE_ATTACK);
     /* successful terror mission */
        INT_ChangeIndividualInterest(-0.2f, INTERESTCATEGORY_BASE_ATTACK);
        INT_ChangeIndividualInterest(0.03f, INTERESTCATEGORY_HARVEST);
     /* unsuccessful terror mission */
        INT_ChangeIndividualInterest(0.05f, INTERESTCATEGORY_TERROR_ATTACK);
        INT_ChangeIndividualInterest(0.1f, INTERESTCATEGORY_INTERCEPT);
        INT_ChangeIndividualInterest(0.05f, INTERESTCATEGORY_BUILDING);
        INT_ChangeIndividualInterest(0.02f, INTERESTCATEGORY_BASE_ATTACK);
     /* successful XVI mission */
        INT_ChangeIndividualInterest(-0.3f, INTERESTCATEGORY_XVI);
        INT_ChangeIndividualInterest(0.1f, INTERESTCATEGORY_HARVEST);
        INT_ChangeIndividualInterest(0.05f, INTERESTCATEGORY_BUILDING);
     /* unsuccessful XVI mission */
        INT_ChangeIndividualInterest(0.1f, INTERESTCATEGORY_INTERCEPT);
        INT_ChangeIndividualInterest(0.05f, INTERESTCATEGORY_TERROR_ATTACK);
        INT_ChangeIndividualInterest(0.01f, INTERESTCATEGORY_BASE_ATTACK);
     /* once every day (increases interest in supplying base */
        INT_ChangeIndividualInterest(AB_GetAlienBaseNumber() * 0.1f, INTERESTCATEGORY_SUPPLY);

## Pre-2.4 Conclusions

I've had a look through the code for generating UFOs, and
increasing/decreasing nation happiness, and here are my suggestions.
These suggestions are designed to address the worst problems (too many
UFOs, nation unhappiness early in game) with a minimal solution to
reduce the risk of seriously upsetting game balance for the 2.4 release.

### Recommendations

1\. Increase the cycle for mission spawning from 4 days to 8.

    cp_campaign.h
    #define DELAY_BETWEEN_MISSION_SPAWNING      8

- This will reduce the number of UFOs spawning by half.

2\. Reduce the maximum possible missions per cycle from 40 to 25.

    cp_campaign.h
    #define MAXIMUM_MISSIONS_PER_CYCLE          25

- This will further reduce the number of UFOs spawning, and it will also
  prevent the numbers of UFOs spawning *on average* per cycle from
  exceeding 8, which is a hard limit in the game anyway. The peak (8),
  will only be reached around 1000 alien interest, far ahead of our
  current campaign (which seems to be peaking around 400).

### Reasoning

The above two changes will drastically reduce the number of UFOs. Here's
how I think they will effect other aspects of the game:

**Nation Happiness:**

Currently, the only things negatively effecting nation happiness are
missions the player does not attack or completely fails (also UFO sales,
see below). As a result, the high number of UFOs was making it very
difficult for players who do not expand quickly enough. UFOs were
showing up in unseen areas causing nation happiness to drop early in the
game (\<-- my hypothesis). Reducing the number of UFOs should slow down
nations getting angry early in the game.

By reducing the number of UFOs, the player will have fewer to sell to
nations. This should not effect things too much. The current code
suggests that selling to one nation just angers others, so selling UFOs
actually works (in aggregate) a negative effect on nation happiness:

    cp_campaign.h
    #define HAPPINESS_UFO_SALE_GAIN             0.02
    #define HAPPINESS_UFO_SALE_LOSS             0.005

    cp_uforecovery_callbacks.c
    UR_DialogStartSell_f
        /* update nation happiness */
        for (i = 0; i < ccs.numNations; i++) {
            nation_t *nat = NAT_GetNationByIDX(i);
            float ufoHappiness;

            assert(nat);
            if (nat == nation)
                /* nation is happy because it got the UFO */
                ufoHappiness = HAPPINESS_UFO_SALE_GAIN;
            else
                /* nation is unhappy because it wanted the UFO */
                ufoHappiness = HAPPINESS_UFO_SALE_LOSS;

            NAT_SetHappiness(ccs.curCampaign->minhappiness, nat, nat->stats[0].happiness + ufoHappiness);
        }

If I understand this correctly, selling a UFO increases one nation's
happiness 0.02 and decreases the other seven nation's happiness by
0.005, leading to an aggregate happiness effect of -0.015. At first I
thought this was a mistake, but it might actually work well, because the
player can channel the effect to those nations it is unable to
effectively defend. Those it can defend will be happy enough because of
the positive results of missions. This aggregate negative effect from
something that seems like it should give a positive effect may actually
cleverly balance the game mechanic.

There is a separate problem with mission performance/nation happiness,
but that needs a separate solution.

**Economy/Research/Production/Disassembly:**

Players are likely to have less money because they have fewer UFOs to
sell. As a result, the research/production will probably be slowed down
a bit *in relation to game time*. But because the player will face fewer
UFOs over that period of time, it will feel like the game is progressing
more quickly. This means that the player may have less research
completed by the time certain alien interest levels are achieved, but my
guess is that this won't put the player in a very bad position. All
indications from player's comments suggests the game gets pretty easy in
the mid-to-late game, where this effect will be strongest.

**Employees:**

The player will face fewer UFOs between intervals where it receives
additional soldiers/scientists/workers. This could mean that the player
has more available employees than they need. But since this risks making
one aspect of the game easier rather than more difficult, I think it is
okay to leave as-is for 2.4 and adjust for 2.5 based on feedback.