![](Entities_settings.jpg "Entities_settings.jpg")
![](Misc_mission_attributes.png "Misc_mission_attributes.png")

## General

- This defines a special mission target. The entity can spawn e.g. a
  particle (like smoke) to mark a landing zone that must be occupied to
  win the match.

## Keys

- **particle**: The particle to display.
- **item**: Item that must be placed here to trigger the target (e.g. a
  bomb that will blast the target entity, valid bombs are e.g. bomb1 and
  bomb2).
- **group:** Allows you to group mission entities - e.g. you have to
  occupy them all for x rounds to win the match.
- **target**: The target that is triggered once the round time was hit -
  target trigger must have targetname set.
- **message:** A message that is shown when the mission is completed.
- **targetname**: The name of this mission target.
- **desc:** The description of this mission target.
- **origin:** The position of this mission target.
- **spawnflags:** Level flags
- **radius**: If the entity has to be occupied this defines the radius
  that is needed. The value is given in world units. This means that one
  grid tile is 32 units.
- **team**: The id of the team this mission is for (1 = Phalanx, 7 =
  Aliens, 1-6 multiplayer teams)
- **time**: If set the entity has to be occupied x rounds to win the
  mission. In case of a bomb target this is the amount of rounds the
  bomb has to be laid down.

## Links

- [Entities](Mapping/Entities "wikilink")

[Category:Contribute](Category:Contribute "wikilink")
[Category:Mapping](Category:Mapping "wikilink")
[Category:Entity](Category:Entity "wikilink")