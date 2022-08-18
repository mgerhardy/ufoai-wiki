This page will list generic problems regarding maps and large scale
development that affects mapping process.

## Generic map related problems

There are some problems that pose like map problems, but most likely are
bugs somewhere in code. Fixing such things per map is not possible.

- Actors entering actorclips

<http://sourceforge.net/tracker/index.php?func=detail&aid=1710034&group_id=157793&atid=805242>
Usually caused by func_breakable somewhere near.

- Out of sync server/client.

Sometimes confirmation path shows one line, actor moves in other, tile
can be selected as the target, but soldiers do not move there, soldiers
manage to walk into seemingly solid walls...
All of these problems have in common being unable to easily reproduce.
Some of the issues that most probably are caused by this :
<http://sourceforge.net/tracker/index.php?func=detail&aid=1829618&group_id=157793&atid=805242>
<http://sourceforge.net/tracker/index.php?func=detail&aid=1849539&group_id=157793&atid=805242>
<http://sourceforge.net/tracker/index.php?func=detail&aid=1864713&group_id=157793&atid=805242>

- Unpassable tiles without a reasonable explanation, at least so far -
  testcase at
  <http://sourceforge.net/tracker/index.php?func=detail&aid=1801104&group_id=157793&atid=805242>

## Map infrastructure improvements

There are also some larger proposed changes related to mapping :

- Reworked pathfinding

Not strictly mapping, but closely related, as this will fix a lot of
problems and also create a new ones.
Currently pathfinding does not take into account all brushes, so
additional actorclips are required, and there are other limitations.
More information at
<http://lists.cifrid.net/pipermail/ufoai/2008-March/000391.html>.


Initial merge to trunk committed in revision 19210.

- Edit-time or compile-time map part inclusion

Some objects have to appear on a lot of maps, and single change to such
object currently involves changing all of those maps individually. Such
objects include dropship and ufos. More information at
<http://lists.cifrid.net/pipermail/ufoai/2008-March/000392.html>.

- Setting **nodraw** flag for invisible faces

Brush faces that are not visible can be set **nodraw** - that improves
map performance. Doing that for all surfaces manually is a very tedious
work, especially for older maps that are cleaned up. The mapcompiler
recognizes cases where surfaces faces downwards and are not seen from
birdsview - they have set the faces to be **nodraw** automatically, but
there's more to gain by setting all the hidden faces to nodraw
automatically. This is being implemented - get [design
information](Proposals/MapUtils "wikilink").

[Category:Mapping](Category:Mapping "wikilink")