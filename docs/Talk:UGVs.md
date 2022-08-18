This page is meant to discuss the best way of implementing UGVs in
UFO:AI

## Models

- Currently the UGV models are incomplete, they don't have a weapon
  mount tag yet. The non-UGV models all have a **tag_rweapon** and
  **tag_lweapon**, and the code assumes they're present for each actor.
  But for UGVs it doesn't make sense to use hands (although the same
  tags could be used).

- Separation of turret and frames

- Animations, including turret rotation and barrel inclination, death,
  movement, etc.

## UI

- There needs to be an equip screen for UGVs, similar to but different
  from soldiers. I propose at least 3 'equip areas' :

  - the weapon, similar to a soldiers hand
  - the invisible armour area, similar to a soldier, but probably bigger
    - Should UGVs have changeable armour? My opinion — they should have
      only changeable weapons, not armour. May be they should have only
      one type of weapon by UGV-type, like it was in first X-Com\`s.
      --[Kildor](User:Kildor "wikilink") 15:36, 12 February 2012 (CET)
  - a storage area for ammo
  - optional 2nd weapon

- Be able to make a combined team. Currently in multiplayer you select a
  UGV race, so only UGVs can be in the 'soldier' list. But I see no
  problem combining those in a single list, allowing only to add a UGV
  when there's space (so 4 soldier spots can fit 1 UGV). The UI should
  then be able to show the right equip screen when one of the list is
  clicked, and show a different set of weapons, ammo and armour to fit.

## Market

- UGV section

  - market already supports UGV, I'm reimplementing the UI for the
    market now, I need some info about the UGV's equipment to do it
    correctly. --geever 2012-03-18

## Maps

- Not all the maps have 2x2 spawnpoints. It will be needed to test
  pathfinding to have at least one point per map.

  - Each map has at least three 2x2 spawnpoints (Team 1, humans) for
    now. --[ShipIt](User:ShipIt "wikilink") 16:04, 19 April 2012 (CEST)

- Is there a minimum for the number of 2x2 spawnpoints for all maps ? A
  maximum ? If so, how do we transport that information to the equipment
  screen? Or do the 2x2 actors stay in the dropship when no spawnpoint
  can be found?
  - If a dropship can bring ten UGVs into battle, we need to have ten
    spawnpoints, right? For this, we need a decision whether the player
    can replace four soldiers by one UGV or not. The minimum number then
    is given by the design of the dropship, the maximum only depends on
    how much room is on the map. --[ShipIt](User:ShipIt "wikilink")
    16:04, 19 April 2012 (CEST)

## Code

- UGV datastructures and entity definitions? Now they're a 'subclass' of
  employee.

- The code assumes two hands/weapon slots. It needs support for just 1
  gun.

- Each non-UGV actor has tag_rweapon and tag_lweapon present. UGVs
  don't. We need to make this dependent on the type of actor we're
  dealing with.

- Pathfinding support for 2x2 units. This is at least partly done -
  what's the status?

- weapon inclination limits? When a UGV is going up/downhill, it might
  not be able to fire along the horizontal plane

- Alien UGV routing and strategy.

- Do UGVs gain experience?

## Milestones

- phase 1 (skirmish basic)
  - only skirmish, no campaign support yet
  - only looking at 2x2 actors
  - At least one of Ares W or Phoenix UGV has weapon mount tag, and
    fires from correct point of origin
  - no turning turret
  - correct routing, UGV is limited to where it physically can go
  - no alien AI support for UGV
- phase 2 (skirmish extended)
  - only skirmish, no campaign support yet
  - mixed teams, so do away with UGV 'race'. Instead allow replacing 1
    or 2 soldiers (rules?) with 1 2x2 UGV.
  - add turret control. Turning will take actor dependent TUs, and is
    possibly animated.
  - UI polishing of UGV capabilities.
    - remove crouching
    - 'hand switch' optional, dependent on actor capabilities.
  - Tune UGV hitpoints, TUs, strength, accuracy, storage, in multiplayer
    combat. Create 'personality' of the Ares W and Phoenix
  - Tune UGV tank weapons in multiplayer combat
  - Limit weapons UGV can wield.
- phase 3 (campaign basic)
  - mixed teams, limit rules for \# of UGVs/soldiers
  - dropship assignment, UGV equipment
  - changes to scoring, autoresolve, experience, summaries, etc.
  - UGV market
- phase 4 (full support)
  - 2x2 spawnpoints on all maps
  - Tune game balance. Alien AI w.r.t. phalanx UGVs, offset UGV strength
    vs. weakness (i.e. less soldiers, not all maps allow UGVs to go
    everywhere etc)
- future
  - Alien UGVs
  - flying units

## See Also

Additional pages where UGVs are discussed

- Wiki
  - [User talk:Duke](User_talk:Duke "wikilink")
  - [TODO/2.5](TODO/2.5 "wikilink")
- Forum
  -

## Mixed team.

Should UGVs use the same capacity pool as human team? If I remember
things right, the UGV is used some sort of lamps, and do not shown on
dropship model. --[Kildor](User:Kildor "wikilink") 15:51, 12 February
2012 (CET)

[Category:TODO](Category:TODO "wikilink")