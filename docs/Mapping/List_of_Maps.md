***Work in progress.***

Page is being updated for version 2.3, be patient :-)

## How missions work

The key to understanding how maps work in the campaign is to look to
file. The file defines the maps which will be used in missions with
given parameters such as maximum amount of aliens or ability to play the
map in multiplayer. It also allows to define terrain, culture,
population, ufo or dropship parameters. Those will be used to select a
map during the game given the mission parameters.

There are two different types of maps, static and
[random](Mapping/Random_map_assembly "wikilink"). Also some maps are
marked as RMA, but contain only 2 types of tiles, dropship and rest of
the map.

## UFO and dropships tiles

Random maps should contain as much ufo tiles as it possible, and all
tiles for dropships. Current state of this work listed here:
[TODO/Mapping/Crafts Tiles](TODO/Mapping/Crafts_Tiles "wikilink").

## Pivot table

<table>
<thead>
<tr class="header">
<th><p>Map</p></th>
<th><p><a href="Mapping/Terrain_Types#Terrain_types"
title="wikilink">Terrain</a></p></th>
<th></th>
<th><p><a href="Mapping/Terrain_Types#Culture_types"
title="wikilink">Culture</a></p></th>
<th></th>
<th><p><a href="Mapping/Terrain_Types#Population_types"
title="wikilink">Population</a></p></th>
<th><p>Comment</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Random maps</p></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p><a href="TODO/Mapping/Crafts_Tiles#+africa"
title="wikilink">+africa</a> </p></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p><a href="TODO/Mapping/Crafts_Tiles#+beach"
title="wikilink">+beach</a> </p></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p><a href="TODO/Mapping/Crafts_Tiles#+bridge"
title="wikilink">+bridge</a> </p></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p><a href="TODO/Mapping/Crafts_Tiles#+cemetery"
title="wikilink">+cemetery</a> </p></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p><a href="TODO/Mapping/Crafts_Tiles#+country"
title="wikilink">+country</a> </p></td>
<td></td>
<td></td>
<td><p>Very old and bad-looking map, may be we should recreate it from
scratch.</p></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p><a href="TODO/Mapping/Crafts_Tiles#+desert"
title="wikilink">+desert</a> </p></td>
<td></td>
<td></td>
<td><p>not real RMA yet</p></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p><a href="TODO/Mapping/Crafts_Tiles#+farm"
title="wikilink">+farm</a> </p></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p><a href="TODO/Mapping/Crafts_Tiles#+forest"
title="wikilink">+forest</a> </p></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p><a href="TODO/Mapping/Crafts_Tiles#+frozen"
title="wikilink">+frozen</a> </p></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p><a href="TODO/Mapping/Crafts_Tiles#+hills"
title="wikilink">+hills</a> </p></td>
<td></td>
<td></td>
<td><p>Uses dummy texture to fit some more terrains. But currently
doesn`t have enough houses and terrain-specific tiles.</p></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p><a href="TODO/Mapping/Crafts_Tiles#+ice"
title="wikilink">+ice</a> </p></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p><a href="TODO/Mapping/Crafts_Tiles#+industrial"
title="wikilink">+industrial</a> </p></td>
<td></td>
<td></td>
<td><p>aka oilpipes_*</p></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p><a href="#+japan" title="wikilink">+japan</a> </p></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p><a href="TODO/Mapping/Crafts_Tiles#+oriental"
title="wikilink">+oriental</a> </p></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p><a href="TODO/Mapping/Crafts_Tiles#+tropic"
title="wikilink">+tropic</a> </p></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p><a href="TODO/Mapping/Crafts_Tiles#+ufocrash"
title="wikilink">+ufocrash</a> </p></td>
<td></td>
<td></td>
<td><p>special assembly.</p></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p><a href="TODO/Mapping/Crafts_Tiles#+village"
title="wikilink">+village</a> </p></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Map</p></td>
<td><p><a href="Mapping/Terrain_Types#Terrain_types"
title="wikilink">Terrain</a></p></td>
<td></td>
<td><p><a href="Mapping/Terrain_Types#Culture_types"
title="wikilink">Culture</a></p></td>
<td></td>
<td><p><a href="Mapping/Terrain_Types#Population_types"
title="wikilink">Population</a></p></td>
<td><p>Comment</p></td>
</tr>
<tr class="even">
<td><p>Semirandom maps</p></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p><a href="TODO/Mapping/Crafts_Tiles#+bridge"
title="wikilink">+bridge</a> </p></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p><a href="TODO/Mapping/Crafts_Tiles#+construction"
title="wikilink">+construction</a> </p></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p><a href="TODO/Mapping/Crafts_Tiles#+desert"
title="wikilink">+desert</a> </p></td>
<td></td>
<td></td>
<td><p>also known as "harvester_crash"</p></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p><a href="TODO/Mapping/Crafts_Tiles#+druglord"
title="wikilink">+druglord</a> </p></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p><a href="TODO/Mapping/Crafts_Tiles#+eaglenest"
title="wikilink">+eaglenest</a> </p></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p><a href="TODO/Mapping/Crafts_Tiles#+gasstation"
title="wikilink">+gasstation</a> </p></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p><a href="TODO/Mapping/Crafts_Tiles#+italy"
title="wikilink">+italy</a> </p></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p><a href="TODO/Mapping/Crafts_Tiles#+military_convoy"
title="wikilink">+military_convoy</a> </p></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p><a href="TODO/Mapping/Crafts_Tiles#+shelter"
title="wikilink">+shelter</a> </p></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p><a href="TODO/Mapping/Crafts_Tiles#+spedition"
title="wikilink">+spedition</a> </p></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Map</p></td>
<td><p><a href="Mapping/Terrain_Types#Terrain_types"
title="wikilink">Terrain</a></p></td>
<td></td>
<td><p><a href="Mapping/Terrain_Types#Culture_types"
title="wikilink">Culture</a></p></td>
<td></td>
<td><p><a href="Mapping/Terrain_Types#Population_types"
title="wikilink">Population</a></p></td>
<td><p>Comment</p></td>
</tr>
<tr class="even">
<td><p>Static maps</p></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p><a href="#bunker" title="wikilink">bunker</a> </p></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p><a href="#city_train" title="wikilink">city_train</a> </p></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p><a href="#corrupter_crash" title="wikilink">corrupter_crash</a>
</p></td>
<td></td>
<td></td>
<td><p>TODO: may be convert to +desert theme.</p></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p><a href="#dam" title="wikilink">dam</a> </p></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p><a href="#excavation" title="wikilink">excavation</a> </p></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p><a href="#farm" title="wikilink">farm</a> </p></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p><a href="#ferry" title="wikilink">ferry</a> </p></td>
<td></td>
<td></td>
<td><p>Terrain set as "water", is it ok?</p></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p><a href="#fighter_crash" title="wikilink">fighter_crash</a>
</p></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p><a href="#harbour" title="wikilink">harbour</a> </p></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p><a href="#mine" title="wikilink">mine</a> </p></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p><a href="#office" title="wikilink">office</a> </p></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p><a href="#oriental" title="wikilink">oriental</a> </p></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p><a href="#oriental_mosque" title="wikilink">oriental_mosque</a>
</p></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p><a href="#pipes_const" title="wikilink">pipes_const</a> </p></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p><a href="#resort" title="wikilink">resort</a> </p></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p><a href="#rivertown" title="wikilink">rivertown</a> </p></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p><a href="#scout_crash" title="wikilink">scout_crash</a> </p></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p><a href="#subway" title="wikilink">subway</a> </p></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p><a href="#village" title="wikilink">village</a> </p></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p><a href="#wilderness" title="wikilink">wilderness</a> </p></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Map</p></td>
<td><p><a href="Mapping/Terrain_Types#Terrain_types"
title="wikilink">Terrain</a></p></td>
<td></td>
<td><p><a href="Mapping/Terrain_Types#Culture_types"
title="wikilink">Culture</a></p></td>
<td></td>
<td><p><a href="Mapping/Terrain_Types#Population_types"
title="wikilink">Population</a></p></td>
<td><p>Comment</p></td>
</tr>
<tr class="even">
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

## Links

- [Mapping](Mapping "wikilink")
- [UFO-Scripts/campaign.ufo](UFO-Scripts/campaign.ufo "wikilink")

[Category:Contribute](Category:Contribute "wikilink")
[Category:Mapping](Category:Mapping "wikilink")