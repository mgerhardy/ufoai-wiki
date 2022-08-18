## Points to Consider

- How should strength relate to weight threshold?
  - 1 strength == 1 weight? might need adjusting the strength stats in
    order to make sense, specially if using real life units (currently
    we have soldiers spawned with 15 to 25 strength)
  - Or maybe some non linear relation between them? (from experience I
    can tell you that a few kilograms can make a huge difference IRL)
- How should the penalty calculated.
  - Flat penalty or based in the amount of overload.
  - In the later case linear penalty or some other formula.
- A bonus for actors that are carrying a very low weight.
- Maybe an absolute max to the weight an actor can carry, based on
  strength?
- Also: revise the system for gaining strength experience

--[DarkRain](User:DarkRain "wikilink") 04:53, 26 September 2012 (SAST)

- What came to my mind first - Will a penalty only affect the soldiers
  ability to walk around or will it also prevent him from firing a
  weapon? E.g. a weak soldier picks up a Rocket Launcher and gets a
  penalty. Now he can (slowly, but he can) carry that weapon around the
  battlefield using the remaining TUs, but not fire it?
  --[ShipIt](User:ShipIt "wikilink") 10:28, 26 September 2012 (SAST)
  - Yeah, this is an issue. It's possible that a soldier will have a TU
    penalty large enough to prevent him from firing a weapon (sniper
    rifle for instance) because he just doesn't have enough TUs. When we
    test if a weight leaves a soldier encumbered or not, we should also
    test whether a weight makes it impossible to use a firemode for an
    equipped item, and alert the player. I've put another error message
    text below. --[H-hour](User:H-hour "wikilink") 12:10, 26 September
    2012 (SAST)

## UI Suggestion

Here is a simple suggestion to display the weight. Putting it in this
window makes it available in base and in the HUD, for
campaign/multiplayer/skirmish. When weight is normal, text can be white.
When weight is very light, it can be green with a little icon by it (I
can supply icon, just ask). When weight is too heavy, it can be red with
a little icon by it. Icons will have tooltips.

![<File:weights_ui_proposal.jpg>](weights_ui_proposal.jpg "File:weights_ui_proposal.jpg")

Ideally, when adding an item to the soldier's inventory, if the weight
will exceed his maximum capacity, it should pop up a small window
alerting him to this and forbid him from adding the new item.

Text for the UI tooltips/errors:

light icon: "This soldier will gain \* TUs because he is not carrying
much."

heavy icon: "This soldier will lose \* TUs because he is carrying too
much."

capacity exceeded error: "This soldier can not carry anything else."

firemode can not be used error: "This soldier no longer has enough TUs
to use the following items: \n\nWeapon: Firemode (TUs required)"

To implement the UI stuff, I would just need to know where in the code
the soldier's weight is being totalled, when the game is checking the
weight again (ie - when items are added/removed), and I can add the
confunc's needed in.

--[H-hour](User:H-hour "wikilink") 12:27, 25 September 2012 (SAST)


I wouldn't insert UI calls directly in the inventory code, (the AI uses
it too, for example) but the UI container nodes behaviours could be used
for this. --[DarkRain](User:DarkRain "wikilink") 05:02, 26 September
2012 (SAST)

## Proper Weights

Doing some quick internet research, soldiers report up to 45kg of gear
on long haul stuff. But our guys are rapid response, deployed to the
battlefield. They don't carry rations or survival gear. I found a page
on globalsecurity.org which showed a "Fighting Load" at around 18kg.
Check the table near the bottom and the section titled "The bottom line"
on this page
globalsecurity.org/military/library/report/call/call_01-15_ch11.htm

Other things to keep in mind. An M4 Carbine is around 3kg loaded with 30
rounds. A Barrett M82 (50 cal sniper rifle) is 14kg. The Carl Gustav
rocket launcher is 8.5kg, but most of the weight is probably in the
rounds.

Since a soldier starts with 15-25, we could make it simple: 1 strength
point = 1 kg capacity. However, the way the UI is done now, all the
ability/skill bars use the same template, which means empty-to-full is
expected to be the same. In other words, we may want a system where the
soldier can grow his capacity to 75-100. In this case, we'd need a
different equation between Strength value and kgs capacity.

Here is a quick, first pass at a rate: A soldier starts with 15kg
maximum capacity. For every 5 strength points, he gets an extra kg.
Encumbered when exceeds 75% of capacity. Extra speed when below 30% of
capacity. That would work out to:

`Str    Max Enc Extra  Speed`
`20 19  14.25   5.7`
`30 21  15.75   6.3`
`40 23  17.25   6.9`
`50 25  18.75   7.5`
`60 27  20.25   8.1`
`70 29  21.75   8.7`
`80 31  23.25   9.3`
`90 33  24.75   9.9`
`100    35  26.25   10.5`

With this rate we can't really model realistic capacity. In reality, an
average soldier COULD carry 50kgs (though he wouldn't typically fight
with that, he could walk around alright). Another option would be to
have a much lower encumbrance threshold (say, 50%) with a rate that
starts at 30kg maximum capacity and gives an extra kg for every 3
strength points. Encumbrance at 50%, speed boost at 20%:

`Str    Max Enc Extra Speed`
`20 36.6    18.3    7.3`
`30 40  20  8`
`40 43.3    21.6    8.6`
`50 46.6    23.3    9.3`
`60 50  25  10`
`70 53.3    26.6    10.6`
`80 56.6    28.3    11.3`
`90 60  30  12`
`100    63.3    31.6    12.6`


Are we sure we want to have a soldier reach 75 - 100 strength? As with
other abilities there are other actor kinds that will have a higher
natural strength, like some aliens for example (I'm thinking ortnoks),
and both humans and aliens share the same skill range (MAX_SKILL is
defined as 100)

--[DarkRain](User:DarkRain "wikilink") 04:50, 26 September 2012 (SAST)


I'm open to other possibilities. My first thought was to have all
soldier skills and abilities follow the same general trajectory (rookies
start around 20, elites end game around 70-100). This would avoid
confusing the player, who might see his strength growing more slowly
than other abilities and think he's doing something wrong. But your
point about other actor kinds is good to keep in mind. It might be worth
considering all abilities, where humans should max out, etc. I'm
unfamiliar with how Speed and Mind work currently. In general, I favor
consistency as a learning aid. --[H-hour](User:H-hour "wikilink") 12:10,
26 September 2012 (SAST)


Something to keep in mind: there is a hardcoded max for the experience a
soldier can gain per mission in a given stat, this was originally
calculated assuming an average career length of 100 missions for a
PHALANX soldier

That means that in 100 missions a soldier can gain up to (assuming that
they get max exp every time): 25 strength, 14 speed, 30 accuracy, 39,
mind, 50 <weapon skill> and 99 max HP

See:


Thanks for that DarkRain. These numbers are interesting. I think making
the stats conform to each other will take a lot more work, so I suggest
we ditch the idea of getting Strength to 70-100. We can do a straight up
system: 1 STRENGTH = 1 KILOGRAM of maximum-can't-equip-any-more weight.
Rookies could start with 35 and use the second of my two systems above.
Is everyone alright with this idea? I believe if we want to rationalize
all stat values at some point in the future, we can change it then.
--[H-hour](User:H-hour "wikilink") 12:49, 27 September 2012 (SAST)


Yes, I guess that's fine. --[DarkRain](User:DarkRain "wikilink")

<!-- -->


In the mean time is a list of equipment with proposed weights, if
someone wants to have a look, it will probably go under severe
adjustments but need to start somewhere.

--[DarkRain](User:DarkRain "wikilink") 04:05, 28 September 2012 (SAST)


Cool. I went ahead nad put it up in another proposal page on our wiki so
we don't lose it:
[Proposals/Equipment_Weights](Proposals/Equipment_Weights "wikilink").
We can also discuss it as needed there.

## Penalty Suggestion

I am in favor of a flat penalty. If a soldier is encumbered, he loses
50% of TU. If soldier is below the light-weight threshold, he gains 50%
of TU. (Actual numbers subject to adjustment, of course.) It has the
benefit of being clear and consistent, so the player can more easily
calculate the costs/benefits. Also, by nailing the full penalty/bonus
around certain thresholds, it will encourage strategic thinking: how can
I equip the maximum on this guy without exceeding this threshold. Or,
since I'm already over the threshold, I might as well load him up with
extra ammo for the snipers/scouts.

When we distribute the penalty/bonus throughout the weight, we force
these kinds of decisions on every single piece of equipment the player
is adding, which could be a little tedious. Furthermore, by distributing
it evenly, there are no MOMENTS OF DECISION -- times and places in the
game where the player feels like this decision is one of the important
ones. If they're all equal, the game can feel a little flat.
--[H-hour](User:H-hour "wikilink") 13:13, 25 September 2012 (SAST)


I mostly agree with H-Hour, although "gaining" TUs seems not very
intuitive to me. I would assume the given TUs for a soldier are to be
his maximum. If he adds weight, this number goes down.

I´d say: A soldier can carry some percentages additional weight without
a penalty, as you add more weight on each threshold he loses some more
percentages of his TUs. This means, if an actor has 20 Strength and 30
TUs, he could carry **100%** (20 kg) additional weight without a penalty
(loosing **0**%), up to **120**% (24 kg) losing **10**% (3) of his TUs,
**150**% (30 kg) losing **30**% (10) of his TUs up to were he simply
cannot carry more weight. **Numbers** open for discussion and scriptable
anyway.

--[ShipIt](User:ShipIt "wikilink") 10:28, 26 September 2012 (SAST)


The reason I chose the system I did is to try to reinforce and
communicate to the player a "normal" weight load. In order to gain the
TUs, the soldier would need to carry very little. I don't want the
player to react to a "normal" load as though he were suffering a
penalty. I realize it's just semantics -- giving a TU "bonus" for low
weight is functionally no different than the system you describe ShipIt.
I'm more concerned about how to display to the player that it is normal
for them to be in the middle and only in special circumstances would
they want to be below or above certain thresholds. I'm not too concerned
about precisely how the mechanics work behind the scenes -- starting
with a maximum and working downwards seems fine to me -- but I do want
to be clear with the player what they "ought" to do.
--[H-hour](User:H-hour "wikilink") 12:10, 26 September 2012 (SAST)


I'm fine with both 'ways' as it is the same way technically. We can't
increase the TUs very easily, because we have a max route length that a
player can walk. --[Mattn](User:Mattn "wikilink") 07:26, 27 September
2012 (SAST)


That is something to consider, I remember someone mentioned that even
the normal TU gain that comes form increased speed caused some soldiers
to have more TU than the max pathing length.

--[DarkRain](User:DarkRain "wikilink") 19:51, 27 September 2012 (SAST)


Can we raise this without overloading the pathfinding system?
--[H-hour](User:H-hour "wikilink") 12:09, 29 September 2012 (SAST)


We might just give it a try - i've doubled it and gave 100 TUs more on
actor creation and did not yet see a problem - but it is definitely more
computation work - so we have to profile it. Maybe aDuke knows more
about it. --[Mattn](User:Mattn "wikilink") 19:41, 29 September 2012
(SAST)

.

MAX_MOVELENGTH is obsolete as of now. The pathfinding depth is
determined by the remaining TUs of the actor. MAX_ROUTE is merely a
limiter to ensure sane TU values, so increasing it has NO effect. The
problem comes with increased TU values for actors. While higher TU
values for soldiers will cause a slight increase in cpu consumtion
(squared, but we don't do that very often), for aliens it could be a
problem.

AI works like this (simplyfied): For every spot I can walk, check if I
can shoot at an enemy. If so, do a secondary pathfinding from there with
the remaining TUs and check if I can hide there.

Pathfinding itself is not the big cpu consumer, the checks 'can I shoot
at' and 'am I hidden' are. Increasing the TUs will increase the number
of those checks.--[Duke](User:Duke "wikilink") 23:40, 2 October 2012
(SAST)


This may not be a big problem then. In most cases I expect we will want
to keep TU down around levels we're currently at for aliens, and
improvements in alien equipment code should keep them from having Max
TUs. So, barring any custom modifications with ridiculous AI TU counts,
I don't see the number of TUs of an average alien increasing
considerably. But we'll have to perform checks on alien equipment to see
what their actual TU is at various stages of the game.
--[H-hour](User:H-hour "wikilink") 00:39, 3 October 2012 (SAST)

## Stat Increase

### Increase Mechanism

What causes strength increases now? What should cause strength
increases? The obvious one is: carry more weight in a mission, gain more
strength. It's not a terribly sophisticated method, but I can't think of
anything better. We could use the thresholds to adjust how much strength
increase a soldier gets each mission. If encumbered, they get 100% of
mission max. If normal, they get 50% of mission max. If extra light,
they get 10-15%. Thoughts? Or any info on what causes strength increase
now? --[H-hour](User:H-hour "wikilink") 13:23, 27 September 2012 (SAST)


It just occurred to me that we'd need to decide WHEN to measure a
soldier's load (start of mission, average of all turns, end of mission).
I am in favor of start of mission. It will prevent extremely dedicated
leveling fanatics from spending the last few turns of a mission having
their soldiers pick up everything they can find. They can still game it
by starting a mission with loads of equipment and then dropping it on
the first turn, but this would be a dangerous thing to do: the first
turn is often when the player is most exposed and so he needs all the TU
he can get to find cover and/or eliminate threats. Another alternative
would be to measure his weight at the beginning of the second turn, but
I have the slight feeling that this is trying to be too clever. We could
check each turn and average them, but I fear this will reward people who
spend every spare TU of an idle soldier picking stuff up. We should
discourage this kind of mundane leveling if possible.
--[H-hour](User:H-hour "wikilink") 13:34, 27 September 2012 (SAST)


Whatever system you choose, it will always be exploitable in some way.
We could also give a flat/percentage increase per mission, which would
depend on the starting or current strength value. This way, the the
weaker soldiers will need to play more missions in order to reach the
max than those that have better starting stats.

--[ShipIt](User:ShipIt "wikilink") 17:17, 27 September 2012 (SAST)

There are four systems proposed to choose from below. IMHO we should
choose one where this **NOT** works : The player gives his soldier as
much equipment as he can. During the mission the soldier crawls savely
through the dropship and finaly is rewarded with max strength increase.

--[ShipIt](User:ShipIt "wikilink") 09:38, 7 October 2012 (SAST)


Unfortunatley none of the four systems prevent that, even a flat penalty
will reward a soldier that stays at the dropship with max strength
increase possible, sadly I can't think of a system that'll prevent it,
without the risks that H-Hour mentions below.

--[DarkRain](User:DarkRain "wikilink") 18:51, 7 October 2012 (SAST)

Right now just taking part in a mission will give 46 exp (of 214 max),
additionally moving around with heavy armours (the ones that cause a TU
penalty) will give more experience, crawling gives twice the experience
than walking.


I am really not in favor of the idea that moving around or crawling
gives extra experience. It is very non-intuitive for the user and
rewards really mundane and mindless leveling (running soldiers around or
crouch walking for the sake of stat gain). Can we remove this somehow? I
would prefer just a flat increase per mission, as ShipIt suggested, or
the light/normal/encumbered method I described.
--[H-hour](User:H-hour "wikilink") 11:33, 28 September 2012 (CEST)


Well, I think the TODO that says: "make a formula for this once strength
is used in game" means its OK to change this.
--[DarkRain](User:DarkRain "wikilink") 20:06, 29 September 2012 (SAST)

Also, you probably know it already but I will mention it any way, the
stats are calculated as initialSkill + (experience / 100) ^ 0.6, which
means it ramps up faster at the beginning and slows down the more exp is
gained (for example gaining 25 points of strength will take 100 missions
at the max exp of 214, gaining 50 points would take 325 missions at max
exp)

--[DarkRain](User:DarkRain "wikilink") 19:46, 27 September 2012 (SAST)


Sorry, but I'm not familiar with the ^. What math is happening there? I
think it's very good that it goes quicker at the beginning.
--[H-hour](User:H-hour "wikilink") 11:33, 28 September 2012 (CEST)


Exponentiation: initialSkill + (experience / 100)<sup>0.6</sup>
--[DarkRain](User:DarkRain "wikilink") 22:45, 28 September 2012 (SAST)

When I plug this into Calc, it looks like the curve is very gradual. Is
this correct (image below) or is Calc not performing the exponential ^
0.6 correctly? --[H-hour](User:H-hour "wikilink") 12:19, 30 September
2012 (SAST)

![<File:strength_gain_formula.png>](strength_gain_formula.png "fig:File:strength_gain_formula.png")


Hmm... the curve does indeed look flatter than I thought, but it seems
to be correct. --[DarkRain](User:DarkRain "wikilink") 16:49, 30
September 2012 (SAST)

[DarkRain](User:DarkRain "wikilink"): on your user page you say you have
implemented a "3-stage" system. Can you explain in more detail?
--[H-hour](User:H-hour "wikilink") 01:55, 7 October 2012 (SAST)


I probably didn't choose the best wording (and I forgot to post here
about it as well), but it would be like option C below, three stages
light, normal, encumbered just with different values, (its the second
easiest: two lines of code) --[DarkRain](User:DarkRain "wikilink")
05:13, 7 October 2012 (SAST)

I'd like to suggest that the weight check for XP gain does not occur at
the end of the mission. This is the time of the mission which is most
tedious, and in which players have the most idle TUs. For this reason, I
think the incentive to run around picking up weight is too high at this
stage. I'd like to suggest either checking at the start of the mission
(easier) or checking at the start of every turn and averaging the total.
At the start of the mission, the player is most exposed to alien fire
and most in need of his TUs, so the incentive to waste them on
XP-gaining tricks is at its lowest point (a soldier would have to waste
several TUs dropping things in the first round). The more full-proof way
is to check at each turn and average the total, but it may be more work
than it's worth. I defer to DarkRain's judgement on this.
--[H-hour](User:H-hour "wikilink") 01:55, 7 October 2012 (SAST)


Checking at start of mission or at start of each turn is pretty much the
same work to implement just changing the location of the check, I will
need to change the mission score structure for either one anyway
--[DarkRain](User:DarkRain "wikilink") 05:13, 7 October 2012 (SAST)

Good, our voting is evenly split. :) So the trade-off between A and D
(below) seems pretty straight-forward to me. (A) can not be gamed in any
way, but soldier development is not linked to soldier performance. (D)
links soldier development to soldier performance, but invites players to
take dummy soldiers on missions to gain exp.


Imo, as [DarkRain](User:DarkRain "wikilink") is the one doing all the
work, his vote should count twice. So if he still wants to go for (D),
I´ll support this. We could add 'action checks' later, if needed.
--[ShipIt](User:ShipIt "wikilink") 08:16, 15 October 2012 (SAST)

**Possible Alternatives/Workarounds**

- A new method: we give a strength exp bonus when a soldier makes a
  kill, depending on if they are light/normal/encumbered. This way a
  player *must* be using the soldier.
- We use D but add a check for particular soldier actions -- spotting an
  alien, shooting at an alien, etc. -- and only give the exp if a
  minimum set of actions are completed in a mission.
  - There is a real risk of disqualifying valid soldiers with this
    method, especially when there are not a lot of aliens in a mission.
    It could also leave players feeling cheated when valid soldiers
    don't gain expected exp. --[H-hour](User:H-hour "wikilink") 12:55, 7
    October 2012 (SAST)
- more ideas...

### Max Values

DarkRain said that in 100 missions strength can increase a max of 25. If
we started around 35 (STR = KG), that sounds about right, but could
probably be increased since few soldiers will gain max strength increase
in all 100 missions. If a soldier gains 25kg and we use the 50%
threshold for encumbered, he'll only actually gain 12.5kg extra carrying
capacity. We may want it to be a little higher so that power armour (for
instance) is really too heavy for some soldiers.
--[H-hour](User:H-hour "wikilink") 13:23, 27 September 2012 (SAST)


Regarding the questions about how many missions we face in 2.5. I don't
know. I don't have any save data for that and expect at least one more
change before 2.5 to reduce the count, so I'll probably have to wait for
after 2.5's release to get some good saves. If soldiers don't reach 100
we can always revise the max increase in the future, but I think it's a
fair estimate for now. It was a lot more before we reduced the number of
UFOs appearing. --[H-hour](User:H-hour "wikilink") 11:48, 29 September
2012 (SAST)

### Increase Values

DarkRain has helpfully created [a page describing how skills/abilities
increase](Skills/Improvement/v2.5 "wikilink"). The formula for strength
gain is currently: 150 \* (weight / strength) / ENCUMBRANCE_MODIFIER.
I've run some numbers on this and want to bring up two simple changes
for discussion. --[H-hour](User:H-hour "wikilink") 13:50, 15 November
2012 (SAST)

![<File:strength_gain.png>](strength_gain.png "File:strength_gain.png")

1\. **Increase strength more quickly**: In the image above, the top set
of numbers uses the existing formula with a starting strength stat of
35. The bottom set of numbers replaces 150 with 300. The cells
highlighted in red are where I've pegged a "normal" soldier progression.
With 150, an average soldier takes around 60 missions to gain 10
strength. Although a player may face around 100 missions in a game, a
soldier is likely to face much fewer. Gaining 10 strength is a key
threshold in many cases for handling late-game armour and heavier
weapons adequately. The player ought to be able to reach this with a
**reasonable vet**.

For this reason, I think 300 is a better constant in this equation. If
you look at the bottom table, a soldier gains 10 strength between 20 and
40 missions, which sounds more appropriate to me. It also means that a
soldier gained in the middle of the game can still be trained up to take
on all necessary functions. I think this is important given the new rate
of attrition I expect for soldiers on the battlescape.

A nice side-effect of this higher rate is that a soldier hits the
maximum gain almost as soon as he hits the maximum encumbered rate. This
will reduce incentives to load a soldier with tons of unnecessary
equipment just to increase the strength gain. Once they're over the
threshold, there is no reason to load more stuff.
--[H-hour](User:H-hour "wikilink") 13:50, 15 November 2012 (SAST)


As I've said before, you have more experience with the game balance, so
I will trust your judgment on this, I'd like to hear what others think,
though.

--[DarkRain](User:DarkRain "wikilink") 21:12, 15 November 2012 (SAST)

2\. **Narrow min/max margins of starting strength stat**: The equipment
weights system has turned the strength stat into one of the most
important stats for a soldier. A low strength can prevent a soldier from
wielding some important weapons. A low-strength explosives expert is
especially disadvantaged.

I think this is exacerbated by the large spread in the starting soldier
strength. Currently, a soldier starts somewhere between 30 and 40
strength, which means a weak recruit could take 20-40 missions to
achieve a strong recruit's capabilities (if we implement faster gain
above). I'm worried that this will cause too much of an incentive to
simply ignore all but the strongest recruits. I propose narrowing the
spread to something like 33-37, so that any gap could be overcome in
10-20 missions. --[H-hour](User:H-hour "wikilink") 13:50, 15 November
2012 (SAST)


I've always thought that initial skill ranges are a bit wild (not only
for strength), specially since they are completely random, if average
values were common and extremes were rare, maybe it wouldn't be so bad.

--[DarkRain](User:DarkRain "wikilink") 21:12, 15 November 2012 (SAST)

Any objections? Things I've missed?


I played for a while (2084 Aug 29, 37 missions, switching to nano armour
right now) and, to be honest, up to this point I cannot see any reason
why we would need to change something here.
--[ShipIt](User:ShipIt "wikilink") 21:45, 15 November 2012 (SAST)


And - Yes. It makes the game harder, more challenging. A lot of People
will not like this. --[ShipIt](User:ShipIt "wikilink") 21:45, 15
November 2012 (SAST)

I think the issues I've pointed out really occur in the later stages of
the game, and that may be why you're not experiencing any problem yet.
Needlers and Power Armour were the two main sources of concern. But
you've played with the weight system more than anyone else so far, so I
will defer to your judgement. We can always change it easily later on.
There is still a long while before 2.5 goes out and I'll be starting my
own run-through as soon as I work out the final major rebalancing
(disassembly + a few weapons issues). What do you think about reducing
the rookie stat spread (point 2)? --[H-hour](User:H-hour "wikilink")
00:31, 16 November 2012 (SAST)


I am not opposed to changes. But what is proposed here looks like a
regression to me. Reducing the stat spread will reduce diversity,
reducing diversity will reduce the freedom to choose. Right now in my
game I have a vet (20 missions) carrying a GL. He is not that strong, so
I cannot equip him with nano armour without thinking about the other
stuff. I finally found a setup he can wear, but had to change the
equipment of other soldiers as well. Those kind of decisions help to
give my soldiers a face. This is something I missed in previous
versions. I have to admit that strength is now the most important stat.
But this is not because of the implementation of the weight/encumbrance
system, but because the other stats are not properly implemented. The
Speed stat increases in slow motion without any visible effect, the
accuracy of the weapon seems way more important than the soldiers stat,
mind goes up in light speed, the soldier is promoted but again there is
no real reward for the player. Meanwhile strenght gives a feedback to
the player. Vets are something of more value because their increased
strenght rewards the player by giving additional possibilities. Do we
want a human soldier to wear Power Armour and a Heavy Needler and (bunch
of even more stuff) and still move across the battlefield fast and
smooth? Yes, if the player is able to keep his soldier alive long
enough. This is the reward he gets if he plays well. Instead of
softening up the Strength stat/weight system, I propose to take a closer
look at the other stats. Increasing Speed should increase TUs by a
reasonable amount and give a better chance to shoot first in unexpected
encounters. Increasing Accuracy should give an increasing chance of
critical hits. There should be something like this for Mind as well.
Than we can review the Stength/weight system.
--[ShipIt](User:ShipIt "wikilink") 09:56, 16 November 2012 (SAST)


I think you make some good points, and I agree that the other stats
sometimes feel kind of worthless. Perhaps if DarkRain is interested we
can start some discussion at some point about how to improve them,
either for 2.5 or for 2.6. Given the stability issues, it could be a
while before 2.5 comes out. --[H-hour](User:H-hour "wikilink") 13:22, 16
November 2012 (SAST)

<!-- -->



Well, yes, other stats aren't very well implemented -- speed is
virtually useless -- I think discussing about possible improvements
would be nice, but might want to take the discussion somewhere less
cluttered, maybe [here](Talk:Skills "wikilink")

--[DarkRain](User:DarkRain "wikilink") 20:02, 16 November 2012 (CET)


A proposal for each stat would be nice. I'll have a think and maybe do
some code-diving to see how dramatic the effects are. Then maybe make
some proposals. Feel free to make some yourself if you've got ideas.
--[H-hour](User:H-hour "wikilink") 00:08, 17 November 2012 (SAST)

I know we will hit the wall at some point in the game. In late stage new
recruits with starting stats will become useless. The player needs to
counter this by train not only one or two squads, but a number of
soldiers with combat experience. This is part of a balanced strategy.
Also, at this point we can introduce the revival of the starting weapons
with advanced ammo. And there is the proposal about implants, which I
imagine could be used to pimp soldiers stats/skills in late game.
--[ShipIt](User:ShipIt "wikilink") 10:19, 16 November 2012 (SAST)

If I was forced to propose something: It would help a lot if we could
make the increase mechanism depending on the campaign difficulty level.
--[ShipIt](User:ShipIt "wikilink") 10:29, 16 November 2012 (SAST)

## Roadmap?

When this could/is expected to/should be included into the game? This
seems easy enough to be ready soon, but the re-balancing for 2.5 is
already huge, and I'm not sure how many balance-altering game mechanics
should be included in a single release, especially since I'm not the one
trying to keep the game balanced.

--[DarkRain](User:DarkRain "wikilink") 05:31, 26 September 2012 (SAST)


I would say that this is up to Nate, but I would vote for a sooner than
later implementation, because we would need this for the multiplayer
balancing, too. The teams should be equally weighted.

--[Mattn](User:Mattn "wikilink") 09:58, 26 September 2012 (SAST)

<!-- -->



I'm ok with quick. 2.5 is going to be a major release in terms of
balance-altering changes. In some ways, it's easier (and better) to do
all-in-one balancing than piece-by-piece balancing. I've rebalanced
heavy weapons after removing the heavy weapon skill, and I'll need to
rebalance them again after we implement the weight system. I think it's
gentler on our users to put as much rebalancing in one major release as
possible. They'll have to re-learn a lot of things with 2.5, and making
them re-learn it all again in 2.6 would be annoying.
--[H-hour](User:H-hour "wikilink") 12:10, 26 September 2012 (SAST)

<!-- -->



Then go for it DarkRain, but please keep in mind while coding this that
i need access in the multiplayer cgame implementation, too (via the
cgame api of course, not cia direct calls - if you have questions about
it, just ask) - because we plan to make multiplayer teams more fair and
use the weight value (and other stuff) for this to ensure that a player
does not carry too much equipment into a multiplayer round.
--[Mattn](User:Mattn "wikilink") 07:25, 27 September 2012 (SAST)

## Cgame access

What will need to be accessed from the cgame api? I have only checked it
lightly so far but shouldn't be a problem (but I'll come back asking if
I get stuck)

## Making it scriptable?

Would it be very difficult to make the basic thresholds and penalties
scriptable at the campaign level? I would think of adding the following
parameters to a campaign definition:

`weight_light       0.2`
`weight_heavy       0.5`
`weight_normal_penalty  0.3`
`weight_heavy_penalty   0.6`

Also, making the max-weight-gain-per-mission scriptable at the campaign
level might help players mitigate any balancing issues.
--[H-hour](User:H-hour "wikilink") 12:18, 29 September 2012 (SAST)


That would be tricky, AFAIK the game (battlescape) and cgame (campaign
one of them) modules don't share data, also what about skirmish and
multiplayer?

--[DarkRain](User:DarkRain "wikilink") 20:42, 29 September 2012 (SAST)


Ahh, I'm not really up-to-speed on how the different parts of the game
talk to each other. I am surprised that skirmish and multiplayer would
even be aware of experience points. But it was only intended as a
request if it was easy. If not then there's no need to worry about it.
--[H-hour](User:H-hour "wikilink") 21:19, 29 September 2012 (SAST)


Well not even I am completely up-to-speed on it either, anyway sharing
campaign level data with the battlescape, would be tricky I think, but
if it is really needed, something can be worked, but preferably not at
campaign level (there \*is\* data shared between the client and server
sides of the game after all).

--[DarkRain](User:DarkRain "wikilink") 22:09, 29 September 2012 (SAST)


I don't think it's important enough to hold up implementation.
--[H-hour](User:H-hour "wikilink") 12:20, 30 September 2012 (SAST)

## Old Saves

It just thought of something: there might be some saves out there with
soldiers that will be over their max weight capacity once this is
implemented (specially if the starting strength is increased), my first
thought was to let them be, with a warning, thoughts?
--[DarkRain](User:DarkRain "wikilink")


I agree. I think this is acceptable. I assume they will suffer the
encumbered TU penalty and that any subsequent equipment changes will not
allow them to add more weight. It seems fair.
--[H-hour](User:H-hour "wikilink") 22:40, 3 October 2012 (CEST)

<!-- -->


I am one such user whose save-game history went from 2.3 to 2.4-dev and
now into 2.5-dev, and changes in soldier carryable weight were instantly
noticed (as well as some reworkings of aircraft weaponry which left many
of my ships with less/no guns while chasing aliens) ;) For example, my
previously elite squads with many dozens of missions per soldier are now
worse than rookies, unable to really shoot due to the penalties which
kick in at 12-14kg/person - a nanocomposite armor and all but the most
light of the guns plus 1-2 ammos often reach this level ;)

I suggest that if a save-game version is at all detectable (or guessable
by amount of soldiers with 25 strength and 80 missions count), such
soldiers should be converted upon import from an older UFOAI - based on
new average starting levels and number of missions behind times some
average value of strength increases they would have had if this game was
started as 2.5. -- [Jim Klimov](User:JimKlimov "wikilink") 00:28, 23
February 2013

## Finalizing Specifications (Please Vote)

Please vote yes/no/more-debate on a specification below. When something
is voted on, I'll move it over to the main page.
--[H-hour](User:H-hour "wikilink") 12:24, 28 September 2012 (SAST)

### Weight Values


All weights in kilograms. UFO script will need to be a float.


H-Hour: yes

ShipIt: yes

Mattn: yes

DarkRain: ok

### Soldier Weight/Skill


1 Strength skill = 1 kilogram of maximum weight.

Rookies start with 30-40 Strength skill (avg 35) and 46 max TUs (correct
Speed values to be worked out).

A soldier gets all TUs when they wear less than 20% of max weight.
(light)

A soldier gets 70% of TUs when they wear between 20-50% of max weight.
(normal)

A soldier gets 40% of TUs when they wear more than 50% of max weight.
(encumbered)


Note: current TU formula is (27 + SPEED \* 20 / 100)
--[DarkRain](User:DarkRain "wikilink") 22:18, 29 September 2012 (SAST)


That means in 100 missions TU raises only 3-4 points. If we change 27 to
39, the average rookie will start with 45 max TUs. Fine for now. We can
address whether the TU formula needs to be changed in the future.
--[H-hour](User:H-hour "wikilink") 12:32, 30 September 2012 (SAST)

`Kgs max    Kgs encumbered  Kgs fast`
`30     15      6`
`35     17.5        7`
`40     20      8`
`45     22.5        9`
`50     25      10`
`55     27.5        11`
`60     30      12`
`65     32.5        13`

`ROOKIE PROFILE`
`Tus max        Tus normal  Tus encumbered`
`45     31.5        18`



H-Hour: yes

ShipIt: yes

Mattn: yes (not sure about the values - but about the mechanic that 1
strength unit is 1 kg)

DarkRain: good starting point (but I'm concerned that max pathing
distance is 33 TU IIRC)

### Stat Increase

DarkRain has implemented this faster than we can agree on an increase
mechanism! In the interest of moving things along, I'll put up four
systems. Please choose A/B/C/D *when you're ready*, but feel free to add
more discussion above.

A\) Flat stat increase per mission. Each mission the soldier gets a set
amount of exp for strength.

B\) Weight is checked at start of mission and a percentage of exp is
given based on how much weight is carried (encumbered = 100%, normal =
50%, light = 10%).

C\) Weight is checked at end of mission and same as above.

D\) Weight is checked each turn and the numbers are averaged. Percentage
increase as above.


H-Hour: D (if possible, otherwise B is plenty good)

ShipIt: favours A) because everything else invites to play the 'pimp
your avatar' style

Mattn: A or D - but D only if ShipIt's concerns can be cleared out (i
have them, too), B and C or really no option imo, because 'pimp your
avatar' would be a real problem here.

DarkRain:D

### Max Values


Increase max strength growth over 100 missions to 35.


H-Hour: yes

ShipIt: yes, maybe less missions and a cap to what a human naturally can
reach

Mattn: unsure - it's 100 missions a little bit too much?

DarkRain: hmm... ok, but does someone know the average career length of
PHALANX soldiers with the new UFO rates?

### UI

Anything we need to discuss/vote on here?