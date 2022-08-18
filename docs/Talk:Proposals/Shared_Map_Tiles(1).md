## Blending Problems

I could be wrong, but I think that the blending process is very much
visual-only. It might be very difficult to implement material system
parameters (bump, etc) on a blend. If this is the case (and Sandro or
Mattn will know better), then it may be better to implement a different
texture-swap for this case in particular, one which would not blend a
texture on the top but actually replace it earlier in the process, like
the dummy texture system used in ufocrash.
--[H-hour](User:H-hour "wikilink") 15:04, 20 March 2013 (SAST)


Yes, replacing would be a lot better - we have to somehow specify which
texture should be used for replacing. But this does not solve the
problem of rotated or scaled textures - so we would have to extend the
replacement code (to also replace the texcoords).
--[Mattn](User:Mattn "wikilink") 15:11, 20 March 2013 (SAST)


Extending the code to replace the texcoords would great. If this proves
too complicated, I think we could live with out it. Each RMA will have
to have this implemented itself. During that process, it should not be
too difficult to ensure the ground texture on all tiles matches a
standard scale (I would say 0.25). To be honest, this should be a
standard we aim towards anyway. Many of the old maps have really bad
texture scaling issues. --[H-hour](User:H-hour "wikilink") 15:17, 20
March 2013 (SAST)


If a replacement sytem is the best way, fine. Imo replacing the
texcoords in the code is not needed. This can easily be done in the map
files. --[ShipIt](User:ShipIt "wikilink") 21:01, 20 March 2013 (SAST)

## Questions

- ShipIt, what do you mean by: "We need unified tile descriptors."?
  --[H-hour](User:H-hour "wikilink") 14:07, 20 March 2013 (CET)



The tile descriptor for the shared tile is located in the shared.ump so
far. This needs to fit in all maps where the tile is used. I think this
will be not much of a problem. Changing this should be part of another
proposal.--[ShipIt](User:ShipIt "wikilink") 21:01, 20 March 2013 (SAST)

## Lighting problems

We still have the problem with the lightmaps. But this could be worked
around with autogenerating the maps (as they are just copies of the
shared map tile with changed lighting parameters in the worldspawn)
--[Mattn](User:Mattn "wikilink") 15:24, 20 March 2013 (SAST)


To decide which lighting settings we should take, the default worldspawn
flags should be moved to the
[ump](Mapping/Random_map_assembly "wikilink") file, too. (they should
still be override-able in the map file) --[Mattn](User:Mattn "wikilink")
14:26, 20 March 2013 (CET)


This is done now - so the autogenerating of "equal" map tiles can be
started now. --[Mattn](User:Mattn "wikilink") 22:33, 20 March 2013
(SAST)

Sorry, I tried hard to get behind this, but I really do not see what the
problem is. Is this in case a map uses worldspawn settings different
from the default? I am lost. --[ShipIt](User:ShipIt "wikilink") 12:40,
21 March 2013 (SAST)


There are two benefits to having the worldspawn settings in a .ump
file. 1) As you said, if a map uses a non-default lighting setting and
the .ump imports the dropship tile, this will ensure the lighting is
consistent. 2) We no longer have to set the worldspawn settings in every
RMA tile! That means if you change the lighting, the maxlevel, etc, you
don't need to change it in 30 different tiles.
--[H-hour](User:H-hour "wikilink") 16:32, 21 March 2013 (SAST)


1\) But the shadows are part of the lightmap in the .bsp file, no? Can
those be changed on the fly? 2) Good thing. At least something I
understand. --[ShipIt](User:ShipIt "wikilink") 17:45, 21 March 2013
(SAST)


1\) Mattn is talking about configuring the build scripts which compile
the maps so that they will automatically compile another .bsp if
different lighting settings are found. So the extra .bsps will be there,
but they will be generated from a single .map file. (This is probably
only a few cases where lighting should be different, like night lighting
on +bridge for example.) --[H-hour](User:H-hour "wikilink") 20:11, 21
March 2013 (SAST)


Thanks for explaining. --[ShipIt](User:ShipIt "wikilink") 21:12, 21
March 2013 (SAST)