## Larger Bases

This proposal presents a concrete description of an extension to the
building space of PHALANX bases.

## Purpose

The reason why bases need more building space is that there are too many
facilities that need to be placed by default. The point to the base
building part of the game is to allow the player to build customized
bases that suit his needs and playing style. Hovever, because there are
relatively many "overhead" buildings (buildings that must be placed in
order to support end functionality of the base), there is very, very
little space for custom building in practice.

To illustrate, consider a new PHALANX base with the maximum amount of
invalid tiles (4) that is going to be geared for heavy construction of
weapons and craft. To even get the base operational, it needs the
following:

- An entrance
- A power plant
- A radar facility (the radar facility is so standard that it can safely
  be considered a base necessity)
- A living quarters housing a few soldiers (if the soldiers weren't
  there the base would instantly succumb to an alien attack)
- A storage facility
- An antimatter storage facility (antimatter is a basic necessity for
  many things in the game, and certainly for production)
- A command centre

The above list comes down to 7 tiles. With the blocked tiles, that means
11 tiles are already taken. And remember, this base doesn't even do
anything yet! It's not even particularly geared up for any specific
role. All bases will typically have these buildings. Now we go about
adding the production lines:

- A large hangar, to allow construction of all PHALANX craft
- At least three workshops (less than three would be laughably few for a
  base that is supposed to be dedicated to production)
- An extra living quarters to house enough workers
- An extra storage facility to handle the item throughput

Now the base has 23 out of 25 tiles filled up. A whopping 2 are still
available (even with the minimum amount of blocked tiles this would only
be 5, which is still not much). And what can this base do? Produce items
at a fairly high rate. It can NOT do such things as disassemble UFOs or
send out craft on missions or interceptions. All its resources have to
be imported. And I'm not even mentioning facilities like base defences
and soldier support.

I think this example makes it clear the 5x5 grid is too small, even for
specialized bases.

## Solution

An obvious solution to the space problem is to increase the base grid
from 5x5 to something larger, like 6x6. However, this is not practical.
The most important reason is that the larger the grid, the more brushes
are going to be displayed on the same level at the same time. Because of
hardware limitations (more precisely, limitations of the hardware we
want to support) as well as limitations in the Quake 2 engine, this is
unacceptable.

Another solution is to cut on base facilities. If less facilites are
needed for the same base functionality, the grid space restriction will
be felt much less strongly. Obviously, this solution is very
unattractive. It would mean removing things from the game that we
already have, such as graphics, map tiles and UFOpaedia texts.

A third solution, and this is the solution I propose in this article, is
to add another level of buildings to the bases. The random map assembly
code allows for this, and because brushes can be optimized away on
different view levels the engine restrictions are avoided.

## Grid sizes and building placement

I propose the base grid to be arranged as follows. The "top" level of
the base will have a 3x4 grid. Two tiles are already taken by the
entrance, so the amount of free space is 10 tiles. The entrance takes up
2 tiles because it not only connects the surface with the top level, it
also connects the top level with the bottom level. The bottom level will
be the 5x5 grid we have now, but again 2 tiles will be taken up by the
entrance, making for a total of 19-22 free tiles. The bottom level is
the only level where blocked tiles can occur, for simplicity.

Buildings that require surface level access can only be placed on the
top level. These buildings are hangars and base defence facilities. No
hangars or base defence facilities may be placed on the bottom level.
All other facilities may be placed on both levels.

In all, the two-level base will have 29-32 free tiles, which is a real
improvement over the current 20-23 (for reference, a 6x6 grid would
offer 31-34 free tiles). If the entrance on the bottom level is made to
be only one tile, then we get 30-33 free tiles.

[Category:Proposals](Category:Proposals "wikilink")