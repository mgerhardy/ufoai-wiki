## General

The **ump** files can be loaded via

    map <day|night> +[ump-filename] [theme]

They have to be in the (see [directory tree](directory_tree "wikilink"))
folder

## ump-format

### Worldspawn

Often you want shared worldspawn settings for a theme. For this you can
define the worldspawn settings in the ump file.

    worldspawn {
        "key" "value"
        "key2" "value2"
        [...]
    }

See [worldspawn](Mapping/Entities/Worldspawn "wikilink") entity article
for more details on the keys/values.

If you want to use this feature, there is a contract in terms of ump
filename and ump directory structure. E.g. if you compile a map in the
ump filename must be . The directory part will be taken in ufo2map to
identify the related ump file.

### Tiles

Each tile that is to be used in random map assembly must have a tile
definition created.

Here is the example I'll use for my explanations:

    // *********************************
    // MIDDLE EUROPEAN VILLAGE
    // *********************************

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

This describes one tile for the middle european village structure, a
streetcorner running from north to west.

The comments are in C-style as `//` and `/* comment */`

**extends**: You can inherit tiles from other themes by extending an
existing ump file. You can only reference those tiles with the full
name, because the base may differ between the ump files. Only one level
of inheritance is supported.

**base**: This part only gives the base string where all the other tiles
are appended to tile +\[some tile name\]: The + means that the base part
from above is to be included here. For this example, the file in
question would be found in \base\maps\villaged\vil_s01.

**4 5** defines the area of the tile with an extra border. In the case
above, the tile is actually only 4 tiles total in size (the + fields),
but it requires 2x3 worth of space to define it. The border defines
which tiles can be next to your solid (again the + fields) tiles.

Basically, **4 5** part defines the size of the following matrix. Note
that you should always enclose all your existing map tiles with
"requirement" fields (without **+** mark).

The next part gives information about how to assemble the map. Our
example tile is a L-shaped street.

The fields with a **+** as first char tell us that there is really
something that was mapped - in our case a street. Load the map in
[UFORadiant](Mapping "wikilink") and examine the map, also noting where
the zero-point in coordinate plane is (lower left corner of the lower
left tile). The grid in the script above makes more sense if you open
the map up and block out the 256x256 'tiles' that exist on the map. If
you're not sure what is meant by map tiles, please go
[here](Mapping/Random_map_parts "wikilink").

The letters are used to indicate the type of tile:

`   * a: placeholder for all types of tiles (generic tile)`
`   * b: street horizontal`
`   * c: street vertical`
`   * 0: no requirements to the tile`

These indicator codes are built on a per file basis. The letter **b**,
in another , could mean something completely different. The fields that
don't have a **+** on them means that for this map to be included, that
tile type must exist in that position neighbouring it. Think about it
like a puzzle.

Fields with **+** denote fields that the tile we are currently defining
actually has. Fields without **+** denote the space around the current
tile. The tile definition is a 2D matrix of our tile and it's
surroundings. The character is defined in tile definition - so, **+c**
in a location means that the specific area gets assigned letter **c**
and that is the letter other tiles can refer to.

These chars can be a single **a**, **b** or **c** or, for example,
**ab** to define an combination of allowed tiles.

For an example, the third line down is **b +b +a a**. This means there
**must** be a 'street horizontal' from another tile to the left, there
**exists** a 'street horizontal' at the second position, there
**exists** a 'generic tile' in the third position, and there **must** be
a 'generic tile' in the fourth position. This expands horizontally and
vertically.

The generic tile is the most common here, the **a** tile. Our generic
tile-definition is a tile from the village - it could be houses, parks,
anything not a street according to the current definitions.

As described, there may be more than one char in a grid position - lets
look at a little 1x1 curve.

In the example **+bc** means that the tile properties for horizontal and
vertical are existing in the built tile.

Notice how the c is only above, and the b only to the left, of the
'real' tile. This will ensure that we only get our vertical street from
above and our horizontal street from the left. The two **a**'s will make
sure we don't get a horizontal or vertical from the right or below,
where the curve doesn't actually connect.

    tile +s05
    {
        3 3

        0 c 0
        b +bc a
        0 a 0
    }

There may be also more than one char in the demand-field (the
surrounding indicators).

    tile +r01
    {
        4 4

        0  ab ab 0
        ac +a +a ac
        ac +a +a ac
        0  ab ab 0
    }

Only one demand must be fulfilled. In the example of tile **r01** there
may be horizontal street above or/and below or a gap-filler (e.g. a
playground), therefore ab is used. The **ac** makes sure only vertical
streets and generic tiles are to the left and right.

If you want a particular tile to always appear at the edge of a map, use
a symbol that is not supplied anywhere (for example, use "z", but don't
define any tile as "+z").

### Assembly

Each random map definition file must have at least one assembly. If the
file has several assemblies and none is specified when the map is
loaded, one of the existing assemblies is chosen randomly.

    assembly residential
    {
        size "6 6"
        grid "2 2"
        +s01 "1 2"
        +s02 "0 2"
        [..]
        +drop "1 1"
    }

To start a map you can type `map +villagen residential`. The
**residential** parameter will chose a **residential** assembly-theme
from the **ump-file**.

Now lets talk about the format. As you see in the above example for
**assembly residential** you can define which size the map theme should
have. This is done with the parameter **size**
([V_POS](V_POS "wikilink") - 2 dimensional vector for x and y).

Size parameter specifies the grid size of the assembled, final map
without "requirement" fields specified before. For example, if you had
two tiles, each with size "4 4", putting them together would require
size of "2 4" (or "4 2", depending on orientation).

    tile +h01
    {
        4 4

        0  a  a 0
        a +a +a a
        a +a +a a
        0  a  a 0
    }

    assembly double
    {
        size "2 4"
        +h01 "2 2"
    }

Notice how tile definition has size "4 4", but actual tile is only 2x2,
thus allowing only two possible rectangle formations, one of whom is
used in the assembly - "2 4".

You can also specify a **grid** parameter ([V_POS](V_POS "wikilink")) to
optimize the assemby as long as all your tiles have the same size or are
multiples of it.

After this parameter all available tiles can be listed with a min and
max value for their amount of appearance (min and max).

You can also place tiles via the **fix** parameter:

    assembly this_has_a_fixed_tile
    {
        size "5 5"
        fix +s01 "2 2"
        +s02 "1 2"
    }

The numbers in "" behind the fix parameter show you the position
(x-y-Coordinate) of your tile in the mapgrid. With its origin "0 0" in
the bottom left corner of the map.

You can also replace fixed tileids with cvars

    assembly this_has_a_cvar_tile
    {
        size "5 5"
        [..]
        *this_is_the_cvar_name this_is_the_default_value "1 1"
    }

Now the assembly function will use the value of as tile id - if no value
is given via this cvar - the default value **this_is_the_default_value**
will be used. The min and max values are the same as for the other tile
ids. It's a naming convention to start these cvar names with the prefix
**rm_** (as in **r**andom **m**ap) - e.g. .

Of note, you need to include enough smaller tile maps to fill in holes
left if the bigger ones are used. If you build a 3x2 map, and the L
shaped tile map from the first example is used, you'd need a 2x1, or 2
1x1, maps to fill in the hole.

Multiplayer only maps can be defined, too. Just add a line like:

    assembly this_has_a_multiplayer_only_tile
    {
        [..]
        multiplayer +s02
    }

to your assembly.

### Tilesets

You can define tilesets to define a set of tiles that should be used in
the same was as you would define to be used tiles in an assembly - just
not a tile id, but a tileset id. The format would be:

    tileset mytileset
    {
        [...]
        +mytile1
        +mytile2
        +mytile3
    }

    assembly uses_a_tileset
    {
        [..]
        tileset mytileset "0 1"
    }

## Missions with map assembly

You can define your missions that should be generated with the random
map assembly algorithm in the [maps
definition](UFO-Scripts/maps.ufo "wikilink") script file.

## Available themes/assemblies

- [africa](Mapping/africa "wikilink")
- [cemetery](Mapping/cemetery "wikilink")
- [city_disco](Mapping/city_disco "wikilink")
- [country](Mapping/country "wikilink")
- [desert](Mapping/desert "wikilink")
- [farm](Mapping/farm "wikilink")
- [forest](Mapping/forest "wikilink")
- [frozen](Mapping/frozen "wikilink")
- [ice](Mapping/ice "wikilink")
- [industrial](Mapping/industrial "wikilink")
- [oriental](Mapping/oriental "wikilink")
- [tropic](Mapping/tropic "wikilink")
- [ufocrash](Mapping/ufocrash "wikilink")
- [village](Mapping/village "wikilink")


also see [Mapping/List of Maps](Mapping/List_of_Maps "wikilink")

## Links

- [RMA Algorithm](Mapping/Random_map_assembly/Algorithm "wikilink") By
  Gerd Heiße
- [Map assembly
  themes](Mapping/List_of_Maps#Mapassembly_Themes "wikilink")
- [Random map parts tutorials](Mapping:Random_map_parts "wikilink")
- [Mapping](Mapping "wikilink")

[Category:Mapping](Category:Mapping "wikilink")
[Category:Contribute](Category:Contribute "wikilink")