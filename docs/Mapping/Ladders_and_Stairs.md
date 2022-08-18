## Introduction

What follows is a technical description of how the pathfinding code
deals with stairs and other vertical obstacles. Most mappers will not
need to know the full details. If you want the player to go up stairs or
over other obstacles, it's a good rule of thumb to keep the vertical
change around 8 units (the height of an average stair). If you're using
a non-standard height or want to implement something other than normal
stairs, you may need to read the following.

## New Ladder and Stair Directions

With 2.3, a new tracing system is being implemented to provide better
realism in regards to solid surfaces. This change has brought about a
change in how stepup is handled.

## Stairs

### No More StepUp Brush

<img src="steps.png" title="steps.png" width="200" alt="steps.png" /><img src="microsteps.png" title="microsteps.png" width="200"
alt="microsteps.png" />There is no longer a STEPUP brush. As of 2.3, all
actors have an stepup of 8 model units. However, to compensate for
slopes and ladders or stairs with many steps between cells, a new
"microstep" tracing system has been added. If the difference in cell
heights between two cells exceeds 8 model units, the path traveled
between the cells is traced in 8 "microsteps". If none of these
microsteps exceed the actor's stepup, the actor is then allowed to
travel up the incline.

### Spacing permitted between steps

<img src="misstep.png" title="misstep.png" width="200"
alt="misstep.png" />Additionally, microstep tracing does not require the
slope to be consistent between cells, and even will allow for a couple
traces to be lower than the the previous without penalty. This number of
microsteps is marked by the PATHFINDING_MICROSTEP_SKIP define in
shared/defines.h. Currently, up to two microstep traces may miss a
platform that could be stood upon and an actor will be able to use the
step found on the third.

Note that the green bars mark the third trace, which must be to a
reasonable floor or the gap is too far and the actor can possibly fall.

### Maximum Actor Rise

<img src="quickstepup.png" title="quickstepup.png" width="200"
alt="quickstepup.png" />The new stepup system has one major limitation
and rule of thumb: An actor cannot rise or descend more than one cell
level per cell movement, even if the slope would allow. Coincidentally,
the current actor stepup \* the number of traces is 64, or one cell's
full height. However, the actor can be given a different stepup if
desired; the actor will not be able to rise or descend more than one
level per cell movement.

It does not look pretty, but it is functional. Refer to the actor clip
image below for ideas to make stairs look nice.

### Required Actor Bounds With Legroom

<img src="actorbounds.png" title="actorbounds.png" width="200"
alt="actorbounds.png" /><img src="actorbounds2.png" title="actorbounds2.png" width="200"
alt="actorbounds2.png" /> There is one more consideration: foot room. A
place for your actors to place their feet when they stand in a cell.
They stand on a 4x4 (model unit) square in the middle of their current
cell. But there's two requirements for the space to be valid: 1. The 4x4
space must not be obstructed up to PATHFINDING_MIN_STEPUP tall
(currently 8 model units) for actor leg room, and 2. The 22x22 wide
space on top of the above volume up to the ceiling for the actor's
torso, arms, and head. This unfortunately means that if we place our
steps too tall and too close together, the floor trace will not let us
stand on the spot because the actor's body does not fit. The three
choices are to increase MIN_STEPUP, increase WALL_SIZE (the thickness a
wall may enter a cell without causing it to become obstructed), or space
out the steps a bit. Currently, the magic ratio is (11-2)/8, or roughly
9 units horizontally per 8 units vertically (about 45 degrees).

Note the black step with the yellow bar. The yellow bar is inside the
actor's bounds box, so this cell can not be occupied by an actor. Shrink
the black step by one model unit, however, and that step is legal.

### Headroom Considerations

In order to walk upright from one cell to another, we need an opening
height of 44 mapunits (24 for crouching). In general, the opening height
is calculated as the delta between the higher floor and the lower
ceiling of the two cells. In a typical indoor stairway situation we take
the delta between the ceiling of the lower cell and the floor at the
border between the two cells.

Keep in mind that those measures are taken with a 4x4 trace. Moving the
whole staircase a tad sideways can sometimes have a large effect on the
heights measured.

## Ladders

## Links

[Mapping](Mapping "wikilink")

[Category:Mapping](Category:Mapping "wikilink")
[Category:Contribute](Category:Contribute "wikilink")