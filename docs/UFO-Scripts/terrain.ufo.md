This script file allows you to define some terrain settings that depends
on the texture. Keep in mind, that this is global in the game - not per
map. The given id is a ufo path of the texture - relative to .

We have a script in that is parsing the textures from the map source
files when they have the
[surfaceflag](Mapping/Surface_inspector#Surface_flags "wikilink")
[footstep](Mapping/Footsteps "wikilink") set.

footstepsound [V_STRING](V_STRING "wikilink")
Sound to play for footsteps relative to base/sound (see [Directory
tree](Directory_tree "wikilink"))

bouncefraction [V_FLOAT](V_FLOAT "wikilink")
The fraction by which grenade bounces are multiplied. 1.0 means no
change, 0.0 means no bounce at all. If not specified, defaults to 1.0.

particle [V_STRING](V_STRING "wikilink")
Particle that is shown when an actor walks on this texture

footstepvolume [V_FLOAT](V_FLOAT "wikilink")
The volume of the footstep sound. 1.0 is the loudest, default is 0.2

## Example

    // normal grass
    terrain tex_nature/grass001 {
        footstepsound "footsteps/grass2"
        bouncefraction 0.3
    }

    // high grass
    terrain tex_nature/jungle002 {
        footstepsound "footsteps/grass2"
        bouncefraction 0.2
    }

[Category:UFO-Scripts](Category:UFO-Scripts "wikilink")