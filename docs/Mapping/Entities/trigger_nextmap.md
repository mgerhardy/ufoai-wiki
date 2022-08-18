![](Entities_settings.jpg "Entities_settings.jpg")

## General

- This trigger is activated once the mission goal is acchieved (all
  aliens are killed or the
  [misc_mission](Mapping/Entities/misc_mission "wikilink") entity goal
  is reached. You now have to move one soldier into the trigger zone to
  load a new map-part. With this trigger it is possible to tell stories
  over maps. E.g. several floor maps where you have to kill all aliens
  on one floor, go one floor down, collect a specific item, go one floor
  up (now with a different map set but the same layout) and use the
  collected item to finish a
  [misc_mission](Mapping/Entities/misc_mission "wikilink") entity.

Any entity on the given team that touches this (once activated) will
trigger the map change to the nextmap. The spawnflags define the levels
the spawned particle is visible on. Only used in singleplayer games.

## Keys

- nextmap


The map to start once this trigger is touched

- particle


The particle that indicates the activity of this trigger

- team


The team number that this trigger serves as a next map trigger

## Links

- [Entities](Mapping/Entities "wikilink")

[Category:Contribute](Category:Contribute "wikilink")
[Category:Mapping](Category:Mapping "wikilink")
[Category:Entity](Category:Entity "wikilink")