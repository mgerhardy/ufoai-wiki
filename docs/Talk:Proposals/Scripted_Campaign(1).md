## Introduction

This page is to give an opportunity for the devs to ask
[mattn](User:mattn "wikilink") what his plans are for the scripted
campaign, to better understand his vision and to decide what role it
should have in the future. For reference, please see the file which
outlines an example campaign using [mattn's](User:mattn "wikilink") new
system.

I've also written up a [briefing on how the current campaign
works](Development/Specifications/Campaign "wikilink") for comparison.

## Basic Concept

The assumptions I draw from the example campaign are the following
(please correct where necessary):

- Each stage of the game defines a number of mission "sets". Each set
  includes a list of possible maps and a quota that must be reached
  before the set is complete. When a set is complete, the player moves
  to the next set.
- The number of UFOs which appear are defined for each set.
- Quota represents some kind of minimum number of successful missions
  which must be completed for each set.
  - Does this represent some kind of fail condition?
    - The quota counter is only increased if the mission was won.
      --[Mattn](User:Mattn "wikilink") 14:41, 6 December 2012 (CET)
  - What happens if the number of UFOs is reached but the quota of
    successful missions are not complete?
    - The number of ufos is not related to the missions that appear. The
      ufos will add new missions that are not in mission list. Those are
      random. --[Mattn](User:Mattn "wikilink") 15:41, 6 December 2012
      (SAST)
- There appears to be some kind of command callback at the end of each
  stage. This is used in the alien base stage, but how is the alien base
  actually created? How does it know to spawn the mission?
  - It does know how to spawn the mission because there is a mapdef with
    alienbase - it will just create an alienbase mission linked with the
    mapdef alienbase. --[Mattn](User:Mattn "wikilink") 14:35, 6 December
    2012 (CET)
    - Btw. this is not yet fully implemented - see
      SCP_CampaignAddMission --[Mattn](User:Mattn "wikilink") 15:39, 6
      December 2012 (SAST)


I'd like to see an explaining description for each tag used in that
script. That's better than guessing.--[Duke](User:Duke "wikilink")
19:37, 3 December 2012 (SAST)

What are the planned features to extend that basic concept ?
--[Duke](User:Duke "wikilink") 21:09, 3 December 2012 (SAST)

## Questions/Concerns

### Sandbox vs Scripted Gameplay

This is my principle concern: how much randomness do you expect to be
possible in your system? How far do you want to go in scripting
missions? I agree that the current UFO/mission spawning system is very
complex and difficult to balance. I am in favor of a simplified system.
However, I believe that UFO:AI's greatest strength is it's sandbox
gameplay -- we don't force the player down a single path, we don't treat
the player too gently and tell them exactly what and when they should be
doing things. When a battle begins the conditions are as random as we
can make them within certain parameters (alien spawn positions,
sometimes map layout, alien equipment, alien AI -- all emerges in
unpredictable ways).

This is, IMHO, one of our greatest assets over the new XCOM. Our entire
game is built around the idea that when you play it a second, third,
fourth time you can not perfect your performance. Each time you play
you'll be presented with different problems. There is no "best" move in
any battle, no "best" research path, no "best" strategy. There are only
better and worse strategies, and this is largely a result of its
"sandbox" gameplay. We set some of the broader conditions, but the
player and the AI has very wide freedom within those conditions. This
means every time I play the game it's a bit different. This is important
to me. When I play most modern games my sense of victory is undermined
by the feeling that the game was carefully scripted to ensure I could
win. I like knowing when I play a game that everything could go horribly
wrong -- it's what makes me feel like I accomplished something when it
doesn't.

I am in favor of more scripting possibilities for the campaign, but your
example campaign makes me a little bit nervous. Here are a few specific
concerns: --[H-hour](User:H-hour "wikilink") 19:18, 3 December 2012
(SAST)

- Map selection: In the example campaign it seems like you choose
  exactly what maps are possible during any specific period. If we have
  50 maps (for example), I don't want to only have 10 maps possible at
  any one stage of the game. It would be nice to be able to hold a few
  maps back for special events (a major terror mission, for example),
  but I don't want the rest of my maps to be limited. I want it to be as
  random as possible, so story-elements like special missions or general
  balancing needs should intrude upon this as little as possible.
  - see the other two points - there is still randomness included.
    --[Mattn](User:Mattn "wikilink") 14:46, 6 December 2012 (CET)
- Mission locations: One of the best things about our UFO spawning
  system is that there is no clear pattern to where exactly events will
  happen. The UFOs spawn and fly and its up to the player to decide
  whether to let them land or not, when to engage them, and where to put
  his bases/radars to capture as many as possible. How does the scripted
  campaign handle the UFO appearance and flight mechanism? You appear to
  tie some missions to some specific cities.
  - This is still true for the ufo spawned missions (see below)
    --[Mattn](User:Mattn "wikilink") 14:46, 6 December 2012 (CET)
- Alien Interest: Every aspect of our campaign is configured according
  to alien interest at the moment. How can the scripted campaign
  interact with this?
  - The spawned ufos (and their missions that they spawned) still rely
    on the interest value - there is no change in the way we handle it.
    --[Mattn](User:Mattn "wikilink") 14:46, 6 December 2012 (CET)

Ok, so the UFOs still appear as normal. It looks like the scripted
campaign just defines a set of scripted missions which the player must
complete before moving to the next level. Now I guess I'm a little
confused. The scripted campaign keeps the hard-to-balance mission type
interest mechanism, the same unwieldy UFO selection criteria, and just
adds as a side element a few different map sets? If we keep the old UFO
appearance mechanism, what problems do you think the scripted campaign
will solve? In what ways will the scripted campaign be better?
--[H-hour](User:H-hour "wikilink") 18:50, 7 December 2012 (SAST)

And I know you're busy, but it would be really nice if you outlined in
more detail what your vision of the scripted campaign is. It's hard to
judge something in such an early state if we don't have a clear idea of
what it is supposed to look and act like when it is completed. In your
view, what were the problems with the old system? What new opportunities
will be available in your system? --[H-hour](User:H-hour "wikilink")
18:50, 7 December 2012 (SAST)

## Format description

[description](UFO-Scripts/staticcampaign.ufo‎‎ "wikilink")