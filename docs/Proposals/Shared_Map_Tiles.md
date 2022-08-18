## Prelude

After [DarkRain](User:DarkRain "wikilink") implemented the feature
request it is now possible to use map extensions without restrictions.
In order to make an example for this, I prepared the +country map to
show what can be done and how.

## General Idea

Each of our RMA themes is supposed to support all dropships and all
UFOs. This is a total number of 17 required tiles per map theme, where
in a lot of cases the tiles are simply a copy of another one. This is
especially true for the dropships. Now the idea is, instead of having
each required tile in each theme, having them only once in a tile pool
that is shared between various maps. The shared tiles use a dummy
texture for the ground surface. Using the material system we can blend
the maps surface texture onto the dummy texture to fit the inherited
tile in. That said, the idea is NOT to force all maps using this.

## Advantages

I want to start with an example. If somebody finds the time to make a
fix or an improvement in the prefab of a dropship, he has to replace
this dropship in more than 30 map tiles in order to apply this to all
our maps. Implementing this proposal would save a huge amount of time
when it comes to maintaining our maps. Also, it would be much easier to
make changes, add missing tiles for existing UFO, new UFOs or dropships.
Beside that, reducing the number of duplicated map tiles should lower
the size of our installer by a reasonable amount.

## Problems

The problems I met so far are related to the blending of the surface
texture.

- Blending makes tile borders visible.

There are also some restrictions regarding the textures to use.

- The surface texture of the map has to have the same resolution and the
  same scaling as the dummy texture we use for the shared tiles.
- When blending the surface texture onto the dummy texture, this surface
  behaves different.
  - The material system parameters (bump, specular) are not applied to
    the blended texture.
  - The blended surface uses the material properties (sound,
    bouncefraction) of the dummy texture.

Furthermore.

- We need unified tile descriptors.
- A lot of unused tile definitions are parsed.

## Further Advantages

There are some thoughts what could possibly be done in the future.

- The rescue missions could be implemented into the RMA themes easily.
- By having different versions of a map (e.g. scout1, scout2 scout3) we
  could have more diversity by randomly choosing one of them for the
  map.
- As above, having various crashed versions (slightly damaged, damaged,
  nearly destroyed).

[Category:Proposals](Category:Proposals "wikilink")