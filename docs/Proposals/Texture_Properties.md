## What we have

We have 1935 different textures right now. The \*_nm.\*, \*_sm.\* and
\*_gm.\* are not included in this number, but the textures used for
animations only are. 1142 textures are used within the maps, whereas in
this case the animation textures are not included.

For every texture we can assign different properties. That are

- [surface parameters](UFO-Scripts/terrain.ufo "wikilink")
  - footstepsound
  - footstepvolume
  - particle
  - bouncefraction

<!-- -->

- [material system parameters](Mapping/Materialsystem "wikilink")
  - bump
  - parallax
  - specular
  - hardness
  - blending
  - animations

Those are defined in different places. The surface parameters in
terrain.ufo, the material system parameters are in the .mat files for
each map.

There is also a proposal about [changes for the footstepsound
property](Proposals/Sound/Footstep_Sounds "wikilink").

## Problems

- General
  - Imo the surface and material system parameters belong together. They
    are properties of the texture. Having them spread all over the place
    is not good. The need to have duplicated entries in different files
    is not good.

<!-- -->

- the .mat files
  - In order to to take advantage of the material system for a certain
    texture, you need to make an entry in the maps .mat file. This
    usually results in either
    - No entry at all.
    - A copy/pasted entry.
  - Not even easy to find out what textures are used within the map.
  - Maintaining this is a nightmare. There might be entries for textures
    that were replaced and therefore are not longer used within the map.
  - An example: The UFOs should look the same on all maps. So, in each
    .mat file, for every map, we have the same entries regarding the
    related textures, over and over again. Now, if I take a closer look
    and see some value in there that could be changed to get a better
    result - I would need to change that value in all those files.

<!-- -->

- terrain.ufo
  - Is simply not flexible enough. It is not possible to assign muliple
    sounds. It simply assumes a concrete texture is always only used for
    concrete surfaces, which is not true in a lot of cases.
  - The values given there cannot be overwritten.

## Proposed

In order to get rid of those problems, I propose a much simpler
approach.

- A new .ufo file to store property templates for various texture
  categories. These values are global for each texture within this
  category over all maps.
- templates.ufo:

<!-- -->

    category metal_thin {
        description "some text"
        footstepsound "footsteps/metal1"
        bouncefraction "0.7"
        bump 0.1
        parallax 1.0
        hardness 0.9
        specular 1.0
    }

- A new .ufo file to assign a categorie to each texture. These values
  should overwrite/expand those given by the category template and are
  used for the texture over all maps.
- properties.ufo:

<!-- -->

    texture tex_base/vent_round2 {
        category metal_thin
        {
        texture tex_base/vent_round2_a0
        blend GL_SRC_ALPHA GL_ONE_MINUS_SRC_ALPHA
        anim 6 48
        }
    }

- Make it possible to define all the texture properties in the .mat
  file, again overwriting the previous values.

<!-- -->

- This would make terrain.ufo and possibly some of the .mat files
  obsolete.

The idea in general:

- The mapper should have the chance to define the textures properties
  for his map completely in the maps .mat file, giving him as much
  freedom as possible.
- But he doesn´t need to, because the game can use the global values for
  the textures given in the properties file.
- If no certain values given for the texture in the properties file, the
  game uses those from the textures category template.
- If the texture has no category assigned, the game can give an output
  to the console.

## Further Improvements

Maybe giving min-max values in the templates would allow some diversity
for e.g. bouncefraction, so the behaviour of a certain texture is
slightly different each time the map is loaded.

Also, implementing the [changes for the footstepsound
property](Proposals/Sound/Footstep_Sounds "wikilink") would be possible
in a way like this

    category metal_thin {
        description "some text"
        footstepsound {
            "footsteps/metal1"
            "footsteps/metal2"
            "footsteps/metal3"
            "footsteps/metal4"
            }
        bouncefraction "0.6"
        bump 0.1
        parallax 1.0
        hardness 0.9
        specular 1.0
    }

or by using a comma seperated list. This would allow a different sound
for the texture on each map start.

## Credits

The idea is based on the work of [DexCisco](User:DexCisco "wikilink")
and [Crystan](User:Crystan "wikilink").

--[ShipIt](User:ShipIt "wikilink") 18:21, 10 March 2013 (SAST)

[Category:Proposals](Category:Proposals "wikilink")