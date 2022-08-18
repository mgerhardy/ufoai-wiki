This page is work in progress. I will collect conceptual information
from wilminator's emails here. --[Duke](User:Duke "wikilink") 16:07, 29
September 2009 (UTC)

This is far from perfectly accurate, but it should be enough for you to
know what the data represents, especially if you look through the
tracing functions based on how I describe the tracing algorithm.

## Trees

It is important to know a) what the tree is, and b) how it is actually
constructed. I know there is a rendering benefit to the tree, but I
still don't grasp that, and I've known about this algorithm for over 15
years now...

The tree itself describes divisions in space. Take a 3D volume, create a
plane, and split the volume in two. Repeat the splitting in each child
volume until you have a small amount of brushes. There is usually only
one brush, but it can be more; it can also be zero brushes. The dividing
plane itself is contained in a node, which has a pointer to the plane
that divides the area that the node represents. If there is not a
dividing plane, that node is called a leaf and there are no children. A
node branches; a leaf is a dead end. All brushes are contained in leafs.
The BSP nodes are stored in BspNodes (either cBspNodes or dBspNodes),
but optimized copies for tracing are stored in tnodes.

From a line tracing perspective, this then becomes very easy to use to
detect an intersection with a brush. In a node, determine if a line is
on only one side of the dividing plane, or both. If it is only on one
side, we repeat the test on the whole line on that one side. If it is on
both, we split the line at the point where it intersects that plane,
then repeat the call on each line segment in their respective volumes.
When we reach a leaf, then we know exactly which brushes to test for
line intersection. Sure beats trying to test every single brush every
time. ;)

Line tracing is a special case of box tracing. With box tracing, we
define extents- the distances around a line that can be intersected- and
calculate these offsets into the above process. In line tracing, this
offset is 0.

When id developed their bsp tree structure, they broke up the brushes by
the level flags they are marked with. If all brushes are tagged with the
level they belong to, then each thead contains all the brushes at that
one level. Then by using the levelmask value, you can prevent the
tracing of levels that the trace obviously does not intersect. However,
we do not take this into account AFAIK, so we always pass 0xFF or 0x1FF.

The line is technically evaluated sequentially from origin to target.
The tracing algorithm uses the BSP tree to find a line splitting point,
if any, and recursively calls the line segment closest to the origin
first. So for tracing, the BSP tree picks the splitting points, but the
BSP tree does not pick the order the leaves (and brushes) are checked
in.

Now, there can be no brushes in a leaf because the whole BSP tree
contains ALL brushes, including the ones we do not want to detect while
tracing. So when the thead and chead trees are created by
TR_MakeTracingNode, only qualifying brushes (ones that have any content
listed in MASK_IMPASSABLE and have no content listed in MASK_PASSABLE)
get added to the leaf. But a node was created in the parent pointing to
this leaf, so we end up with a stump- a leaf with no brushes. A good
example of this is a painting that is marked CONTENT_PASSABLE so an
actor can walk into the same cell: That brush exists in the BSPnodes,
but the brush will be missing in the thead tree. And the way the BSP
creation algorithm works, every brush that has no intersection with
another brush (edges can touch, but surfaces cannot pass through each
other) will be in its own leaf.

## Levels

cheads are pre-calculated bsp trees that only contain the leafs from the
thead trees that match the criteria in TR_MakeTracingNode. Currently
this looks for brushes that have MASK_IMPASSABLE but not
CONTENTS_PASSABLE. This speeds up the line tracing functions, but
complicates the ACTORCLIPS and WEAPONCLIPS.

Now, levels. 0-255(0xff) reflect the selection of the level flags in a
brush. Take the selected level flags of a brush, where level 1 is the 0
bit, level 2 is the 1 bit, etc. to create an 8 bit value- this is the
level value of the brush, and also the thead bsp tree that the brush
should be found in. 256 is the actorclip level (0x100) and 257 is the
weapon clip (0x101). The original problem was that the line trace would
originally go through ALL levels per trace, so I added the
TL_FLAG_ACTORCLIP and TL_FLAG_WEAPONCLIP to try and allow us to
selectively use or not use the CLIP levels but still be able to select a
separate mask for the other levels. This specifically was meant to allow
us to trace a line for a bullet to travel, as well as an actor. Without
the flag, all bullets and actors stop at any CLIP.

The box tracing functions for pathing are wrappers for each other.
TR_BoxTrace traces through selected levels of a tile,
TR_CompleteBoxTrace calls TR_BoxTrace for every time in a RMA, and
CM_EntCompleteBoxTrace calls TR_CompleteBoxTrace for the RMA then calls
TR_HintedTransformedBoxTrace for the func_doors and func_breakables. The
pathing code is set to use TR_SingleBoxTrace for ufo2map and
CM_EntCompleteBoxTrace for ufo.

Oh, the TR_\*DM functions and CM_\*DM functions return the location of
the trace intersection with a brush, where the corresponding function
without the DM just returns qtrue or qfalse based on if the line hits a
brush.

## Tracing

There are two different types of traces: LineTrace and BoxTrace. The
main difference is that the BoxTrace can examine the leafnodes for their
contents while the LineTrace can't. For LineTraces the tnodes are
filtered at the time the tree is built. The cnodes for Boxtraces contain
all the brushes, so the filtering is done while tracing. That makes
LineTraces fast and BoxTraces relatively slow.

So a LineTrace only knows about blocking or non-blocking leaves. But
there is one exception: clips. Brushes are assigned to levels 1-8
(technically it's 0-255). Clips (ie. actor-, weapon- and lightclips) are
assigned to special levels (256-258). See above. By passing the
'levelmask' we can tell the LineTrace which of the special levels to
look at.

The LineTrace is used for visibility and shooting while BoxTraces are
used for routing/pathfinding. One might expect that visibility and
lighting are the same, but that is not the case. The lighting is done in
ufo2map, which builds a special bsp tree that is discarded later on and
not passed to ufo.exe.

NOTABENE: This is about the design. The implementation in UFO:AI differs
slightly :(. Some parts of the code use PointTraces (ie.BoxTraces with a
zero-extents box).

[Category:Coding](Category:Coding "wikilink")
[Category:Contribute](Category:Contribute "wikilink")
[Category:Coding](Category:Coding "wikilink")
[Category:Contribute](Category:Contribute "wikilink")