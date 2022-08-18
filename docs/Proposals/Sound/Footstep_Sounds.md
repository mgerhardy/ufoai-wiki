Currently the "Footstep Sound System" supports only one sound per
texture and the assignment is very inconvenient. It would be better if
you could create "material groups"(e.g.wood,stone,dirt,gravel etc.) and
assign several sounds to every group (four stone sounds to the stone
group) via a ufo. Now you can assign multiple textures to these material
groups in the same or a new ufo. Here's a example how it could look
like:

`// Material Group Wood `
`wood {`
`  footsteps/wood1`
`  footsteps/wood2`
`  footsteps/wood3`
`  footsteps/wood4`
`}`

`// Material Group Stone `
`stone {`
`  footsteps/stone1`
`  footsteps/stone2`
`  footsteps/stone3`
`  footsteps/stone4`
`}`

`// Wood Textures`
`wood {`
`  tex_buildings/floor001`
`  tex_ctp1/wood_b_10`
`  tex_misc/wood_palet`
`  ...`
`}`

`// Stone Textures`
`stone {`
`  tex_buildings/concrete001`
`  tex_buildings/concrete005`
`  tex_buildings/concrete007`
`  tex_buildings/floor_se01`
`  ...`
`}`

To reduce the amount of work a function in radiant to assign textures to
material groups would be also useful.

## Questions

- Should we select the same sound from the group for every surfaces the
  texture is applied to? I mean, should the first step have the same
  sound as the second? Or should they be randomly picked? Or should we
  select the particular sounds on level start?
  --[Mattn](User:Mattn "wikilink") 12:04, 1 October 2012 (SAST)

Answer: Just randomly picked.

- What categories exactly are you thinking of? Concrete, dirt, glass,
  grass, gravel, leaves, metal, sand, snow, soft, stone, tiles, wood.
  Anything else? Or not that detailed at all?
  --[ShipIt](User:ShipIt "wikilink") 07:30, 3 January 2013 (SAST)

<!-- -->

- What about using the tex_NAME NAME-part as category? Ok, yes, we would
  have to reorder the textures on time. But this is a sed script and we
  are done. Using the NAME as category would allow us to add new
  textures with sound support without editing any ufo script file (which
  imo is the best) --[Mattn](User:Mattn "wikilink") 09:19, 3 January
  2013 (SAST)
  - I'm a little hesitant about this. The folder system is the principle
    method of organization for finding and using textures in Radiant.
    Yes, the current organization is a mess, but where it's used
    properly -- alien base, misc (for signs), nature, streets -- it is a
    big help. Putting the alien base floor in with all the other tiles
    would be both annoying and encourage new mappers to mis-use them
    (ie - use alien textures for non-alien surfaces).
    --[H-hour](User:H-hour "wikilink") 11:58, 3 January 2013 (CET)



I agree. --[ShipIt](User:ShipIt "wikilink") 08:43, 4 January 2013 (SAST)

- - If we go with the footstep sounds as proposed, what happens to the
    "bouncefraction" property? Do we keep this next to the sounds, e.g.
    every material group has a bouncefraction number assigned?
    --[ShipIt](User:ShipIt "wikilink") 08:43, 4 January 2013 (SAST)

[Category:Proposals](Category:Proposals "wikilink")