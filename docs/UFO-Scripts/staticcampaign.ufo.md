## Static campaign

The static campaign is there to allow a fixed map selection that can be
tweaked by the scripter. You have the opportunity to (almost) define the
order of the appearance of the maps in the campaign.

*So the static campaign is only about the map selection* - the remaining
stuff is the same as the other campaign. But the map selection has a big
influence on the campaign progress.

## Description

### mission

- **city**: City reference to define the position of the mission

### stage

A stage contains several sets that define a timeframe and a mission and
ufo set that should appear.

#### set

- **delay** [V_DATE](V_DATE "wikilink"): year, day, hour
- **frame** [V_DATE](V_DATE "wikilink"): year, day, hour
- **expire** [V_DATE](V_DATE "wikilink"): year, day, hour
- **missions** [V_STRING](V_STRING "wikilink"): the mission set
  (mapdefs)
- **number** [V_INT](V_INT "wikilink"):
- **quota** [V_INT](V_INT "wikilink"): The amount of missions you have
  to fulfill to mark this set as done
- **needed** [V_BEP](V_BEP "wikilink"): Reference to another sets
- **ufos** [V_INT](V_INT "wikilink"): The amount of ufos to spawn in
  this set
- **nextstage** [V_STRING](V_STRING "wikilink"): The next stage that is
  going to become active once the current set is done
- **endstage** [V_STRING](V_STRING "wikilink"): Ends the given stage
  (can be the current, or any other)
- **commands** [V_STRING](V_STRING "wikilink"): Commands that are
  executed once the set is done

## Example

`staticcampaign example {`
`   mission africa_large`
`   {`
`       city    cairo`
`   }`

`   stage intro`
`   {`
`       set first`
`       {`
`           delay       "0 0 10"`
`           frame       "0 3 0"`
`           expire      "0 6 0"`
`           missions    "africa_large"`
`           number      1`
`           quota       0`
`       }`
`       set terror_only`
`       {`
`           needed      first`
`           delay       "0 5 12"`
`           frame       "0 9 0"`
`           expire      "0 8 0"`
`           missions    "italy japan_large village mine mart estate bungalow bungalow2 wilderness rivertown transport eaglenest neighbourhood" `
`           number      12 `
`           quota       8`
`       }`
`       set soldier_terror`
`       {`
`           needed      terror_only`
`           delay       "0 10 7"`
`           frame       "0 15 0"`
`           expire      "0 45 0"`
`           missions    "bunker japan_small dam spedition stadium druglord tower small_house gate fueldump city_industry community_centre"`
`           number      12`
`           quota       7`
`           ufos        2`
`       }`
`       set landed_ships`
`       {`
`           needed      soldier_terror`
`           delay       "0 5 2"`
`           frame       "0 6 0"`
`           expire      "0 5 0"`
`           missions    "frozen_alienlandingnature rivertown farm2 frozen_alienlandingindustrial village_commercial"`
`           quota       4`
`       }`
`       set ultimate_terror`
`       {`
`           needed      soldier_terror`
`           delay       "0 15 7"`
`           frame       "0 6 0"`
`           expire      "0 5 0"`
`           missions    "oriental_large small_house subway gasstation tower village military_convoy frozen_industrial mansion"`
`           quota       7`
`           nextstage   ufos_are_coming`
`           ufos        2`
`       }`
`       set stop`
`       {`
`           needed      ultimate_terror`
`           delay       "0 20 0"`
`           endstage    intro`
`       }`
`   }`

`   stage ufos_are_coming`
`   {`
`       set first_coming`
`       {`
`           delay       "0 2 7"`
`           frame       "0 12 0"`
`           expire      "0 5 0"`
`           missions    "fighter_crash"`
`           quota       1`
`           ufos        4`
`       }`
`       set crashed_and_landed`
`       {`
`           needed      first_coming`
`           delay       "0 0 1"`
`           frame       "0 10 0"`
`           expire      "0 8 0"`
`           missions    "construction office harbour city2 resort bungalow tropic_river city_disco tropic_drug_crash oriental_medium_crash desert_harvester_crash"`
`           quota       6`
`           nextstage   invasion`
`           ufos        2`
`       }`
`       set stop_coming`
`       {`
`           needed      crashed_and_landed`
`           delay       "0 11 0"`
`           endstage    ufos_are_coming`
`       }`
`   }`

`   stage invasion`
`   {`
`       set first_invasion`
`       {`
`           delay       "0 5 1"`
`           frame       "0 10 0"`
`           expire      "0 7 0"`
`           missions    "africa_large eaglenest lake_ice corrupter_crash oriental_mosque england"`
`           quota       6`
`           nextstage   alienbase`
`       }`
`       set stop_invasion`
`       {`
`           needed      first_invasion`
`           delay       "0 11 0"`
`           endstage    invasion`
`           commands    "addeventmail alien_base_discovered;"`
`       }`
`   }`

`   stage alienbase`
`   {`
`       set first_alienbase`
`       {`
`           delay       "0 11 0"`
`           missions    "alienbase"`
`           quota       1`
`       }`
`       set stop_alienbase`
`       {`
`           needed      first_alienbase`
`           delay       "0 12 0"`
`           endstage    alienbase`
`           commands    "cp_endgame;"`
`       }`
`   }`
`} `

[Category:UFO-Scripts](Category:UFO-Scripts "wikilink")
[Category:Contribute](Category:Contribute "wikilink")