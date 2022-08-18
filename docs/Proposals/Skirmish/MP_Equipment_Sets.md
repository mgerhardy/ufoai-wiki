### Implemented

This proposal has been implemented except that currently there is no
weapon selection in multiplayer.

### Original Proposal

Currently, when selecting a equipment set in Skirmish or Multiplayer
mode, there is a large number of equipment sets to choose from. Most of
these are not useful for skirmish/mp and they have names that don't make
it clear what they contain.

I would like to see a parameter added to the equipment definitions that
would specify whether an equipment template is meant for skirmish/mp.
That way the skirmish/mp setup screens would only contain weapon sets
that make more sense for that gameplay. This could be as simple as:

campaignonly false


I don't really like this approach - with my cgame support in mind I
would rather allow each cgame mode to define a list of equipments that
are valid for this mode. I would rather not add cgame specific
parameters to 'global' script data. But the general idea is good. I will
see what I can come up with to implement this feature.
--[Mattn](User:Mattn "wikilink") 07:42, 1 October 2011 (CEST)


That sounds fine as well. I can see how having a list of equipment sets
for each gametype would be better. Perhaps the same could be done for
maps in some way? --[H-hour](User:H-hour "wikilink") 10:28, 1 October
2011 (CEST)


we already have gamemodes.ufo - maybe we can extend this
--[Mattn](User:Mattn "wikilink") 11:12, 1 October 2011 (CEST)

It would also be nice to be able to give the equipment definitions a
title that would be accessible in the UI, so that the player could
choose from meaningful titles like "All Weapons", "Starting Weapons",
"Low Tech", "Medium Tech", "High Tech", "Lasers Only", etc.


This is already implemented (git rev:
b2096c444d347ec0648ca79ad24210d11aabd8b1)
--[Mattn](User:Mattn "wikilink") 07:40, 1 October 2011 (CEST)

Which reminds me - the names are still missing in the script... \*hint\*
\*hint\*


now has names, but do not. --[H-hour](User:H-hour "wikilink") 10:28, 1
October 2011 (CEST)

[Category:Proposals](Category:Proposals "wikilink")