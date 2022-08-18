## Map testing

Map testing is a very important part in getting the maps usable.
UFORadiant is not rendering every detail - and there's always human
error factor. This article will try to help with in-game testing of maps
and reporting the problems. Of course, you should have latest
development version running - see [compilation
details](http://ufoai.ninex.info/wiki/index.php/Coding). You can check
the pathfinding data in UFORadiant now - to make this work you first
have to compile your map and then use the button in the toolbar to show
the pathfinding overlay.

You can either test and report new bugs found, or help with triage of
already reported bugs. See
[tracker](https://sourceforge.net/tracker/?group_id=157793&atid=805242) -
select "Status" to be "open" and "Category" - "Maps", then take some
reported bug and test it. Report your findings by commenting on the
original bug.

Of course, map bugs can be found during normal gameplay - but dedicated
testing usually will cover larger areas of the map and more maps, So
there must be a way to load any arbitrary map. To load a map, open the
game console with the / key above your *tabulator*-key (or to get the
console and to return to the normal GUI). You may do it in game or from
the main menu.

Type to get a list of valid maps. Start the map by typing

`map <day|night> [mapname]`

for a static map or

`map <day|night> +[mapname] [theme]`

for assembled maps.

Sometimes you will want to start a random map using specific tiles in
specific locations, so that you can test the exact same layout. This
will require specifying individual tiles and their positions (the
following example is broken in two lines, use single line when entering
a command).

`map <day|night> "-map/prefix +tile1 ... +tile `*`n`*`"`
` "tile1_xpos tile1_ypos tile1_zpos ... tile`*`n`*`_xpos tile`*`n`*`_ypos tile`*`n`*`_zpos"`

Given that there currently is no way to paste commands in game console,
typing such string can be very tedious. Fortunately, there's a
solution - you can create aliases, which later can be executed ingame
with a single command. To do this, you have at least 3 options:

1.  add it directly to file in yor game installation directory;
2.  edit to contain something like , then add in your UFO:AI profile
    directory (on Linux, something similar to , which contains the
    alies;
3.  add to your UFO:AI profile directory.

The alias itself would look like:

`alias testmap1 "map day \"-farm/f_ +drop_firebird\" \"16 0 0 -24 -32 0\""`

Note that you must start a new single player game, build a base, hire
and assign to the dropship a team of soldiers, otherwise the map will be
loaded without actors and you will not be able to test it properly. You
can also load a single player game.

The map will be loaded with the soldiers from your current game (those
selected on the first dropship in the first base) with their current
equipment. Aliens and civilians will be chosen from \[?\].

Some examples:

`map night tower`
`map day +oriental small`
`map day +oriental medium`
`map day "-b/ +aliencont +quarters" "0 0 0 8 8 0"`

## Hints and best practices

So, what and how should be tested? Before you start, it is desired to
have a debug build and [run the game in a
debugger](Debugging "wikilink") - that way you will be able to report
crashes as well.

There are a lot of things that can go wrong with a map. After loading
the map, look around it - check for incorrectly looking objects and
shadows, check for incorrect textures. Switch levels, check that objects
appear and disappear as expected. Walk around with soldiers, check that
both pathline and actual walking are as expected. Ideally one would try
to step on most tiles in a map, but remember that some problems show up
only when longer pathline is displayed. Hover the mouse cursor over the
tiles, select them as targets for walking - this also can expose
different problems. Try to step into various objects, try to walk in
unintended directions. In general, just try to break things :).

### General hints

- Test using latest trunk checkout of both code and maps.
- Enable confirmation in options - this way you will be able to see
  exactly where soldier intends to walk and we will see that in
  screenshots.
- Compile without lightmap if you only want to check the brushwork or
  the pathfinding, see the [map
  compiling](Mapping/Compile#Parameters "wikilink") article for more
  information.
- If the map is random assembly (map name starts with a **+**), game
  prints map definition to console - for example,

`"-village/vil_ +s02 +s03" "0 0 0 8 8 0"`

(this is not a valid definition). When reporting problems in such maps,
copy and paste this string to your report.

### Screenshots

- You can create in-game screenshots using key. Screenshots are created
  in directory.
- When creating screenshots, consider hiding HUD with key. You can get
  the HUD back by pressing .
- When creating screenshots, consider that somebody has to both
  understand what the problem is and where is it located on the map. Do
  not zoom in too much and do not zoom out too much.
- You can set screenshot format to PNG by executing . Remember that even
  though screenshots will have better quality, they will also be much
  bigger. Cut out the relevant parts and resave as JPG in Gimp for
  uploading to the tracker or sharing otherwise. This variable also
  supports TGA as a parameter.
- For one-time screenshot format change you can use syntax , where
  *format* is one of jpg, png or tga.
- You can also change JPG quality with the variable .
- You can set in-game variable to 0 - this way you will be able to take
  screenshots from more angles if required.

### Routing debug dumps

If the problem is related to pathfinding, it can help to have routing
information dumped to a file.
To obtain this information, load a map and execute and .
This will create csv files in the current directory. Note that these
files are fairly large, so you will want to compress them for adding to
bugreports.

### Testing helpers

#### Useful variables

- You can see nodraw brushes and other entities in-game by enabling
  variable.

- You can see actorclip brushes in-game by enabling variable - **removed
  in current trunk**.

- When testing maps, it is often not desired to have aliens and
  civilians - turn ending takes a long time and sometimes they even
  shoot at you. Setting ingame variable to 0 will prevent AI actors from
  appearing (note that you have to set this variable before loading a
  map).

- If for some reason you want to walk around a lot and maybe test
  func_breakable by shooting, you can load the map with AI actors (by
  setting to 1) and enable variable (). Note that this will only
  preserve TUs spent on walking.

- You can change camera tilting behaviour with variables:
  - \- sets lower angle at which camera can be tilted. Defaults to 35.
    Suggested value for map testing - 0.

  - \- changes camera rotation speed. Defaults to 250.

  - \- changes camera movement speed. Defaults to 750.

- Testing a lot of
  [func_breakables](Mapping/Entities/func_breakable "wikilink") in one
  go can be harder if aliens can hurt you (and you must have them if you
  want to be able to shoot more than once). Setting to 1 will prevent
  any damage to be dealt. Unset it when attempting to break
  [func_breakables](Mapping/Entities/func_breakable "wikilink"), set
  again before ending your turn.

- will render map in wireframe.

- will show some values, including brushcount. Note that this brushcount
  will differ a lot from you would see in
  [Radiant](Mapping "wikilink") - it takes into account brush splitting
  done by map compiling process (overlapping brushes, lighting related
  splits etc).

#### Pathfinding grid

Wilminator has implemented an overlay of the pathfinding grid. It draws
rectangles over tiles, depicting pathfinding related information using
colours and shape of those rectangles.

To enable this overlay, enter in the game console. Here's a screenshot
of the result:
[image:Pathfinding_overlay.jpg](image:Pathfinding_overlay.jpg "wikilink")

Colour explanation:

- **green** - this tile can be reached and entered by the actor based on
  remaining TUs;
- **yellow** - this tile can be entered by an actor, but the current
  actor does not have enough TUs to reach it this turn;
- **red** - this location cannot be reached;
- **black** - this location would have the actor fall more than one
  level and is not reachable;

The height of the box is the marker for the highest the adjacent cell
floor can be in order to enter the adjacent cell.

#### Pathfinding information in Radiant

Based on pathfinding grid for Game Client, a rendering overlay for
pathfinding was introduced into Radiant. It basically shows the same
data as the Game Client by loading the data from bsp file. The overlay
can be enabled by using the Tools\>Show Pathfinding menu entry. Level
filtering can be applied to these.

For each grid following details are rendered:

- a box showing accessibility state *and*
- arrows for adjacent grids connectivity (starting from current grid).

Colour explanation (both box and direction arrows):

- **green** - default standing/walking mode possible
- **yellow** - height restricts to crouching mode
- **red** - not accessible/connected (If grid is not accessible, arrows
  won't be drawn)

## Links

- [console commands](commands "wikilink")
- [console help](console "wikilink")
- [Pathing debug formats](Pathing_debug_formats "wikilink")

[Category:Mapping](Category:Mapping "wikilink")
[Category:Contribute](Category:Contribute "wikilink")