For random map generation, it is necessary to know the type of terrain,
culture and population density the mission takes place. This place lists
all different types that can occur.

The exact kind of terrain underlying a particular point on geoscape is
determined via usage of a colormask. Each color value marks a particular
type, listed below.

## Terrain types

`The mask for terrain types is defined in ``.`

|     |      |      |     |          |                                                                            |
|-----|------|------|-----|----------|----------------------------------------------------------------------------|
| RGB | 0,   | 0,   | 64  | water    | Crashed ufos will disappear                                                |
| RGB | 128, | 255, | 255 | arctic   | Rough ice-covered landscape; no vegetation; inhabitation impossible        |
| RGB | 255, | 128, | 0   | desert   | Rough sand regions; infrequent vegetation; inhabitation unlikely           |
| RGB | 255, | 0,   | 0   | mountain | Rough cliffy landscape; some vegetation; inhabitation unlikely             |
| RGB | 128, | 128, | 255 | tropical | Warm, moistly woods, maybe rivers; lots of vegetation; inhabitation likely |
| RGB | 128, | 255, | 0   | grass    | plane fields, some streets; good amount of vegetation; inhabitation likely |
| RGB | 128, | 0,   | 128 | wasted   | volcano, atomic test fields                                                |
| RGB | 0,   | 0,   | 255 | cold     | cold regions                                                               |

## Culture types

`The mask for culture types is defined in ``.`

|     |      |      |     |          |             |
|-----|------|------|-----|----------|-------------|
| RGB | 0,   | 0,   | 64  | water    |             |
| RGB | 128, | 255, | 255 | western  |             |
| RGB | 255, | 128, | 0   | eastern  |             |
| RGB | 255, | 0,   | 0   | oriental | bazaar like |
| RGB | 128, | 128, | 255 | african  |             |

## Population types

`The mask for population types is defined in ``.`

|     |      |      |     |              |                                                                             |
|-----|------|------|-----|--------------|-----------------------------------------------------------------------------|
| RGB | 0,   | 0,   | 64  | water        |                                                                             |
| RGB | 128, | 255, | 255 | urban        | sky scrapers, stadions, schools, massive buildings; inhabitation guaranteed |
| RGB | 255, | 128, | 0   | suburban     | wide streets, private homes, churches; inhabitation guaranteed              |
| RGB | 255, | 0,   | 0   | village      | small homes, narrow streets, old buildings; inhabitation guaranteed         |
| RGB | 128, | 128, | 255 | rural        | large farm houses, wide places, farms, inhabitation likely                  |
| RGB | 128, | 255, | 0   | nopopulation | no buildings, no inhabitation at all                                        |

## Nations

`The mask for nations is defined in ``.`

|     |      |      |     |         |                             |
|-----|------|------|-----|---------|-----------------------------|
| RGB | 0,   | 255, | 128 | latin   | The Revolutionary Countries |
| RGB | 0,   | 128, | 0   | states  | United America              |
| RGB | 0,   | 128, | 255 | europa  | The Greater European Union  |
| RGB | 128, | 128, | 0   | asia    | The Asian Republic          |
| RGB | 255, | 255, | 0   | middle  | The Middle-Eastern Alliance |
| RGB | 255, | 128, | 64  | africa  | New Africa                  |
| RGB | 128, | 0,   | 0   | russia  | Russia                      |
| RGB | 128, | 0,   | 128 | oceania | The Commonwealth of Oceania |

## Code example

The following code snippet shows the usage of the function
CP_GetRandomPosOnGeoscape. When preparing the linkedList_t for terrain
types (as example), you can add a string "Any" to indicate that the
terrain type does not matter and every terrain type is to be accepted as
suitable.

    /* initialization of terrain, culture, population types and nations */
    linkedList_t* terrainTypes = NULL;
    LIST_AddString(&terrainTypes,"cold");
    LIST_AddString(&terrainTypes,"grass");

    linkedList_t* cultureTypes = NULL;
    LIST_AddString(&cultureTypes,"Any");

    linkedList_t* populationTypes = NULL;
    LIST_AddString(&populationTypes,"rural");
    LIST_AddString(&populationTypes,"nopopulation");
    LIST_AddString(&populationTypes,"village");

    linkedList_t* nations = NULL;
    LIST_AddString(&nations,"Any");

    /* getting random point with given criteria */
    vec2_t randPos;
    if (CP_GetRandomPosOnGeoscape(randPos,terrainTypes, cultureTypes, populationTypes, nations)) {

        /* randPos has now a random value according to the given criteria */
        char* nationString = "none";
        if (MAP_GetNation(randPos))
            nationString = MAP_GetNation(randPos)->id;

        Com_Printf("Random position chosen is: x %.3f y %.3f (terrain: %s,
            culture: %s, population: %s, nation: %s) \n", randPos[0], randPos[1],
            MAP_GetTerrainTypeByPos(randPos), MAP_GetCultureTypeByPos(randPos),
            MAP_GetPopulationTypeByPos(randPos),nationString);
    } else {
        Com_Printf("No point fulfilling the given criteria could be found!");
    }

[Category:Mapping](Category:Mapping "wikilink")
[Category:Contribute](Category:Contribute "wikilink")