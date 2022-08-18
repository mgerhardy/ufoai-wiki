## Map descriptor files

This is a proposal for descriptor files for maps. This proposal ties in
with the proposal for [the dynamic
campaign](Gameplay_Proposals/Campaign "wikilink"), and is also related
to the work done on [Terrain Types](Mapping/Terrain_Types "wikilink").

The goal is to render
[missions.ufo](https://ufoai.svn.sourceforge.net/svnroot/ufoai/ufoai/trunk/base/ufos/missions.ufo)
obsolete by combining the campaign mechanics, the terrain masks and
these map descriptors. Additionally, the goal is to facilitate the
multiplayer game setup.

## Format

Each map or mapset has associated with it one map descriptor. Ideally,
these descriptors should be stored in separate files, but it's also
possible to place them all in one file. The following is an example of
fields that could be in the descriptor:

    map farm
    {
      map      farm08 //The file that contains the bsp filename of the map. Can also be a .ump. Without extension and d or n char.
      description "_A farmhouse surrounded by fields and sheds. A UFO has landed in one of the fields." //A description for this map for use in setting up multiplayer.
      size        "medium" //A rough indication of the map size relative to the others. This information is useful when choosing a map in multiplayer.
      teams       2 //The amount of multiplayer teams on this map.
      music       PsymongN2 //The music to play for this map.
      deathmatch  true //For use in filtering maps by game type during multiplayer setup.
      assault     false //For use in filtering maps by game type during multiplayer setup.
      takeandhold true //For use in filtering maps by game type during multiplayer setup.

      terrains //Lists the terrain types that this map can appear on. If the map is not bound by terrain restrictions, put a single entry named "Any".
      {
        grass
        cold
        desert
      }

      cultures //Lists the cultural areas that this map can appear on. If the map is not bound by culture, put "Any".
      {
        western
      }

      population //Lists the population density areas that this map can appear on. If the map is not bound by population density, put "Any".
      {
        rural
        village
        suburban
        urban
      }
    }

Most of this is straightforward, but there are a couple of things to
note.
Firstly, note that this descriptor does not specify how many aliens
there are on this map, what types there are and what equipment they are
using. This information is provided by the campaign framework.
Secondly, note that this map has "desert" listed as a valid terrain.
However, since the cultures constraint disallows it to be placed in
Africa or the Middle-East (as they have culture types african and
oriental), that means the only deserts it can appear in are the ones in
North america, South America and Australia. However, it will only appear
on the edges of the Australian desert, as the center is unpopulated, and
this map requires at least some population.