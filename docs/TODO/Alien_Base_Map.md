## Alien Base Map

This article describes some of the features that are desired in the
alien base map.

### Lighting

Ambient lighting in the alien base should be rather dark, but individual
tiles can have a decent amount of local lights to make the map visible.
Some leftover dark corners would be preferred.

### Architecture

The base tiles should ideally follow nonstandard designs, moving away
from cubical rooms and right-angle walls to make it more alien-looking.
However, the overall style should not be too different from the style
used in UFO designs. So preferably no round doors or curved walls.

### Tileset specification

There are two types of tile: room and corridor. Room tiles can be any
size, but should have at least some entrances. Not all walls need have
entrances, though all rooms should always be connected. Corridor tiles
are simple connecting tiles with no frills, although it would be nice if
they were creatively designed to block line of sight.

Here is a list of possible rooms for the tileset:

- Entrance (starting tile for PHALANX, exactly one required on each map)

- Wormhole chamber (target tile, exactly one required on each map)

- Hangar (at least one required on each map)

- Research lab

- Storage chamber

- Incubation chamber

- Antimatter containment (exactly one required on each map)

- Telemetry

- Power core (exactly one required on each map)

- Nutrition plant

The "ground" floor of most tiles should be at the third floor (z
coordinate 128). This is because some bigger room tiles, such as the
hangar and the wormhole chamber, will have their floors lower than most
other tiles, creating a "pit" effect.

[Category:TODO](Category:TODO "wikilink")