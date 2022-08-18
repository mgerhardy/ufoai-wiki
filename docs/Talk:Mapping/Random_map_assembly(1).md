## Map extentions

### Goals

There are two main goals I could think of.

1\. Extending an existing map theme would give the opportunity to use a
different material file. The initial idea was to use this for the downed
UFOs. Those look so bright and shiny right now - one could think they
are fresh out of the car wash. But furthermore a different material file
could even be used to give the theme a very different look by using the
material system.

2\. Dropship and UFO tiles are similar (even identical in some cases) in
a lot of maps. So using "blueprints" for these tiles would result in
less tiles to be maintained and a lowered size for the installer.

3\. Have \#1 and \#2 combined.

### Needs

For goal \#1 this seems easy. A "Child".ump would only extent his
parent. The child refers to the existing definitions and tiles in the
original map. This already works fine. But we cannot use the *drop* or
*ufo* cvar right now (see [bug
\#3446](https://sourceforge.net/p/ufoai/bugs/3446/)). This needs to be
solved.

A child of the +africa map would simply look like this. It refers to the
+africa map, reads the tile definitions from africa.ump and the map
files from the +africa map, but could use a different material file.

    // *********************************
    // Africa Crash
    // *********************************

    extends africa

    // map assemblies ---------------------------------------------------

    assembly medium_crash
    {
    size "10 8"
    title "_Africa"
    multiplayer africa/af_mp_team2
    africa/af_empty6        "0 30"
    ...
    tileset rock_a          "0 1"
    *rm_drop africa/af_craft_drop_firebird  "1 1"
    *rm_ufo africa/af_craft_ufo_harvester   "1 1"
    }

For \#2 we use the blueprint tiles for dropships and UFOs. Again, this
is expected to work once the issue about the cvar usage is solved.

    // *********************************
    // Africa
    // *********************************

    base africa/af_
    extends blueprint
    ...
    // map assemblies ---------------------------------------------------

    assembly medium
    {
    size "10 8"
    title "_Africa"
    multiplayer +mp_team2
    +empty6     "0 30"
    ...
    tileset rock_a      "0 1"
    *rm_drop blueprint/af_craft_drop_firebird   "1 1"
    *rm_ufo blueprint/af_craft_ufo_harvester    "1 1"
    }

Goal \#3 seems more difficult, because it means (taken from the above
examples) that \#1 refers to an .ump which again refers to another one,
bilding a chain which our current system seems unable to process.

## FAQ

### General

- What is the minimum size of a map ?


256x256

This is a tile of size 1

<!-- -->

    tile +s11
    {
    3 3

    0      c      0
    a      +c     a
    0      c      0
    }

- What assembly-theme is used when no parameter is given ?


a random one

- How can you specify the exact layout of a map, using parts ?


use a min of 1 and a max of 1

<!-- -->

    assembly recreational
    {
    size "6 6"
    [...]
    +s11 "1 1"
    [...]
    }

### Tilesets

- There is a cap at eight tiles per tileset, isn't it?
  [ShipIt](User:ShipIt "wikilink") 09:04, 11 April 2012 (SAST)


From looking at the code: yes there's a hardcoded limit of eight.
--[DarkRain](User:DarkRain "wikilink") 20:19, 11 April 2012 (SAST)

- Is it possible to use a tile more than one time in one tileset?
  [ShipIt](User:ShipIt "wikilink") 09:04, 11 April 2012 (SAST)


Didn't see any check in the code to avoid it, so I'd say yes it's
possible. --[DarkRain](User:DarkRain "wikilink") 20:19, 11 April 2012
(SAST)

- Also, what happens to the tiles within the tileset? If I have three
  tiles in a tileset, will they form a line, using the same conditions
  as the overall map? Is it some kind of 'map in a map'?
  [ShipIt](User:ShipIt "wikilink") 09:04, 11 April 2012 (SAST)


The algo will choose random tiles form the tileset.
--[DarkRain](User:DarkRain "wikilink") 20:19, 11 April 2012 (SAST)

## Proposed page layout

Below is what I propose to be the new layout for this page. I believe
this will make it easier to write a document which is easier to
understand and eventually makes clear how to use random map assembly.

### General

**TODO:** write the explanation of random map assembly is and what it's
scope (possibilities and limitations) are.

### ump-format

**TODO:** In plain English, write an outline of **ump** file sections (I
guess these include the **tiles** and **assemblies**). This should
include short descriptions of what each section means.

**TODO:** Write detailed explanations for each **ump** file section like
below:

#### tile section

Example:

    // a map comment

    base villaged/vil_

    tile +s01
    {
        4 5

        0  0  c 0
        0  a +c a
        0  a +a a
        b +b +a a
        0  a  a 0
    }

- **TODO:** explain what the text after "base" means
  - this is the base pathname for all tiles - if a tile has a `+` in its
    name, the name will be appended to the *base*
- **TODO:** explain what "s01" means
  - s01 is the tile name - e.g. the map with the filename  - must not be
    give, because all maps are searched in this directory - is the
    *base* (see above). So you only have to give the `+s01` to define a
    complete tilename. This is needed because some of the buffers are
    limited because they are send over the net (yes, you can play random
    maps over the network) - so the shorter the name, the better.
- **TODO:** explain what the first two numbers mean
  - this is the tile definition size - e.g. 4 cols, 5 rows
- **TODO:** explain what the matrix of numbers/characters mean
  - the outer numbers of this matrix are the needed tiles for the
    adjacent tiles - you can use letters from a-z to define different
    tile types
- **TODO:** explain the meaning of all valid characters/numbers
- **TODO:** explain what the '+' means in the matrix
- **TODO:** explain what a "demand-field" is

#### assembly section

Example:

    assembly residential
    {
        size "6 6"
        +s01 "1 2"
        +s02 "0 2"
        fix +s03 "0 2"
        +drop "1 1"
    }

- **TODO:** explain what residential means
  - residential is the theme name - you can define several themes in one
    ump file - e.g. you want some map where you must have an ufo - and
    another one where you don't want an ufo - define assemblies for this
    task
- **TODO:** explain what +s01 "1 2" does
  - +s01 is again the tilename (see above) - `"1 2"` means, that this
    tile must be at least 1 times in this map - but at the most 2 times
- **TODO:** explain what "size" means
  - size is the size of the assembly in game - in this case - 6x6 means
    1536x1536 (remember, one tile is at least 256x256 units in the
    mapeditor). A size of 6x6 would also lead to a square size (walkable
    actor squares) of 48x48 (because a unit has the size 32x32 in the
    mapeditor)
- **TODO:** explain what '+' means
  - extend the tilename with the **base** definition (see above)
- **TODO:** explain what "fix" means
- **TODO:** explain what "+drop" means

### ump in action

Full **example.ump** file:

    TODO: repeat all of the example sections here to show the _full_ .ump file

**TODO:** show how to play the .ump file in the game

**TODO:** show a ![Image:screenshot
jpg](screenshot_jpg "Image:screenshot jpg") of what this assembled map
looks like in-game