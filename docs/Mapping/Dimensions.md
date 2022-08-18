## Top view

![](Fields_top.jpg "Fields_top.jpg") Unlike in 3d shooters, you have to
take care of the fields which are used to position your actors in the
game and moving them around. The fields have a size of 32x32 in topview.
The actor is a bit smaller: 24x24. The walls of the house have to be
created such, that the actors can walk trough doors and such. Walls
should have a thickness of 4, to give the actor enough space. The orange
highlighted space shows the size of an actor.

8 units equals one foot. Each field is thus 4 feet, approximately 1.3
metres.

## Side view

![](Fields_side.jpg "Fields_side.jpg") From sideview one floor has a
height of 64 units. The ground floor goes from 0-64 the second from
64-128 and so on. The lowest 4 units of each floor are used for the
block the actors are standing on.

## Some other notes

Keep in mind, that the very lowest level has to be above the 0 for the
z-coordinate. Otherwise the pathfinding and collision detection can
become confused.

The order you place your spawnpoints is the order of the actors in your
dropship. This means the first soldier in your dropship spawns at the
first spawnpoint you placed. The second soldier in your dropship spawns
at the second spawnpoint you placed, and so on...

## Useful Sizes

- The maximum height a soldier can shoot over when crouched is 32 units.

## Links

[Mapping](Mapping "wikilink")

[Category:Mapping](Category:Mapping "wikilink")
[Category:Contribute](Category:Contribute "wikilink")