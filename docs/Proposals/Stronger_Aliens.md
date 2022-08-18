# Stronger Aliens

We need the few alien races we have to assist during the whole campaign.
To be able to make it balanced we need weak aliens for the beginning and
stronger to the end.

A first crude try was trippling taman team to have some diversity in
their stats. It was the only solution possible without coding with the
current script systems. However it had some bad sideeffects on the UI,
so it's time to fix up the system.

The **good news** is that we have (almost) everything for a correct
system, we just need to do some wiring.

## We have

#### Character templates for aliens

That contains the skills of an alien

` chrtemplate alien_taman_light {`
`   strength  "20 20"`
`   ...`
` }`
` chrtemplate alien_taman {`
`   strength  "38 38"`
`   ...`
` }`

#### Alien teams

That describes the species and lists the useable character templates

` team taman {`
`   name  "_Taman"`
`   tech  rs_alien_taman_autopsy`
`   ...`
`   templates (`
`     alien_taman`
`   }`
` }`

#### Alien team definitions for missions

Which says which aliens go to missions in early/mid/late game and what
can they carry.

` alienteam scouts {`
`   category ("recon")`
`   equipment ("alien_workers")`
`   teaminterest {`
`     mininterest 0`
`     maxinterest 49`
`     team (taman)`
`   }`
`   ...`
` }`

## The solution

... is easy: allow selecting character templates in *alienteam*s

` alienteam scouts {`
`   category ("recon")`
`   equipment ("alien_workers")`
`   teaminterest {`
`     mininterest 280`
`     maxinterest 309`
`     team (taman/alien_taman shevaar)`
`   }`
`   ...`
` }`

Where

- *taman*/*alien_taman* means only *alien_taman* chrtemplate of *taman*
  teamDef can play, while
- *shevaar* or *shevaar*/ means any character templates of teamDef
  *shevaar* is useable

Sounds good? How to implement?

### Implementation

Store character templates in **alienTeamGroup_t** structure too.

`  typedef struct alienTeamGroup_s {`
`    int idx;`
`    int categoryIdx;`
`    int minInterest;`
`    int maxInterest;`
` `
`    const teamDef_t *alienTeams[MAX_TEAMS_PER_MISSION];`
` +  const chrTemplate *alienChrTpls[MAX_TEAMS_PER_MISSION];`
`    int numAlienTeams;`
`  } alienTeamGroup_t;`

If an entry has a vaild template set, store it's pointer, if not, store
NULL. This needs extending the parser in cp_parse.cpp
(CP_ParseAlienTeam) and the structure change above (cp_campaign.h) and
maybe some lookup functions for character templates.

In GAME_AppendTeamMember -\> CL_GenerateCharacter -\>
CHRSH_CharGenAbilitySkills chain, CHRSH_CharGenAbilitySkills generates a
character from a chrTemplate-\>rate based random template. It needs to
be changed so we can ask for a specific template and to the random stuff
if get NULL chrTemplate only. This would also help eliminating the @HACK
for the soldier_mp multiplayer character template too.

## Resistance, Body models

... are out of question for 2.5, but for later:

Even *"weak"* humans react bit differently to heat or electricity so it
is the **character**s' attribute too not only the **race**s'. So I think
we should move resistance values into **character templates** ...
*partially*. I say *partially* to save some typing for us and modders,
it has no use to copy&paste the same values without any real value. So
let's have a **base value** in the teamDef (values default to 0) and a
**modifier value** in the character template (values default to 0).
Resistance would be simply calculated as **base + modifier** ofc.

This will probably need more coding on server-side which I guess uses
the teamDef to get resistance values and not the actors.

About models, I can suggest similar: allow adding models to the
chrTemplates. If we want completely different models for a race. Leave
the models out from the teamDef definition and add them to the character
templates connected to it.

-- [Geever](User:Geever "wikilink") 01:10, 8 February 2013 (SAST)