## Random map assembly algorithm

This algorithm was made by Gerd Heiße. Below is his description of how
it works:

Update: I committed some changes to the random map assembly code
recently. The new code does not check all possible tile placements
systematically, because this takes much too long - something I had to
learn ...

Such a systematically approach is only implemented for the mandatory
tiles, the other tiles are chosen by randomly testing some possible
tiles at random positions, calculating a rating value for each placement
and selecting the best one. This is done until the map is filled. If the
algorithm comes to a dead end, it falls back to the mandatory tiles and
start with the next possible placement of these tiles. The rating of a
placement is done in the following way:

- 0 points for an empty field
- 1 point for an filled (solid) field
- -N points for a field with connection information, where N is the
  number of adjacent tiles

The idea behind this is to prevent isles and holes in the map assembly
process and to prefer larger tiles in the beginning. I made good
experiences with this solution, but for some maps (i.e. village big) it
takes up to a minute in bad cases. From my point of view this algorithm
works better than the former one, but it is not a big problem to go back
to the other code if it leads to problems (only one file involved).

The current changes in code have some other consequences:

- The assembled maps are built from more larger tiles than before. So we
  should do some fine tuning in the ump files if there are too much
  tiles of one kind.
- The algorithm now uses bit logic for quicker connection tests. Because
  of this the possible connection characters are reduced to 31. The
  numbers 6...9 are not available anymore. The only valid characters are
  now: '+', '0' ... '5', 'a' ... 'z', 'A' ... 'Z'.

A note about the release: I think we should simply deactivate or comment
out the big village map and other maps which need more then a few
seconds for assembly. One possibility to achieve better assembly times
is to use larger tiles and more complete tile sets (i.e. the village
tile set has only two street corners from four possible).

## RMA2 algorithm

The above algo had a problem with certain random seeds on some maps
taking ages to assemble. This could not be fixed, because the RMA1 algo
was a 'by chance' approach. With a little luck, it worked nicely. But
sometimes with bad luck, it either seemed to hang or gave up explicitly.
So we needed a new algo and I ([Duke](User:Duke "wikilink")) invented a
new one in 2011.

As Gerd already pointed out above, a brute force approach is difficult
because on a typical UFO map there are fantastillions of ways to place
the tiles. Even contemporary computers can't check them all. They are
not even fast enough to sequentially search for the first working
solution to the puzzle. I decided to use a brute force approach anyway.
Plus some tricks. But first things first:

### Basics

A random map assembly is done in three stages:

- place the **fixed** tiles
- then the **required** tiles
- then pad the rest of the map with the **optional** tiles.

The RMA2 algo only deals with the 3rd part, the padding.

A stupid approach for the padding will look like this: for all positions
check all the available tiles if they fit there and pick one. If you
don't find one, remove your last placement and try the next option.
Repeat until the map is filled. Obviously this is best implemented by a
recursive function (at least I have not found a better way yet). The
size of the map limits the depth of the recursions and thus saves us
from stack overflows and such.

The RMA2 algo was 'designed to profiler'. I started with that stupid
brute force code, ran it in the profiler, looked where it spent the most
cpu and then thought about a way to reduce that.

### Trick \#1

With the plain stupid code the profiler showed that SV_FitTile()
consumed some 50% of the cpu. That function itself is not very
cpu-intensive, but an assembly of 'forest large' called it 823 million
times IIRC. So the 1st goal was to reduce the \# of calls to
SV_FitTile().

RMA2 starts with an incomplete map after the fixed and required tiles
have been placed somewhere. If a tile doesn't fit at a certain position,
it will also not fit there in any of the recursions. So we build an
array of the valid position/tiletype combinations. This is called
**posTileList**. In order to save a little space, those combinations are
encoded into a short value, further referred to as a **'tilecode**'.

While an 8x8 map with 20 tiletypes has 1280 calls to SV_FitTile(),
you'll usually find some 200-500 entries in posTileList for the same
map.

### Trick \#2

Recursing through the billions of ways that 400 entries can be placed
doesn't make sense if it's clear that a position will always be
uncovered no matter which combination we try. This thought lead to the
idea to look at the posTileList from a different point of view: the
**gapList**.

The gapList is an array of map size with a list of tilecodes for each
square that can cover this square. So while the posTileList holds our
potential moves, the gapList holds the potential results per square of
the map and the moves that provided that result.

So if we find an uncovered square in that list, we can immediately stop
recursing. That's a very important shortcut.

The second purpose of the gapList is that we will walk the tree not by
our potential moves (ie. posTileList), but by the most 'interesting'
gaps, see trick#4.

### Trick \#3

You can probably imagine a situation where two adjacent gaps a and b can
be covered by 2-3 tiles each, but placing the 2nd tile on gap a will
leave you with no tile for gap b. This result for gap b will repeat over
and over again (can be millions of times) while we recurse through the
options. So we can as well eliminate it right from the start. This is
done in **SV_GapListReduce()**. As this function is rather costly
cpu-wise, it is only called once before the recursions start.

### Trick \#4

If we now start to recurse through the remaining options, the recursions
will form a tree. The tree can be rather wide and not so deep or rather
narrow and pretty deep. The shape of the tree does matter. And we have
ways to influence the shape.

Unlike the RMA1 algo did or an A\* would do, RMA2 does not try to find a
working solution as quickly as possible. Instead, it achieves the same
goal by eliminating the non-working combinations as soon as possible.
That is, in large chunks of the tree.

If we have a gap that just one single tile can cover, we must place it
sooner or later. In that situation it would be foolish to start with a
gap that has a lot of options. So RMA2 always tries to find the gap with
the least options, thus narrowing the tree.

It's probably not too obvious from the above text, but this strategy is
the **core of the RMA2 algo** and what makes it really fast.

### Trick \#5

If a map has something like a winding brooke, a street or footpath on
it, ie. something that has to form a line, it's pretty obvious that the
algo could place some (required) houses and such in a way that no river
can flow through. Easy to see for a human, but it takes millions of
tries for the algo to figure out the impossibility.

So I created the **line tag**. It allows the mapper to mark the tile
types the line is composed of. As line tiles are very restrictive as far
as their neighbours are concerned, they are most likely to eliminate
many other options if placed. So if a line tag is present, RMA2 will
place the line tiles first, according to the strategy described in
trick#4.

### Room for improvement

1.  The placing of the required tiles still uses the RMA1 code.
2.  Selecting the gap with the least options could be done more
    efficiently.
3.  The SV_RemoveTile() function is not very efficient. It clears the
    map, then places all those n-1 tiles.

However, the current RMA2 code seems to be **fast enough**. On the
buildbot, it creates the assemblies for 50 seeds for each of our some 60
(?) maps in less than 2 minutes. That's an average of 40 ms per
assembly. There are still some seeds that take up to 17 secs, though.

## Recommendations for mappers

In the process of developing RMA2 I learned how amazingly different UFO
maps can be. And how amazingly many ways there are for an unaware mapper
to trick RMA2. So here are some rules for you:

1.  The number of entries in posTileList is crucial to the speed and
    memory consumption of the assembly of your map. The current limit is
    set to 1700. If your map hits that limit, you probably have a large
    map with many different small tiles. Your best bet is usually to use
    **tilesets**. But you can also add fixed tiles, required tiles (very
    carefully), reduce the map size or make bigger tiles (ie.
    'precombined').
2.  Don't make your brand new tile a required tile just because you want
    to see it on the map, especially if it is rather small. A small tile
    can easily block the placement of a big tile and it takes many
    attempts to find the right place for a small tile.
3.  If your map has something like a winding brooke, a street or
    footpath on it, ie. something that has to form a line, use the line
    tag to mark the tile types the line is composed of. This may or may
    not speed up the RMA2 process significantly, so use it with care.
4.  If your map is slow with some seeds, there is some code to visualize
    the incomplete map stages where RMA2 finds a dead end. They can give
    you an idea what is missing in the assembly. Unfortunately this
    feature is currently only available to coders.

## How to analyze RMA2 problems

As mentioned above, you can visualize RMA2 problems. You don't need to
be a great coder, you merely must be able to compile and edit the source
in a few places. Here is what to do:

- in change the to *"1"*.
- in change \#define SEED_TEST 0 to 1
- in function testNewSeedlists() change mapname, assembly and craft to
  the values you want to test
- you may want to change the 'i=0' in the for-loop to the seed you want
  to test
- compile
- configure your console window to keep the last 2-300 lines of output.
  On Windows, open cmd (command prompt), select properties -\> buffer
  height (or buffer size)
- run testall with the param --only-RandomMapAssemblyTests
- wait a couple of seconds (5-10), then press Ctrl-C.
- you will now hopefully recognize your map in the output. One map is
  printed for each dead end RMA2 encounters, along with a reason below
  the map. Reason codes are:
  - uncovered gap at x/y - none of the remaining tiles fits in a way it
    would cover the specified gap
  - couldn't pad - no combination of the required tiles could be padded
    with optional tiles
  - out of solids - the total number of solid squares in the remaining
    tiles is lower than the number of gaps
- repeat with a different number of seconds

## Todo

- change the remaining \#defines to cvars to allow mappers to test their
  assemblies without any compilation. --[Mattn](User:Mattn "wikilink")
  08:24, 22 December 2011 (CET)
- sv_rmadisplaythemap must not be changed in the code - that's why it's
  a cvar
- write some docs to explain to Duke how to pass a cvar to testall.exe.
  --[Duke](User:Duke "wikilink") 23:35, 25 December 2011 (CET)

  You can't set a cvar from the shell. Or what do you mean? Setting cvar
  on testcase? Anyway, you can ask if you need it.
  [Bayo](User:Bayo "wikilink") 11:17, 27 December 2011 (CET)

[Category:Mapping](Category:Mapping "wikilink")
[Category:Coding](Category:Coding "wikilink")