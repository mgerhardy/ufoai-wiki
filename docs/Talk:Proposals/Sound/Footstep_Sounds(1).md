I would suggest something more like this:

    terraintype grass
    {
        bouncefraction 1.0
        sounds {
            footsteps {
                normal (
                    "footsteps/grass"
                    "footsteps/grass1"
                    "footsteps/grass2"
                )
                crouched (
                    ...
                )
                heavy (
                    ...
                )
                spider (
                    ...
                )
                wheeled (
                    ...
                )
                ...
            }
            bounce (
                "weapons/grenade-bounce-grass"
            )
        }
        textures(
            "tex_nature/grass001"
            "tex_nature/grass"
            ...
        )
    }

--[DexCisco](User:DexCisco "wikilink") 01:35, 24 November 2012 (SAST)