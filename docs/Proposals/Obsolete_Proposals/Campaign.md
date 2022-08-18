## The final campaign

This proposal describes the singleplayer campaign as it should behave in
its final incarnation.
<FONT color="red">This system is now (largely) implemented, though exact
formulas and values might differ. Use this article as a general
guideline to the campaign game mechanic.</FONT>

REVISED by --[BTAxis](User:BTAxis "wikilink") 00:38, 13 May 2007 (CEST)
after discussing the issue with [Wanderer](User:Wanderer "wikilink").
The revised version contains many of his ideas.

REVISED by --[Wanderer](User:Wanderer "wikilink") 05:35, 13 May 2007
(CEST) Included more detail into the process, did some formatting and
general cleanup, included more information regarding map scripts.

REVISED BY --[BTAxis](User:BTAxis "wikilink") 00:56, 14 May 2007 (CEST)
after another brainstorm session with
[Wanderer](User:Wanderer "wikilink").

## Overview

The campaign should be much less rooted in fixed definitions and targets
than is the case at the time of writing. Rather than having a set of
scripted missions, missions should appear depending on alien activity.
As such, the missions should not so much be part of the campaign, but a
result of the campaign parameters.

During the campaign, the aliens will pursue their goals. They will try
to attack cities, build bases, subvert the human population and
governments, and so forth. These activities will spawn missions
depending on what is happening. A landed harvester will generate a UFO
mission, an attack on a town will generate a terror mission, discovered
bases can be attacked. And of course the aliens will launch their own
attacks against PHALANX installations.

Over time, alien activity will increase in intensity. More UFOs will
visit Earth, and they will be larger and better armed. The soldiers
brought planetside will be bringing increasingly dangerous equipment,
and they will be harder to kill. This process should theoretically
continue indefinitely until the player is defeated, or wins the game.
This is important because it makes the campaign a race against time,
rather than a race to the finish.

The difficulty setting should ideally influence the process described
above. On higher difficulties, the aliens will gain in strength faster,
and their numbers will be larger than on lower difficulty settings. In
effect, this means that players will have less time for R&D in the
strategic part of the game, and will have to fight harder in the
tactical part (of course, other difficulty-related factors have an
impact on that as well).

## Implementation and definitions

### Alien activity

Alien activity is determined by a framework of "interest" levels. This
interest level starts at 20 and keeps increasing over time. We will
assume an interest level of 1000 to be the point at which an average
player will be overwhelmed by alien activity. Good players will be able
to endure beyond this point, but everyone will have their limit. The
speed of increase of interest levels, and the 'upper threshold' that a
player will be able to survive, will be affected by the difficulty
levels.

In addition to the overall interest level, the aliens will have
interests in a number of categories. These categories include:

- Recon
- Harvesting
- Terror Attacks
- Base Attacks
- Base Building (this interest doubles as government subversion by
  non-[XVI](XVI "wikilink") means)
- Base Supply
- [XVI](XVI "wikilink") Propagation
- Interception (this interest doubles as attacking phalanx aircraft or
  installations)

The best way to think of interest levels is to think of them as overall
goals the overmind has. The overmind is also distracted by the running
of its ship, so at the beginning, Earth is nothing more then a footnote.
The longer the planet is able to defend itself, the more interest the
overmind takes in the conflict. The more interest, the more resources
it's willing to use.

Interest will spawn events. Note I don't say missions. A mission that
the player can affect should be about 90% of the events available, but
the framework should be built to allow for non-player interactive
events. It is also possible that an event is "null", meaning the event
does not happen at all.

There are two kinds of interest. The first is categorical interest, such
as interest in Recon or Harvesting. The other type is the 'overall'
interest.

### Choosing the Interest Events

First, we need to separate the process out to cycles (three days) when a
new alien "activity cycle" will start. The amount of alien missions to
be generated will be calculated from the overall interest rate (as per a
bell curve, such as **\#missions = (CurInt/10)^(0.6))**, rounded down.
This bell curve will ensure that the number of alien events is ramped up
fairly early on in the game, while the late game mainly causes events to
be harder to beat.

For each mission to be spawned, the framework will select what kind of
mission to spawn. The total value of all categories will equal 100%, and
each category's value divided by the total will equal the chance it has
of being selected. When an event ends, alien interests are updated. For
example, if a recon mission is a success, alien interest in recon will
decrease of 20%, and terror attack will increase of 10% (latter in the
game, a success may also imply [XVI](XVI "wikilink") spreading or base
supplying). If the same recon mission is a failure (phalanx killed
aliens), the result will be a 5% increase in recon interest, and 10%
increase in intercept interest.

Therefore, depending on player activity, alien interest may evolve in
different directions.

### Increasing and decreasing interest

The overall current interest starts at 20 and rises at a steady pace (1
point every 28h in normal difficulty). This means the interest will
reach 1000 after a little more than three game years, which is a period
of time that fits within the storyline.

The individual interests start at their own specific values. They will
increase and decrease depending on what happens in the game.<B>It is
important to note here that the INCREASE percentage is taken from the
overall interest value, and the DECREASE percentage is taken from the
category's own interest value.</B>

In addition, each interest category is weighted. The weight is a
modifier that applies to all increases that are applied to that category
interest, but not to the decreases. A second weight applies on top of
this, but only if the category's interest value is greater than the
overall interest value. In effect, this means that it IS possible for
events that are more difficult than "average" to occur, but the greater
the discrepancy, the smaller the chances of it ever happening.

Examples:
\*Suppose overall interest is at 50, Terror is at 30 and Base Building
is at 12. and Recon is at 36. Per the calculation given above, this
corresponds to two events per cycle. Suppose one Recon mission is
selected, and the other event is null. Suppose also that the recon
mission is a success. That means the Recon category decreases to 28 (as
we round down), Terror is increased as per 30 + 50 \* 10% = 35.

- Suppose that same mission fails because the player intercepted it.
  Then Recon is increased as per 30 + 50 \* 5% = 32.

<!-- -->

- For the next example, suppose overall interest to be 50 again, with
  Recon also at 50. Should the mission fail this time, the increase in
  Recon is slower, because it gets weighted extra. This is because it
  now exceeds the overall interest. Supposing this extra weight is .5,
  the calculation would be 50 + 50 \* 5% \* 50% = 51.

### Executing an event/mission

Once a list of missions is thus generated, the missions will be executed
over the course of the activity cycle. Once executed, they will be
carried out as in code, in combination with team an equipment definition
script files that help generate alien teams to be used during the
events.

At this time, It is undetermined if the number of mission types should
be broader, to allow for a second 'mission specs' file to be used, or if
a smaller number of mission types with the parameters to be loaded
included with the declaration would be the best effort. If a second
mission script file is used, these script files provide parameters to
the game engine that help determine what UFO to spawn, whether or not it
should have escorts, where to spawn the UFO, where to conduct the
mission, how long to spend on each action associated with the mission,
and so forth.

### Category Definitions

Here is a slightly more in-depth description of the mission categories
and their behavior.

#### Recon

Recon can spawn either aerial recon missions (UFOs that fly across the
geoscape without landing and disappear after a while) or ground recon
missions (UFOs that fly around, land in one or more locations, then
disappear). Ground recon missions may be spawned spontaneously if the
aliens have an operational base.

#### Harvesting

Harvesting spawns UFOs that fly to an area, land, gather life-forms from
Earth by means of Bloodspiders and soldiers with Kerrblades, then take
off and return to the mothership.

#### Terror Attacks

Terror Attacks are missions to human population centres for various
purposes, including harvesting, XVI propagation, and increasing
unhappiness with PHALANX. Terror missions should always occur in a major
city. The UFO is spawned some way away from its destination, then
proceeds to fly there and generates a terror mission. Terror missions
may be spawned spontaneously if the aliens have an operational base.
These missions don't have a recoverable UFO.

#### Base Attacks

Base Attacks are assault missions on PHALANX bases. A UFO will be
spawned on the map, fly to a PHALANX base and, should it survive,
initiate a base attack mission. Base Attack missions may be spawned
spontaneously if the aliens have an operational base.

#### PHALANX Interception

PHALANX Interception missions are direct hostile actions by the aliens
against PHALANX. PHALANX Interception missions come in two flavors: a
roaming variant, which is a UFO or wing of UFOs that flies around the
geoscape and tries to intercept any PHALANX craft within a certain
radius, and a targeted variant in which the UFO specifically seeks to
destroy a randomly picked PHALANX installation on the geoscape. The
targeted variant will also indiscriminately attack PHALANX craft, but
the roaming variant should largely ignore installations.

#### Base Building

A Base Building mission is a mission to establish a new base on the
geoscape. At lower values (say under 400), these missions will never
cause a new base to be built, but will instead contribute to the
subversion of governments by non-XVI means. When a Base Building mission
is successful, a new alien base will be created at the location the UFO
landed, but stays in "under construction" mode for 30 days before going
online. The base stay invisible to player until he discovers it.

#### Base Supply

Base Supply missions consist of supply transport UFOs that are spawned
on the geoscape, fly to the nearest alien base, stay there for a while,
then take off and return to orbit. Interest in Base Supply increases
over time by a fixed value multiplied by the amount of bases on the
geoscape, both operational and under construction. The more supply an
alien base get, the bigger it is.

#### Subversion

Subversion missions are intended to change a nation's government to
think more highly of the aliens and less highly of PHALANX. In gameplay
terms, a successful Subversion mission lowers the happiness for the
nation it occurs in. A Subversion mission consists of a UFO that flies
to its destination, lands and stays grounded for some time, then flies
off again. The mission is considered successful if the UFO manages to
take off again.

#### XVI Propagation

XVI Propagation missions consist of missions where the goal of the
aliens is to infect more humans by several possible methods. Alien
syringes, Breeder units, and terror attacks on hospitals/blood banks are
all methods by which XVI can spread rapidly. The mission will be carried
out by a UFO and its crew, optionally aided by infected humans.
Propagation missions can be initiated by UFOs or spontaneously in
infected regions.

XVI Propagation missions must never occur in an area that isn't
connected to at least one operational alien base by the XVI infection
spread. PHALANX bases in regions with high XVI saturation should suffer
fairly frequent attacks from infected humans. Once a region reaches 100%
saturation, any PHALANX bases in the area should be automatically
destroyed.

The XVI propagation category poses an interesting problem with the
concept of 'saturation'. Once a region reaches 100% XVI saturation, no
more Propagation missions should occur there. This category will have to
monitor the region infection levels from the hard code to determine its
values. However, the higher infection levels there are in regions with
established alien bases, the higher BaseBuilding should increase so that
the overmind can saturate more landmass with XVI.

### Maps

As ALL missions are generated randomly (excepting a few story-related
fixed ones, but even these are spawned depending on factors outside the
coders' control), maps cannot be associated with missions directly.
Instead, the Earth's terrain should be divided into a set of "zones".
Each zone "layer" should focus on one criterion. Examples of criterea
are terrain and architectural style.

To determine the correct map for a region, especially when dealing with
the random maps, four criterion must be reviewed. 1) Terrain or zone in
question. This can be anything from as simple as 'desert' to 'New York
City'. 2) The type of mission occurring. A Terror Mission won't occur on
a farm, and a ground recon wouldn't occur in the middle of Bangkok. 3)
The alien ship in question, to determine the right build tile. 4) The
player's ship in question, to determine the right build tile and to make
sure there's enough spawn points on the map.

#### Implementation

Currently the thinking is the following.

First, a map.ufo file. This file would contain the parameters explaining
how a map can be used. For example, the Antarctican City of Derriere
Gele (re-named Iskallt Arsle for the French localization) would have
definitions stating 'ice', 'city'. Missions would be 'Terror',
'Harvest'. Because the map was built as a solid build, instead of a
random map build, it would have a single ship type on it at this time,
so you would list 'Alienship: Harvester' and 'PlayerShip: Dropship1'.

A random file might have say, 4 listings, one for each of the Alienships
that could land there, so it could choose the right build method.

The second would be maps of terrain types.

See [Proposals/Map_Descriptors](Proposals/Map_Descriptors "wikilink")
and [Mapping/Terrain_Types](Mapping/Terrain_Types "wikilink") for more
details on the implementation of maps.