## Structure

A .map file is composed of a number of entities which contain brushes
(defining geometry) and attributes (key-value pairs). Most brushes are
usually found in the first "worldspawn" entity and "func_group"
entities. Common brushless entities include models, lights, actor spawns
and particles. Map files created using UFORadiant 1.5 have no
indentation.

    // entity 0
    {
    "classname" "worldspawn"
    // brush 0
    {
    face_0
    ...
    }
    // brush 1
    {
    }
    }
    // entity 1
    {
    "classname" "some_other_entity"
    "another_key" "another_value"
    }

## Brushes

Each brush consists of a number of faces, and a face is a "directed"
plane (half-space) and texturing info. Plane is given by listing its 3
points, if these appear clockwise when viewed from a point in space,
then the point is outside of the face. The polyhedron defined by a brush
is an intersection of its half-spaces or you may say that a point is
inside the brush if it's inside all its faces.

    ( x0 y0 z0 ) ( x1 y1 z1 ) ( x2 y2 z2 ) tex x_off y_off angle x_scale y_scale cont_flags surf_flags surf_value

- (x0, y0, z0) ... Points coordinates are usually integers, but can
  sometimes be real.
- tex is the path to the image file for the texture
- x_off y_off are coordinates for the texture on the face
- angle the angle of the texture
- x_scale y_scale the scale of the texture
- cont_flags [Content
  flags](Mapping/Surface_inspector#Content_flags "wikilink")
- surf_flags [Surface
  flags](Mapping/Surface_inspector#Surface_flags "wikilink")
- surf_value E.g. the light value for surface lights

Flags are optional, if they are missing one should assume they are zero.

## Attributes

One attribute is obligatory, namely "classname" that defines what an
entity represents. Each class has a different set of meaningful other
attributes. See the [entities article](Mapping/Entities "wikilink") for
a full list.

[worldspawn](worldspawn "wikilink")
The first entity defining world geometry and some globals.

- maxlevel
- maxteams

[func_group](func_group "wikilink")
Some additional geometry.

[misc_model](misc_model "wikilink")
External model to be placed on map.

- model (path to a model file)
- origin
- angles

[light](light "wikilink")
A point lamp.

- origin
- _color (note the underline)
- light

[info_human_start](info_human_start "wikilink"), [info_civilian_start](info_civilian_start "wikilink"), [info_alien_start](info_alien_start "wikilink"), [info_player_start](info_player_start "wikilink")
Phalanx, civilian, alien or multiplayer spawn.

- origin
- angle
- team (only with info_player_start)

[misc_particle](misc_particle "wikilink")
Particle generator.

- origin
- particle

## Levelflags

see [Mapping/Levelflags](Mapping/Levelflags "wikilink")

`LEVEL1 0x0100`
`LEVEL2 0x0200`
`LEVEL3 0x0400`
`LEVEL4 0x0800`
`LEVEL5 0x1000`
`LEVEL6 0x2000`
`LEVEL7 0x4000`
`LEVEL8 0x8000`

[Category:Mapping](Category:Mapping "wikilink")