The stuff in *General* is not assigned to a specific version.

**But please do only commit stuff to trunk if it's no major change. If
it is please ask a project manager before doing that.**

## Artwork

### 2D artwork

- Alternate skins for existing civilians, scientists, pilots, etc.

- We need normalmaps, specular maps, glow maps, etc. for a lot of our
  existing artwork. See [Artwork](Artwork "wikilink") for more details
  and use the forums to coordinate work.

- Alternate skins for 'crashed' aircraft.

### 3D models (other than maps)

- We need various character models that are animated

  - Several soldier models with a unified style, in several different
    armors. [TODO/Soldier_Models](TODO/Soldier_Models "wikilink")

  - Civilians in all shapes and sizes

  - Alternate scientists' models/heads

  - Small 1x1 robot to be used as a scout drone

  - New aliens with animations
    [Proposals/Alien_Bestiary](Proposals/Alien_Bestiary "wikilink")

- [Aircraft/Hyperion-class_Armed_Dropship](Aircraft/Hyperion-class_Armed_Dropship "wikilink")

- 'crashed' versions for the already existing aircraft models,
  essentially cutting the model into parts and making each part a
  seperate model

- Human-Alien Hybrid Missile (as aircraft weapon, I think)

- We must find GPL'd replacements for a few models with UNKNOWN
  licenses. .

### Maps

- Maps for [Storyline_Missions](Storyline_Missions "wikilink").

- New map themes and more tiles for
  [Mapping/List_of_Maps](Mapping/List_of_Maps "wikilink") existing
  themes. [Mapping/Suggestions](Mapping/Suggestions "wikilink") See
  suggestions.

### PHALANX craft

- [Hyperion](Aircraft/Hyperion-class_Armed_Dropship "wikilink"): Model,
  article, scripts.
- [Herakles](Aircraft/Herakles-class_Heavy_Lifter "wikilink"): Article,
  remove 8 soldier limit, scripts.
- [Raptor](Aircraft/Raptor-class_Combat_Transport "wikilink"): Article,
  finish , scripts.

## Equipment interface and team handling

- equip screen before mission start, after map load, which will allow to
  adjust soldiers' equipment after reading mission briefing

## Map code

- code to spawn a light on the map, which will be used for example with
  flares

  - That code is already there - spawn a server side edict that will
    spawn a particle for each client where at least one actor can see
    this edict. you can also use some triggers to use touch functions
    (to be able to execute different actions as soon as an actor enters
    a given grid field) --[Mattn](User:Mattn "wikilink") 19:41, 17
    August 2008 (UTC)

- nextmap mission trigger (to immediately start new map after
  "finishing" first one) - useful for situations where we need to have a
  mission with more than 8 levels

- Code to allow aliens and humans to destroy cameras placed in the
  battlescape.

## LUA driven AI

- find targets

- shoot targets

- handle approaching far away enemies or when enemies are not seen

- better grenade handling

- hiding

- civilian ai

## Music & Sounds

- Atmospheric background noise for the missions (the more the better)

- New music tracks for the geoscape and the battlescape

- Replace sounds from this with [gpled](License "wikilink") ones

## Code

- [XVI](TODO/XVI "wikilink") Incorporate overarching XVI system.
- [Map ladders](TODO/ladder "wikilink") Code and model changes to allow
  using ladders on maps

<!-- -->

- mission briefings at mission selection (to re-equip soldiers and
  decide whether you want to do that mission or not BEFORE you send your
  craft)

- Generate soldier names depending on their nation of origin. Change
  team_humans.ufo so it defines names per nation rather than per class.
  --[Cmdrquan](User:Cmdrquan "wikilink") 23:11, 15 February 2008 (EDT)

  - Taking a second approach to
    [CharacterGeneration](TODO/2.3/CharacterGeneration "wikilink")--26,
    February 2008

- Proposed: Knockdown effect for very damaging hits.

- Code to handle Alien Containment behaviour during base defence
  mission - based on difficulty, aliens stored in containment should get
  free in certain situations and participate in the battle; i know more
  what to do and how, but this is a long-term
  task--[Zenerka](User:Zenerka "wikilink") 12:07, 22 January 2007 (CET)

- Multiplayer: (proposed) [Point-based setup
  system](ReactionFireImprovements "wikilink").

- (Proposed) [Changes to reaction
  fire](ReactionFireImprovements "wikilink").

- [Support for 2x2 units](TODO/General/Support_for_2x2_units "wikilink")
  such as Phoenix, Triax, Hovernets/Floaters, etc...

### Equipment

- extension container

- fix/finish equipments

  - fuel pod (aircraft)

    - reduces the operational range instead of increasing it

    - can be equipped to antimatter powered craft and works on it

### Inventory to team assignment

- each object that can wear, use, store items should get its own
  equipment container (that is NOT related to a global linked list)

- capacity can be calculated for each of the above mentioned equipment
  container because the all use the same data structure just with a
  different size

- inventory templates

  - allow to save current soldier inventory as a template

  - allow to equip soldier by picking desired template from the list;
    when doing that check if the items exists in base storage, block
    usage of template if no items for hands in base storage

- unhiring soldier

  - readd inventory to base storage

  - if the storage inventory is full at any point in the unhiring
    processed, drop any remaining items that are not already stored.

- beginning a mission

  - soldiers can reequip themselves by using items from aircraft
    equipment container - but this costs TUs when we are already in the
    tactical mission

  - open inventory menu for aircraft before entering a mission (button
    to do this in mission brief screen)

- dropship returns to the base

  - reload soldiers' weapons (check for item.a, check if such clip is in
    base storage, reload)

- destroying an aircraft will destroy its storage as well - as it's an
  equipment container that is stored in the aircraft_t data

- adding items to aircraft storage updates aircraft capacity - do not
  allow to put too many things to aircraft (see the above mentioned
  capacity function for all the equipment containers)

### New equipping menu code

- Soldier equip menu should not be dependent from any aircraft -
  equipment should be stored at the soldier and thus only the soldier is
  needed to equip him (and the storage equipment container of course)
- Additional option for transfer menu: transfer soldier to another base
  with (default) OR without equipment assigned to this soldier (just
  move the soldiers equipment container back into the base the soldier
  is currently in, or the aircraft the soldier is currently assigned to
  \[if any\] in case the base equipment container is full).

### Interface add-ons

- \[low priority\] Tooltip action with content based on specific values,
  when moving cursor on the specific node; it could be used in various
  situations, few examples:
  - Moving cursor to the ammo in inventory menu shows tooltip with names
    fo the weapons that use this ammo ... vice versa for weapons. As
    long as the weapons are researched that is.

  - Moving cursor to the hire button (of the employee already hired in
    another base) in hire menu shows tooltip the base where this
    employee is hired.

  - Moving cursor to the reaction fire button in HUD shows tooltip
    informing which weapon and which firemode will be used.

  - Moving cursor to the button "next entry" in UFOpedia shows the name
    of the next entry, same for previous entry.

  - Moving cursor to the reload button in HUD shows tooltip informing
    about the amount of TU needed to reload.

- Rework the input system to allow user-configurable key combinations
  (such as shift+key or control+key). Currently, they have to be
  hardcoded.

- Allow the user to change key bindings in the game menu, rather than
  having to edit keys.cfg.

### Pathfinding and Tracing

- Support hovering/flying units

- Support areas that are only reachable when crouching

- Support more accurate model tracing to determine pathfinding

- Support accurate pathfinding for 2x2 actors

## Other

- Psionic warfare

- Add support for item- and building-upgrades. \<Suggested by
  [Winter](User:Winter "wikilink")\>

- Unmanned recon/spy drones that search for alien activity. You'd simply
  pay X credits to send a UAV drone out to check for UFOs and alien
  bases and such. \<Suggested by [Winter](User:Winter "wikilink")\>

- Pilot management (pilot skills) -- [Malick](User:Malick "wikilink")

- "civilian" teams, which can fight against aliens, like soldiers

- knockdown effect for very damaged soldiers

- Incorporate UFO_CONDOR ([UFO -- Corrupter](UFO/Corrupter "wikilink")
  to the game - we already have model and one map with that UFO

- Incorporate flare (base/models/weapons/flare/) into the game (scripts
  entry, UFOpaedia article)

- Add [tutorials](tutorials "wikilink")

## Installer

- add UFO:AI to the game-explorer for windows vista - see for
  [nsis](nsis "wikilink") for more information

This version is mainly point of discuss but we need some points to start
it.

## Misc decisions from developers

- Marketsystem (should work like transfers)

- finish UFO-Yard support
  - selling already stored UFOs: Need to rework UFO selling to avoid
    cheating

- Destroyable bases: PHALANX bases should be destroyable
  - refactoring structures needed, I have some progress on it in a local
    branch

- implement Pilot skills (finish patches from Malick, @see patch)

- UGV support

- [UFO-Gunboat](UFO/Gunboat "wikilink"): We have tech- and ufopaedia-
  entries for this UFO. Also we have draft model of the craft.
  - Prefab-model
  - geoscape model
  - Crashed prefab
  - Tune scripts
  - incorporate to the existing RMAs
    ([Status](TODO/Mapping/Crafts_Tiles "wikilink"))

- Incorporate Alien Launcher & Antimatter missile to campaign
  - Alien Launcher model

  - Alien Launcher writeup

  - Antimatter Rocket model

  - Antimatter Rocket geoscape model

  - Antimatter Rocket writeup

  - Hybrid Launcher model

  - Hybrid Rocket model

  - Hybrid Rocket geoscape model

  - Hybrid Rocket writeup

  - scripts

- Decision: currently base storage sizes for craft items and soldier
  items are not much different. Do we want to change this? If so, we
  need to take a look at how it will effect campaign storage limits and
  make sure we re-balance appropriately.

- Add equipment scores for all equipment to be used in autoresolve

- Make shooting down a Carrier UFO the end of the game

  - Complete tech tree

  - Develop a mechanism in the geoscape for firing at the Carrier when
    research completed (automatically placed installation?), or just
    automatically fire at the Carrier.

  - Tech image

  - Crashed Carrier icon for geoscape

## Things to think on

- Campaign: we ought to move our campaign forward. What do we need to do
  for this?
  - Research topics and research entries?
  - New maps?
  - New missions and missions type?
  - XVI?
    - What do we need to include XVI-infected humans as enemies?
      ([Translation:Enemy_on_earth_txt/en](Translation:Enemy_on_earth_txt/en "wikilink"))
  - New UFO\`s?
- Lua-based AI: It is broken currently and there is no active
  maintainer. We should decide, kill it or bring back to live?
  - It's not broken, it's simply not
    implemented--[Duke](User:Duke "wikilink") 23:29, 5 April 2012 (SAST)
- Whole efficiency and perfomance of the game.
- Current work in the branches (like renderer branch). Is they still
  alive? Is they still able to compiled?
- Should we begin working towards a visibility sytem? See the
  [roadmap](Gameplay_Proposals/Visibility#Roadmap "wikilink").
- …

## Multiplayer

We should improve the overall multiplayer experience in the hopes of
growing at least a small multiplayer community. A good multiplayer game
could increase development participation (at least for maps). Here are
some steps that I (H-Hour) think could help:

- Better organization and selection of maps to allow players to find
  MP-appropriate maps more easily.
  - Improve mapcycle.txt as a temporary fix
  - [Changes to maps.ufo
    definitions](Proposals/Map_Definitions_Options "wikilink") to allow
    categorization by recommended game types, map construction
    (static/dynamic), size, etc.
  - UI that supports selecting a theme and then the different available
    parameters (see changes to map.ufo definitions above). It should
    also allow the player to view only maps for the parameters they
    select (size, gametypes, fixed or random assembly, etc).

- Maps designed for properly balanced multiplayer games. These are
  typically static maps, but we could also create fixed assemblies
  designed exclusively for multiplayer.

- Support for new game types (domination, alien rush, king of the hill
  implemented).
  - see
  - Game types will also need UI improvements to be done well: score
    counters, turn numbers, etc.
    - see

- Changes to weapon selection
  - Clean up the equipment set selection process as described here
    [proposed here](Proposals/Skirmish/MP_Equipment_Sets "wikilink").
    Ideally, it would be nice if a host could create and save custom
    equipment sets that could be used when hosting.
  - A nice addition, but maybe for post-2.5: allow a host to set a
    credits-limit in addition to the equipment set. Each item would cost
    the player credits and he would be forced to limit his selection.
    This would allow a host to (for instance) allow any type of weapon
    but prevent the player from equipping only the best items (because
    he can't afford it).

- Small changes:
  - Rotate turn order from one map to another so the same player's do
    not always start first
  - Implement a bar that shows the time remaining in a turn and
    decreases each second.
    -
  - Make some MP-specific information available on UI:
    - How many soldiers of each team are left alive
  - Message log of events in battlescape (not just multiplayer)

## Balancing

- Weapon balancing

- Nation happiness: some complaints that nations go unhappy too quickly
  in early game. Test and, if verified, improve.

- Consider switching order in which shevaar and ortnoks appear in
  campaign

- Work out a way to scale the number of aliens based on the size of the
  map

- Campaign balancing, including new aliens, research items, alien teams,
  equipment, weapons research times, disassembly times, alien materials.

## Artwork

## Maps

- Alienbase theme

- +hills (The assembly needs more tiles and remaining ufos)

- early- +railroad

- +harbour2 (it needs to be finished and polished before including to
  the campaign)

[Category:Contribute](Category:Contribute "wikilink")
[Category:TODO](Category:TODO "wikilink")
[Category:Development](Category:Development "wikilink")