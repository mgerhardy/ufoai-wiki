Weapon skills make no difference. Discussed with mattn. bug lodged on
sf.net --[Blondandy](User:Blondandy "wikilink") 21:16, 25 May 2007
(CEST)

I have been meaning to bring this up with a knowledgeable dev.
G_ShootSingle() from g_combat.c uses a function called GET_ACC() to
obtain the actor accuracy used in the spread calculation. If I read it
right (I'm not great at c) the 'weapon type ability' *makes no
difference*, which can't be correct.
  The chaingun isnt great at long range (the rounds dont go that far), I
have corrected the table. I have had a quick look at bolter.precision Vs
sniper.aimed. The bolter does have a higher point blank damage rate
([Damage_rate_table](Damage_rate_table "wikilink")). The spread of the
sniper is larger because it has a high modif (in the firedefs, 1.7).
modif is an odd and little-used parameter. Note that this changes for
actors with maxed accuracy (where the modif term goes to zero). a highly
accurate soldier could do better with a sniper rifle, my calcs on this
table assume an accuracy of 50. The sniper's high modif with an acc of
50 makes the overall spread worse for the sniper.aimed. This does make
sense within the UFO:AI world: the ufopedia says that the bolter can be
a type of sniper rifle, and it is more advanced tech.
--[Blondandy](User:Blondandy "wikilink") 20:38, 25 May 2007 (CEST)

Have you done any work with computing accuracy against the 'weapon type
ability' that each character has? Such as 75 sniper vs. 75 heavy
affecting the weapons? I have no idea how much these abilities weight in
on accuracy and wasn't sure if you knew.
--[Wanderer](User:Wanderer "wikilink") 19:23, 25 May 2007 (CEST)

I will look into this. I will present example calc. here. Also I just
realised that i am presenting damage rates beyond the range of some
weapons... --[Blondandy](User:Blondandy "wikilink") 15:03, 25 May 2007
(CEST)

There's something either very wrong with the weapon specs on Sniper
rifles or on the calculation for MDR when the Chaingun and Bolter is
beating out the Sniper at max ranges.
--[Wanderer](User:Wanderer "wikilink") 02:05, 23 May 2007 (CEST)

I find this and many of the other charts misleading because they do not
take armor into consideration. This is why the chaingun looks better
than the sniper rifle at a distance for example. But with the small
damage each bullet does with a chain gun (something like 20?) and an
alien in medium armor, the first few bullets do essentially no damage at
all. Whereas two hits with a sniper rifle could kill him because each
bullet deals more damage, overcoming the armor. I'd like to see this
table with each armor type taken into consideration. These charts are
only accurate if no armor is worn. --[Slow](User:Slow "wikilink") 00:44,
30 January 2008 (CET)