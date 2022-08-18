There are some "problems" in this proposal.

the mapdef should not contain any information about skirmish (the
sk_\*) - only about singleplayer and multiplayer. there maybe will be
more cgame mods that are not only campaign, skirmish and multiplayer.
and these cgame dlls can be added and removed dynamically. that's why
the information should be in a mod directory in extra script files.

i like the prefix idea - and maybe we should already do this for 2.4 -
as currently some static maps and rma share the same loading shots -
which is just wrong.


--[Mattn](User:Mattn "wikilink") 18:39, 8 September 2011 (CEST)

<!-- -->


I've made some changes to address the possibility of other cgame types.
Now game types are specified in a comma-separated list and the game
could search for (gametype)_modes for a list of modes supported for
each cgame type so that custom game types could also have different
modes. Does that look more feasible? --[H-hour](User:H-hour "wikilink")
19:42, 8 September 2011 (CEST)

<!-- -->


Ok, now I understand a bit better what you want to do with cgame types
(I think). Perhaps the mapdef should not include any information about
specific cgame types (mp/skirmish/campaign) or game types (1on1, etc).
Perhaps we should just say what the map technically supports:

`/*`
`* This only indicates what alien and civilian spawn points`
`* are available on the map.`
`*/`
`maxaliens      25`
`maxcivilians       10`

`/*`
` * This indicates which multiplayer teams have spawn points`
` * available on the map. Multiplayer would automatically be`
` * true/false if this is 1/0.`
` */`
`teams          4`

`/*`
` * Other parameters could indicate the presence of requirements`
` * for future gametypes, like domination.`
` */`
`domination     3 // 3 Domination zones supported`
`kingofthehill  true`
`demolition     2 // 2 Demolition zones supported`

Then we could place the conditions necessary for a gametype in that
gametype's definition:

`/*`
` * Skirmish game type would require at least one human spawn`
` * point and one alien spawn point`
` */`
`minhumans      1`
`minaliens      1`

`/*`
` * Multiplayer game type (1on1) would require at least two`
` * teams supported`
` */`
`minteams       2`

`/*`
` * Domination game type would check for at least two domination`
` * zones.`
` */`
`mindomination      2`

And finally, the cgame definition would include a list of gametypes it
supports.

`cgame multiplayer {`
`   window  "multiplayer"`
`   name "_Multiplayer"`
`   gametypes {`
`       1on1`
`       1on1on1`
`       2on2`
`       2on2on2`
`       coop2`
`       coop3`
`       coop4`
`       domination`
`       kingofthehill`
`   }`
`}`

With this setup, the maps list would automatically get sorted according
to what is available for a cgame type. We could then implement something
in the UI that would allow the player to select a gametype and it would
display only supported maps. Users could easily modify the maps list by
creating their own mapdefs. And future cgames/gametypes would be able to
build on existing mapdefs easily. --[H-hour](User:H-hour "wikilink")
11:06, 1 October 2011 (CEST)