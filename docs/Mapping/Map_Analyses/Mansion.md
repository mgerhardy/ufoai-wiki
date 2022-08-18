## Introduction

Author: --[H-hour](User:H-hour "wikilink") 18:31, 23 January 2012 (CET)

ShipIt has managed to build one of the largest maps ever produced for
UFO:AI. Large maps are great. Personally, I feel the average UFO:AI map
is too small. But large maps bring their own problems -- both technical
problems and gameplay difficulties.

This tutorial looks at the overall structure of ShipIt's Mansion map
while it is still in progress, to describe some of the gameplay issues
that arise. It will not address the technical issues.

A big thanks to ShipIt for volunteering to have his map scrutinized this
way. I chose the map because it offers an opportunity to praise many of
its great elements and illustrate some of the concepts that I think can
improve many maps.

*What follows is purely my opinion and offered for discussion.*

## Overview

Mansion is a great map that has done a lot of things right:

- Multiple paths into and out of buildings / map areas will encourage
  different strategies on multiple replays
- A good mixture of exposed and unexposed areas in the eastern half.
- Some great "fun factor" elements, like the giant castle walls
- Good vertical play. It doesn't all take place on one level.

But because it is so large, it runs certain risks that other maps don't:

- The player may spend forever hunting down that last alien
- All the tunnels could take many, many turns to fully explore
- Many of the map elements are so spread out that they can't work
  together: a soldier on a castle wall can not fire on the beach house
  or mansion effectively, a soldier in the beach house can not fire on
  the mansion effectively, etc.
- Currently, we can not set a minimum number of aliens, so it will be
  possible to face only three aliens in this giant map.
- Weapon ranges are tuned to fit our smaller maps, and having such an
  expansive map can expose the shortcomings in weapon ranges.

Let's look at an overhead view of the map.

![Image:mansion_sat.png](mansion_sat.png "Image:mansion_sat.png")

Those tiny dots in the southeast are the soldiers. One of the first
problems large maps face is the weapon range scale. The game does not
use realistic scales. A real-life sniper rifle can fire up to a mile and
it would take a lot of turns for the player to walk his soldiers that
far. The game uses a semi-realistic visual representation of space but a
very condensed tactical space. Weapon ranges, player movement and
eventually visibility, all take place across much shorter distances than
in real life.

As a result, the game must have a higher-than-normal level of "cover
density". I use this word to indicate the availability of tiles a
soldier can stand on that hide him partially or completely from threats
in a certain direction. This is an abstract way of saying boxes and
walls to hide behind. But it can be created in many ways: cliff edges,
sloped terrain, etc.

The following image is a rough visualization of the map's "cover
density". The blue-green represents things that can provide some kind of
cover. Green is the soldier start. Red is the alien start/UFO.

![Image:mansion_outline.png](mansion_outline.png "Image:mansion_outline.png")

We can see from this outline that the right and bottom of the map have a
lot of "cover density". There are many positions from which the player
can move and shoot behind cover. A smart player will be able to use the
environment in the bottom right to his advantage, while using a diverse
range of weapon skills -- long, medium and short distance. Long guns can
cover the short guns as they breach and clear buildings. What makes this
area so good is that there is a *mixture of exposed and unexposed
areas*. The player has different problems to solve and is rewarded for
understanding and employing multiple strategies.

## Player Movement

Now we can use this outline to get a sense of what options the player
faces for fire and movement within the map.

![Image:mansion_player_movement.png](mansion_player_movement.png "Image:mansion_player_movement.png")

This overhead scheme does not do a good job of representing the long
distances this map forces the player to move and fire across. While the
southeast of the map has a lot of shorter arrows, most of the map has
much longer distances which must either be crossed in the open or fired
across. As a result, much of the map is sniper's territory. But because
even our sniper rifles are not that accurate, much of the map will
become a frustrating sniper battle, shooting back and forth but hitting
little, as the aliens advance on the player across open space.

Having a long shot from time to time is not bad. A good sniper shot is a
satisfying thing. But it is a good idea to limit the effectiveness of a
long shot because the player will always be much better at taking
advantage of this than the AI. The player understands cover and how to
draw the AI in. That's why long shots should usually take place along
narrow channels where the player may see an alien or two, but should not
be able to catch most or all of the aliens in the map in his trap.

![Image:mansion_ideas.png](mansion_ideas.png "Image:mansion_ideas.png")

## Recommendations

The following image outlines the recommendations I would make. The
overall goal is to reduce the open space in the west and northwest of
the map, and reduce the potential for the map to revolve around one kind
of battle: the long shot.

Also, the map has pushed all of its most interesting elements to the
edges: the castle walls, the mansion and the poolhouse. By re-orienting
the map along a more north-south axis and putting in an extra wall in
the middle, many of these elements take on a more central role in the
map's tactical layout.

![Image:mansion_changes.png](mansion_changes.png "Image:mansion_changes.png")