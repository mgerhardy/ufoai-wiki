Pathfinding is an important piece of gameplay that is taken for granted
until you try to make or edit a map. It is processed by a series of
functions to ultimately determine how in-game actors can or cannot move
on, around, or under objects in the map. This page is intended to do two
things- to document the process that is run to generate the pathfinding
data and to describe its impact on and how to work with it when map
editing.

## Step One - Floor and Ceiling Tracing

The first step in determining where an actor can move is to search for
horizontal surfaces that can be stood on, then determining if there is a
sufficient opening to accommodate the actor if it were to stand in that
surface. This trace is meant to be ran once for every size actor that
will be used in the game.

This is started by sending a 4 unit \* 4 unit (in model units) box trace
from the highest untraced part of the map down towards the base of the
model. This box is centered at the center point for an actor of a given
size, so a 2 cell \* 2 cell actor (UGV) will have the tracing box
centered in the corners of the four adjacent cells, where a 1 \* 1 actor
will trace through the center of each cell. If no cell is found, the
cells traced are considered "bottomless" and no actor may enter.

When a potential surface is found, another box trace is prepared. This
second trace starts at the found floor and extends up through the point
above the floor that is the minimum distance that any actor may step up.
(Step up refers to the maximum height that any given actor may "step up"
or increase its height when traveling from one cell to another before
the climb is too steep and is considered a wall, which currently is 20
units.) This test is to ensure that there is legroom for the actor to
stand. If any brush is found, this floor is considered unusable and this
whole step is restarted at a point beneath this found floor.

DISCUSSION ITEM: Should this legroom test be made wider? It currently is
not the same size as the actor's width to prevent unwanted brush
detections in irregular floors.

The third and final trace is from that minimum step up point to the top
of the model. The first suitable brush found that would obstruct an
actor from occupying the cell is marked as the ceiling. This ceiling
must be a minimum specified height above the floor that was found,
otherwise this process is repeated at a point beneath this found floor.

If the ceiling is acceptable, the cells that occupy the traces between
the floor and the ceiling are assigned both floor and ceiling values.
The values stored are relative to the base of the cell that the value is
for, and are recorded in "step up" units. One "step up" unit is 4 model
units. Any negative floor values indicate that the floor is at a point
below the base of the current cell and that an actor would likely fall
if that cell was entered. Any ceilings that are 16 or greater indicate
that the brush was found in a cell above the current cell.

If no ceiling is found, the top of the model is treated as an acceptable
ceiling, and the above applies.

If there are any cells that have a ceiling below them and a floor above
them and contain no usable floor brushes, the cell is marked as "solid"
by setting the ceiling value to 0.

## Step Two - Wall (Passage) Tracing

**Note:** This section is highly outdated due to a new commit. However,
a good discussion of what has changed can be found in [this SourceForge
tracker
article](https://sourceforge.net/tracker/?func=detail&atid=805244&aid=2489125&group_id=157793).
I will update this page to reflect those changes shortly.
--[Wilminator](User:Wilminator "wikilink") 06:00, 18 March 2009 (UTC)

The next step in pathfinding is to trace for walls. However, this is
done by looking for the openings (passages) between cells. Just like
floors and ceilings, the passages found can span multiple cells
vertically. This trace is also meant to be ran once for every size actor
that will be used in the game.

A couple of mathematical checks are made first to see if traces should
even be made. If the current cell or the destination cell cannot be
occupied, the whole test is skipped. The difference in height from the
original cell into the destination cell may not exceed the maximum step
up height, but the destination may be lower than the original cell.

DISCUSSION ITEM: I never separated out the minimum and maximum step up
heights. We can do that, but it could make map compile times slower and
maybe even buggier. Split them so we can have per-actor step up heights
or make that a fixed value in game?

The first trace ran checks the space between the maximum step up height
and the minimum opening size between the original cell and the
destination cell. A tracing box with the actor's x and y dimensions is
traced from the original cell to the destination at this height and must
be completely void of obstructions. If any obstruction is detected, then
there cannot be a passage here, and so this step is restarted in the
cell \*above\*.

A series of traces is then ran from the maximum step up height to the
higher of the two floors to look for the passage's lowest point. Next, a
series of traces is ran from the minimum opening height to the lower
ceiling. This difference is then calculated and stored as the size
opening available for an actor to move through into the destination
cell. If this opening extends into the cells above, the opening is
recorded as if the bottom of the opening only dropped to the bottom of
the current cell. If theory, we can now accommodate actors that are
taller than one cell, as well as making some openings that only allow
for crouching actors to pass through.

If no opening is available, a 0 is stored as the size of the opening.

## Step Three - Path Finding

Now that there is enough data collected that describes the terrain, we
can begin generating available paths from a place in the map. However,
before I write about the process used to figure out where an actor can
move, I want to talk about a few features taht can affect how an actor
can move through the map.

The first feature to discuss is the concept of crouching. This feature
allows an actor can now move while crouched and have the adjusted height
of the actor used to determine if a passage big enough exists for the
actor. The default pathfinding function will consider both the actors
standing and crouching heights when determining where an actor can move.
This allows for a path to be determined that will require an actor to
crouch in order to get to a desired location, and enables an actor to
crouch through an opening if it is the optimum path in terms of TUs
used.

A new feature that has been added is flying actors. In order for an
actor to be a flier, it must be able to fly and intend to fly. If the
actor cannot fly or does not want to, then gravity affects its
movements. To fly, one of two conditions must be met: the player must
have turned on the actor's ability to fly (which then allows the actor
to select airborne cells to move into) or a land-based destination is
selected that may only be reached if the actor were to fly. By default,
an actor will walk to the destination if possible as it will save TUs.

NOTE: The flying feature is partially written into the pathfinding code,
but is not in the user interface or built into the game. At this time it
is for reference only, and flying is turned off in the pathfinding code.

Another feature that has been added is the ladder feature. Brushes can
be marked as ladders and used to climb up and down through the map.
Actors that face the direction of the ladder brushes will not be
affected by gravity while they face the direction of the ladder brush.
If the actor climbs to the top of a ladder, the actor may stand and face
any direction, but may only climb down when facing the direction of the
ladder brush. There is the possibility of the actor using weapons while
on the ladder, but may not turn to face the target unless a ladder brush
would permit it.

NOTE: The ladder feature is written into the pathfinding code, but is
turned off. The ladder attribute for brushes needs to be defined, as
well as some additional housekeeping items for fully implementing
ladders.

Please note that when a move is recorded, both the TUs needed to get to
the cell, the direction moved to get into the cell, and the z coordinate
from the originating cell is recorded. Also remember that there is
different map data depending on the actor's size (not height) that was
generated in the last two steps.

When determining if an actor can move from one cell into another, the
first check is to ensure that we are not trying to see if a non-flying
actor is trying to fly. We also check to see that the actor is not
trying to fly while crouched. We then identify the TUs used to move in
this direction. NOTE: A move may also indicate a crouching toggle or a
fall.

Next, we check to see if we can stand from our crouch or move into a
crouch and check to see if it is the least TU expensive move. If so we
record the move. Either way, we are done if we we crouching or standing.

Next, if we are trying to fly, we only need to ensure that the direction
we are flying in can accommodate the size of our actor. If so, then we
check to ensure that this is the least TU expensive move, and record the
move if it is. If we were trying to fly, we are now done.

If the actor is trying to walk, we also ensure that the passage is big
enough for the actor to pass through. Additionally, we check to ensure
that the heights of the floors do not differ too much. If the change in
floor height is within the actor's step up height, then the actor is
allowed to enter the cell. Also, if the actor needs to rise or sink one
cell to stay on the ground and the floors are within this height, then
the actor is adjusted vertically, too. (Think stairs.) However, if the
actor would drop more then his step up height but less than the maximum
falling height, The actor is allowed to enter the cell to begin a fall.
Remember that if this is the least TU expensive move that the move is
recorded.

There is a move for falling. If the actor can fall, this move will be
allowed and the actor will then be able to fall one cell. Again, if this
is the least TU expensive way to arrive in this cell, it will be
recorded.

Additionally, there are checks for climbing up and down ladders. This
code is disabled until we fully implement ladders.

After the main pathfinding function is called, the TUs needed to move or
crouch into any location on the map, if possible, is available in a
table. There is a pending request for an A\* function to be written to
only generate a path, if possible, between two points. This will be
developed later.

## Step Four - Moving

When actually moving, the data recorded in the table is used to develop
the actual path traveled by an actor between two points. However, this
data is stored inverted- it documents where an actor \*came from\* to
get to the destination, and not where the actor \*goes to\* to get to
the destination. This is fixed by starting at the destination in the
table and "moving" backwards toward the starting cell. As we go, we also
swap out the z coordinate data of the source for the z coordinate data
for the destination, as an actor walking up or down stairs needs to stay
on top of the model as it slopes into a higher or lower cell. Now at
this point, we have the data needed to move from the starting cell to
our destination.

[Category:Mapping](Category:Mapping "wikilink")
[Category:Contribute](Category:Contribute "wikilink")
[Category:Coding](Category:Coding "wikilink")