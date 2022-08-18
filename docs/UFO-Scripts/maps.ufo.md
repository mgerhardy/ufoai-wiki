This page describes the map definition format. Every map should have one
to get included in the campaign and is selectable from the skirmish and
multiplayer menu.

## Terrain types

- desert
- arctic
- cold
- water
- mountain
- tropical
- grass

Also see [Terrain types](Mapping/Terrain_Types "wikilink")

## Culture types

- eastern
- western
- oriental
- african

Also see [Culture types](Mapping/Terrain_Types "wikilink")

## Population types

- urban
- suburban
- village
- rural
- nopopulation

Also see [Population types](Mapping/Terrain_Types "wikilink")

## General

If you create a terrain, culture or population block and leave it empty,
this means, that all the values match.

## Triggers

You can add special triggers for campaign related missions with:

- onwin
- onlose

### Trigger commands

- cp_add_researchable <tech-id>


"Add a tech as researchable"

- cp_add_item <item-id>


"Add an item as collected"

- cp_changehappiness <absolute-happiness-value>


"Function to raise or lower nation happiness."

- cp_endgame


"This command will end the current campaign"

## UFO types

- craft_ufo_scout, craft_crash_scout,
- craft_ufo_fighter, craft_crash_fighter,
- craft_ufo_gunboat, craft_crash_gunboat
- craft_ufo_harvester, craft_crash_harvester,
- craft_ufo_bomber, craft_crash_bomber
- craft_ufo_corrupter, craft_crash_corrupter
- craft_ufo_supply, craft_crash_supply

## Aircraft types for dropships

This is for skirmish only - in general your map should support every
dropship if you want to get it included into the game (or it should not
use any dropship)

- craft_drop_firebird
- craft_drop_herakles
- craft_drop_raptor

## Parameters

mapdef
This is the name that will be shown for the map in the single player
skirmish mode menu.

map
This is the name of the .bsp file, e.g "example". If the map is an RMA
it needs to be "+example".

description
Is used in the campaign to describe the location the mission takes place
in. The underline is used to mark this as translatable.

param
This is the name of the assambly that will be loaded from the \*.ump
file.

maxaliens
The maximum number of aliens to spawn on the map. Note this is not
necessarily the number of available spawnpoints. We can put a lot of
spawnpoints in the map and limit the number of aliens by the
**maxaliens** parameter, depending on the map size. Setting
**randomspawn** will distribute them to the spawnpoints at random. This
way we avoid spawning an army of aliens on a very small map, while still
keeping diversity.

Note: The number of aliens is still limited by the UFOs crew number.

singleplayer [V_BOOL](V_BOOL "wikilink")
Whether or not to use this map in single player games (like skirmish).
Default: true

multiplayer [V_BOOL](V_BOOL "wikilink")
Whether or not to use this map in multiplayer games. Default: false

campaign [V_BOOL](V_BOOL "wikilink")
Whether or not to use this map in the campaign. Default: true

## Example

`mapdef oilpipes_small`
`{`
`   map     "+industrial"`
`   param       "small"`
`   description "_Industrial theme."`
`   size        "small"`
`   teams       4`
`   multiplayer false`
`   maxaliens   6`
`   hurtaliens  false`

`   aircraft `
`   (`
`       craft_drop_firebird`
`       craft_drop_raptor`
`       craft_drop_herakles`
`   )`

`   ufos`
`   (`
`       craft_ufo_scout`
`       craft_ufo_fighter`
`   )`

`   terrains`
`   (`
`               // empty or missing block means "all"`
`   )`

`   cultures`
`   (`
`               "western"`
`   )`

`   populations`
`   (`
`       "village"`
`       "suburban"`
`       "urban"`
`   )`
`}`

[Category:Contribute](Category:Contribute "wikilink")
[Category:UFO-Scripts](Category:UFO-Scripts "wikilink")
[Category:Mapping](Category:Mapping "wikilink")