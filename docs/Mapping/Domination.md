## General

Doing a domination map is quite easy. All you have to do is to place a
[misc_mission](Mapping/Entities/misc_mission "wikilink")
[entity](Mapping/Entities "wikilink") set the **time** and the
**radius** of the entity.

Setting a **team** to the
[misc_mission](Mapping/Entities/misc_mission "wikilink") entity will
only allow this team to do the mission.

The **time** value is given in rounds.

The **radius** value is given in world units. This means that one grid
tile is 32 units.

## Testing

Verify the radius property by setting the [cvar](Cvars "wikilink") to
**1**. This will enable the server side bounding box rendering.

[Category:Mapping](Category:Mapping "wikilink")
[Category:GameTypes](Category:GameTypes "wikilink")