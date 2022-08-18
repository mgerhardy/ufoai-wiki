Improvements to the maps definition to allow for improvements to the UI
in the future. Main changes:

- Have a top-level theme definition that takes an unlimited number of
  children map definitions. Then the player would be able to click on a
  theme and after that select a particular map in that theme if there
  are several available for the game type they have chosen.
- Add settings for specifying map usage for campaign, skirmish and
  multiplayer, with gametype options for skirmish and multiplayer. (See
  discussion page for possible revision to this aspect)
- New parameter for map title, and layout (fixed or random)
- Support for comma-separated list of assemblies supplied to param

### Example maps.ufo definition:

`# /*`
` * Theme definition on a per-RMA basis`
` * This would be the first thing the user selects`
` */`
`themedef forest`
`{`
`   title           "_Forest"`
`   description     "_A sparsely populated forest region"`
`   `
`   `
`   /*`
`    * Map definition for large, single-player map using forest theme`
`    */`
`   mapdef forest_large`
`   {`
`       map     "+forest"`
`       size        "large"`
`       maxaliens   15`
`       `
`       /*`
`        * A proper title to help players select the appropriate mapdef.`
`        */`
`       title       "_Large (Random)"`
`       `
`       /*`
`        * Optional screenshot prefix so that different`
`        * mapdefs could use different screenshots.`
`        * This example would look for screenshots named:`
`        * forest_large, forest_large_1, etc.`
`        * If no screenshots are found, it should fall`
`        * back to the themedef. Same will be true for `
`        * loading shot.`
`        */`
`       mapshots    "forest_large"`
`       `
`       /*`
`        * Whether or not the assembly will result in`
`        * random map configurations or a fixed map.`
`        * Fixed should be used even in cases where the`
`        * user can change the UFO or Dropship, as long`
`        * as the rest of the map doesn't change.`
`        * Options: fixed,random`
`        */`
`       layout      random`
`       `
`       /* `
`        * Comma-separated list of assemblies supported.`
`        * Useful for fixed assembly maps like alien base `
`        * or in cases where we create a multiplayer-specific`
`        * assembly that we don't want to be used.`
`        */`
`       param       "large,large2"`
`       `
`       /* `
`        * Which game types it supports. The game will then`
`        * look in the definition for (gametype)_modes. (See`
`        * below). Campaign could be read as a special entry.`
`        */`
`       gametypes   "campaign,skirmish"`

`       /*`
`        * Skirmish game types supported.`
`        * For now there is only deathmatch but in the future`
`        * there could be things like capturing a zone, blowing`
`        * something up, survival, defend, etc. The alienrush option`
`        * should probably be an option on several game modes`
`        * rather than a separate game type.`
`        * Could be replicated for any custom gametype.`
`        */`
`       skirmish_modes`
`       {`
`           deathmatch`
`       }`
`       `
`       /* `
`        * None of the following details need to be changed`
`        */`
`       aircraft { }`
`       ufos { }`
`       terrains { }`
`       cultures { }`
`       populations { }`
`   }`
`   `
`   /*`
`    * Map definition for MP-map using forest theme`
`    */`
`   mapdef forest_mp`
`   {`
`       map     "+forest"`
`       size        "large"`
`       maxaliens   15`
`       mapshots    "forest_mp"`
`       layout      fixed`
`       param       "mp"`
`       gametypes   "multiplayer"`
`       `
`       /*`
`        * If there are multiple mp maps, a `
`        * unique name will help players remember`
`        * preferred assemblies.`
`        */`
`       title       "_The Black Forest"`
`       `
`       /*`
`        * Multiplayer game types supported.`
`        * The asterisk (*) or some other character could be used`
`        * to indicate that this map is ideal for this gametype.`
`        * Eventually it could be useful to be able to view recommended`
`        * maps for a gametype`
`        */`
`       multiplayer_gametypes`
`       {`
`           1on1`
`           1on1on1`
`           2on2`
`           2on2on2`
`           coop2`
`           coop3`
`           coop4`
`           *kingofthehill1on1`
`           kingofthehill1on1on1`
`           kingofthehill2on2`
`           *domination1on1`
`           domination2on2`
`       }`
`   }`
`}`

[Category:Proposals](Category:Proposals "wikilink")