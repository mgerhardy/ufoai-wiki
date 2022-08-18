## Introduction

This page will provide a brief description of how the game manages the
campaign. It is designed to be a base-line for further discussion among
the development team.

Version described: 2.5-dev

## Overview

The campaign is guided by an overall alien interest value that increases
at a set speed (standard: 1 alien interest value every 24 hours). Almost
all of the aspects of UFO spawning are guided by this overall alien
interest value, which is how we ensure that only certain UFOs, aliens
and equipment show up at certain times. This value is basically
equivalent to time, but we manipulate it via a campaign script variable
so that it increases faster on harder difficulties. In addition to the
overall alien interest value, the campaign tracks and modifies
individual interest values for each mission type (terror, harvest, etc).

Using these values in combination with the scripts, the campaign is
designed to slowly increase the frequency of UFOs, introduce more
powerful UFOs and more capable alien threats (aliens and equipment).
Aside from these parameters, the campaign has no mechanisms for
specifically targeting certain alien actions at certain moments in the
game. The aliens will not, for instance, stop running scouting or
harvesting missions at any particular time. We can use a hack to ensure
a given mission type does not occur too early (see below). And we do
control how the game adjusts the individual mission interest values (see
below). But we don't have a mechanism for scripting things like: run
lots of terror attacks during this period.

## UFO Number, Type and Mission Selection

Every n days, a new UFO mission spawn cycle begins. The game decides how
many UFOs to spawn during this cycle. Higher overall alien interest
values will lead to more UFOs, so that it increases over time. But the
curve is very gentle. Once it knows how many UFOs to spawn, it does
something to spawn them (I'm not sure if it spawns them all immediately
or spaces them out throughout the spawn cycle period).

With each mission, the game looks at the individual mission interest
values and spawns missions according to these values. I'm not sure
exactly how it makes this choice, but (in theory) it chooses mission
types with the highest interest levels.

When spawning a mission, the game attempts to locate a suitable UFO. A
harvesting mission, for example, may only use a harvester UFO -- see
/src/client/cgame/campaign/missions/\*
CP_\[missiontype\]ChooseAvailableUFOs. In some cases, a suitable UFO
can not be found because only the UFOs suitable to the selected mission
type are not yet available. Each UFO has a minimum overall alien
interest level that must be reached before it appears. If no UFO is
found, the mission is canceled. (This has a knock-on effect of making
fewer UFOs appear early in the game.)

The individual mission interest values are adjusted whenever an alien
mission is concluded. A successful base construction mission, for
instance, will raise interest in supply missions. Drawing conclusions
from these interactions is very difficult. I gave up trying to find some
way of estimating what would happen at different stages of the game and
how to make certain missions appear more later on. However, some rough
changes might be possible. For instance, all XVI missions could decrease
harvesting missions if we wanted them to go away later in the game. The
full adjustments are listed here:

`/* successful base attack */`
`   INT_ChangeIndividualInterest(0.3f, INTERESTCATEGORY_RECON);`
`   INT_ChangeIndividualInterest(0.1f, INTERESTCATEGORY_HARVEST);`
`   INT_ChangeIndividualInterest(-0.5f, INTERESTCATEGORY_TERROR_ATTACK);`
`   INT_ChangeIndividualInterest(-0.5f, INTERESTCATEGORY_INTERCEPT); `
`/* unsuccessful base attack */`
`   INT_ChangeIndividualInterest(0.05f, INTERESTCATEGORY_BUILDING);`
`   INT_ChangeIndividualInterest(0.1f, INTERESTCATEGORY_BASE_ATTACK);`
`/* alien base constructed */`
`   INT_ChangeIndividualInterest(0.1f, INTERESTCATEGORY_TERROR_ATTACK); /* only if it is a subversion mission */`
`   INT_ChangeIndividualInterest(0.4f, INTERESTCATEGORY_XVI);`
`   INT_ChangeIndividualInterest(0.4f, INTERESTCATEGORY_SUPPLY); `
`   INT_ChangeIndividualInterest(0.1f, INTERESTCATEGORY_HARVEST);`
`/* alien base mission failed */`
`   INT_ChangeIndividualInterest(0.5f, INTERESTCATEGORY_BUILDING);`
`   INT_ChangeIndividualInterest(0.05f, INTERESTCATEGORY_BASE_ATTACK);`
`/* alien base destroyed */`
`   INT_ChangeIndividualInterest(+0.1f, INTERESTCATEGORY_BUILDING);`
`   INT_ChangeIndividualInterest(+0.3f, INTERESTCATEGORY_INTERCEPT);`
`/* successful harvest mission */`
`   INT_ChangeIndividualInterest(-0.3f, INTERESTCATEGORY_HARVEST);`
`   INT_ChangeIndividualInterest(0.2f, INTERESTCATEGORY_RECON);`
`   INT_ChangeIndividualInterest(0.05f, INTERESTCATEGORY_BUILDING);`
`   INT_ChangeIndividualInterest(0.1f, INTERESTCATEGORY_XVI); /* only if XVI researched */`
`/* unsuccessful harvest mission */`
`   INT_ChangeIndividualInterest(0.1f, INTERESTCATEGORY_INTERCEPT);`
`   INT_ChangeIndividualInterest(0.03f, INTERESTCATEGORY_BASE_ATTACK);`
`   INT_ChangeIndividualInterest(0.03f, INTERESTCATEGORY_TERROR_ATTACK);`
`/* successful intercept mission */`
`   INT_ChangeIndividualInterest(0.3f, INTERESTCATEGORY_RECON);`
`   INT_ChangeIndividualInterest(-0.3f, INTERESTCATEGORY_INTERCEPT);`
`   INT_ChangeIndividualInterest(0.1f, INTERESTCATEGORY_HARVEST);`
`   INT_ChangeIndividualInterest(0.1f, INTERESTCATEGORY_XVI); /* only if XVI researched */`
`/* unsuccessful intercept mission */`
`   INT_ChangeIndividualInterest(0.1f, INTERESTCATEGORY_INTERCEPT);`
`   INT_ChangeIndividualInterest(0.05f, INTERESTCATEGORY_BUILDING);`
`   INT_ChangeIndividualInterest(0.05f, INTERESTCATEGORY_BASE_ATTACK);`
`   INT_ChangeIndividualInterest(0.05f, INTERESTCATEGORY_TERROR_ATTACK);`
`/* successful recon mission */`
`   INT_ChangeIndividualInterest(-0.2f, INTERESTCATEGORY_RECON);`
`   INT_ChangeIndividualInterest(0.1f, INTERESTCATEGORY_HARVEST);`
`   INT_ChangeIndividualInterest(0.1f, INTERESTCATEGORY_SUPPLY); /* if base exists */`
`   INT_ChangeIndividualInterest(0.1f, INTERESTCATEGORY_XVI); /* only if XVI researched */`
`/* unsuccessful recon mission */`
`   INT_ChangeIndividualInterest(0.05f, INTERESTCATEGORY_RECON);`
`   INT_ChangeIndividualInterest(0.1f, INTERESTCATEGORY_INTERCEPT);`
`   INT_ChangeIndividualInterest(0.05f, INTERESTCATEGORY_TERROR_ATTACK);`
`/* successful base supply mission */`
`   INT_ChangeIndividualInterest(-0.2f, INTERESTCATEGORY_SUPPLY);`
`/* unsuccessful base supply mission */`
`   INT_ChangeIndividualInterest(0.1f, INTERESTCATEGORY_SUPPLY);`
`   INT_ChangeIndividualInterest(0.1f, INTERESTCATEGORY_INTERCEPT);`
`   INT_ChangeIndividualInterest(0.05f, INTERESTCATEGORY_BASE_ATTACK);`
`/* successful terror mission */`
`   INT_ChangeIndividualInterest(-0.2f, INTERESTCATEGORY_BASE_ATTACK);`
`   INT_ChangeIndividualInterest(0.03f, INTERESTCATEGORY_HARVEST);`
`/* unsuccessful terror mission */`
`   INT_ChangeIndividualInterest(0.05f, INTERESTCATEGORY_TERROR_ATTACK);`
`   INT_ChangeIndividualInterest(0.1f, INTERESTCATEGORY_INTERCEPT);`
`   INT_ChangeIndividualInterest(0.05f, INTERESTCATEGORY_BUILDING);`
`   INT_ChangeIndividualInterest(0.02f, INTERESTCATEGORY_BASE_ATTACK);`
`/* successful XVI mission */`
`   INT_ChangeIndividualInterest(-0.3f, INTERESTCATEGORY_XVI);`
`   INT_ChangeIndividualInterest(0.1f, INTERESTCATEGORY_HARVEST);`
`   INT_ChangeIndividualInterest(0.05f, INTERESTCATEGORY_BUILDING);`
`/* unsuccessful XVI mission */`
`   INT_ChangeIndividualInterest(0.1f, INTERESTCATEGORY_INTERCEPT);`
`   INT_ChangeIndividualInterest(0.05f, INTERESTCATEGORY_TERROR_ATTACK);`
`   INT_ChangeIndividualInterest(0.01f, INTERESTCATEGORY_BASE_ATTACK);`
`/* once every day (increases interest in supplying base */`
`   INT_ChangeIndividualInterest(AB_GetAlienBaseNumber() * 0.1f, INTERESTCATEGORY_SUPPLY); `

## UFO Flight

All mission types have mission stages. They typically involve flying,
landing, and taking off, and I think in some cases the stage at which a
mission is ended (ie - shot down or something) may effect how it changes
individual mission interest values. In some cases I believe missions can
transform from one type to another at different stages. I'm not too sure
how this works.

## Map Selection

Maps are selected based on the culture, population and terrain values of
a scripted mapdef where the mission occurs. If the UFO landed in the
desert, it will get a mapdef that supports desert. For UFOs that are
shot down, this will depend on where it is shot down. Landed terror
missions always target cities (I believe). Some intercept missions will
just fly around looking for targets. Others will commence a base attack
or ground attack. Building missions attempt to build a base (and may
also try to turn a nation against you, not sure). Supply missions fly to
bases and disappear into them. I'm not sure how other mission types
(XVI/recon) choose their targets.

Maps are further checked according to UFO type. If a map does not
support the Harvester UFO, for instance, it will not be considered a
valid map for a mission with a Harvester. However, most of our static
maps which contain no UFOs are designed to work with all UFOs. Many are
configured to work with all culture and population values. This is
important to maintain map variety, for now.

## Special Events

We have a new events system to trigger specific events (see events.ufo).
This allows us to perform a command if certain conditions are met. This
is used to pop-up a few helpful messages (build a UFO yard, arm your
SAM, etc). It is also possible to allow certain things to become
researchable. The idea is to extend this.

In addition to this scripted events system, our end-game event is
hard-coded. When the player completes a research scripted to behave in
this way (Orbital UFO Activity), a new installation is built that allows
the player to fire at the carrier. When this happens, the game ends.

However, we don't at present have any way of using this events system to
spawn specific missions, such as a save-the-UN mission or something like
that.

[Category:Development](Category:Development "wikilink")