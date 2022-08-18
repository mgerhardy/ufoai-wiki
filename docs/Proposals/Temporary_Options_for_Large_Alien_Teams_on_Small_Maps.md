Currently there is a problem from the middle to the late game with large
alien teams appearing on small maps. This is extremely difficult and
forces the player to over-rely on exploits like hiding in smoke, etc. At
the moment the game does not choose a map appropriate for alien team
size, so it is quite frequent in the late-game to get small maps with
large teams.

Map definitions have a maxaliens parameter, but this is used for
campaign, skirmish and multiplayer. Because of this, I long ago set the
maxaliens parameter very high for all maps, so that players can try out
a skirmish with tons of aliens (in skirmish I only need one survivor to
win, after all, but in the campaign I need a better survival rate!).

This causes some problems when trying to use this to balance campaign
missions. I can think of two solutions to this for 2.5, which do not
require adding in size-criteria to the map selection code (which has its
own problems regarding map variety). Both involve limiting alien team
size based on the map, which means it will be possible to face large
UFOs with few aliens, which is not ideal. But to address this properly
without reverting back to too much map repetition, we need to assess our
map collection and consider a more long-term solution.

## The easy solution

We just preference the campaign over skirmish, and revise the maxaliens
parameter to be appropriate for campaign balance. Skirmish now has an
"Alien Rush" mode the user can select to spawn infinite enemies, and the
campaign is the core of the game anyway. But Skirmish and Coop players
will face low arbitrary limits on alien team size.

## The organised solution

We can use the map parameters to set up separate map definitions for
campaign, skirmish and multiplayer maps, and split them into separate
files (maps_campaign, maps_skirmish, maps_multiplayer). This will allow
us to have specific control for each gametype, which fits the more
long-term goal to develop the gametypes separately. But doing a large
restructuring of the map files this close to 2.5's release would risk
introducing errors that could stop maps from spawning properly in the
campaign. And it would be more script files to maintain over time.

Duplicating the scripts is certainly a no-go. But what about
maxaliens_campaign, maxaliens_skirmish and maxaliens_multiplayer params
? --[Duke](User:Duke "wikilink") 21:05, 4 March 2013 (SAST)

- If I recall, mattn didn't really want the gametypes involved like
  this, but of course we already have parameters for whether a map is
  available for campaign/skirmish/multiplayer.
  --[H-hour](User:H-hour "wikilink") 22:43, 4 March 2013 (SAST)
- Not to be too pedantic, but the scripts wouldn't actually be
  "duplicated". We'd just have separate entries for different gametypes
  (we already do the same thing for different assemblies,
  multiplayer-specific maps or skirmish-only maps, we just throw them
  all into one file). --[H-hour](User:H-hour "wikilink") 22:43, 4 March
  2013 (SAST)
  - Even if the \# of script files would be constant, they would be 3
    times as long, right ? ==\> no go. --[Duke](User:Duke "wikilink")
    23:24, 4 March 2013 (SAST)
- If we use the ids from gamemodes.ufo like e.g. maxaliens for all
  gametypes, maxaliens_multiplayer for well... multiplayer and so on, I
  would be fine with it. We can also override it with a gametype block
  e.g.

`mapdef africa_large`
`{`
`   map             "+africa"`
`   param           "large"`
`   description     "_African Village"`
`   multiplayer     true`
`   teams           2`
`   gametypes (`
`       fight1on1`
`       fight2on2`
`       coop2`
`       coop3`
`       coop4`
`   )`
`   maxaliens       30`
`       `**`skirmish {`**
`              `**`maxaliens 10`**
`              `**`description "_Some descriptive text"`**
`       `**`}`**

`   civilianteam    africa`

`   aircraft`
`   (`
`       craft_drop_firebird`
`       craft_drop_herakles`
`       craft_drop_raptor`
`   )`

`   ufos`
`   (`
`       craft_ufo_bomber`
`       craft_crash_bomber`
`       craft_ufo_corrupter`
`   )`

`   terrains`
`   (--`[`H-hour`](User:H-hour "wikilink")` 14:14, 5 March 2013 (SAST)`
`       "grass"`
`       "tropical"`
`       "desert"`
`       "mountain"`
`   )`

`   cultures`
`   (`
`       "african"`
`   )`

`   populations`
`   (`
`       "village"`
`       "suburban"`
`       "urban"`
`   )`
`}`

- - the problem here is, that it would not be possible to add a mod with
    a new gametype because one would have to override all the mapdefs,
    too. Specifying this in a block independent from the mapdef would
    maybe be better and more modable. --[Mattn](User:Mattn "wikilink")
    12:53, 5 March 2013 (SAST)
    - We could keep the existing maxaliens parameter in the mapdef as
      the kind of default, upper-limit for a map. Then have a separate
      block where we store max aliens for campaign (we wouldn't need it
      for mp/skirmish) and eventually we could even put
      terrain/culture/population data there, for instance.
      --[H-hour](User:H-hour "wikilink") 14:14, 5 March 2013 (SAST)

<!-- -->

- Imo we can treat the 'maxaliens' parameter as campaign-only. In
  skirmish (and mp?), the user can always change the number of aliens.
  But, when selecting the map, we dont know the size of the alien team
  yet, no? --[ShipIt](User:ShipIt "wikilink")
  ([talk](User_talk:ShipIt "wikilink")) 09:51, 15 March 2015 (CET)

[Category:Proposals](Category:Proposals "wikilink")