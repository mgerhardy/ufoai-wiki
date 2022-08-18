## Contributions

- Alien Base map
- MP/Skirmish maps (Training Zones Alpha and Bravo)

## Maintenance / Modifications

- Lots of textures to replace those without appropriate licenses
- Texture work on new Stiletto
  [:<File:New_Stiletto.jpg>](:File:New_Stiletto.jpg "wikilink")
- Map errors
- Weapon and campaign balance

## Work in Progress

- Completing Alien Base map
- Custom UI [TODO/UI2](TODO/UI2 "wikilink") and
- Weapon and campaign balancing for 2.5
- Web-based campaign viewer and data analyser

## Wish List / Proposals

- Improvements to multiplayer
  [TODO/2.5#Multiplayer](TODO/2.5#Multiplayer "wikilink")
- Visibility system, even one that starts simple.
  [Gameplay_Proposals/Visibility#Roadmap](Gameplay_Proposals/Visibility#Roadmap "wikilink")
- Better map selection
  [Proposals/Map_Definitions_Options](Proposals/Map_Definitions_Options "wikilink")

## Planned Projects

- Crashed Carrier UFO map
  [Storyline_Missions](Storyline_Missions "wikilink")
  [UFO/Carrier](UFO/Carrier "wikilink")
- Large city RMA. Have some ideas, but it's a big project that needs to
  be done right. Don't know when it will happen if it ever does.

## Personal 2.5 TODO list

- Campaign balancing

  - Check out Telok's save game to see when items were researched, how
    many UFOs were encountered, etc.

  - Schedule appearance of aliens, weapons and UFOs

  - Balance weapons and aliens; aircraft weapons and UFOs

    - Make sure each aircraft can compete and is worth buying when it is
      introduced

    - Adjust laser timing and damage

    - Check human armour resistances for balance with new campaign
      schedule.

    - Adjust alien team sizes and available recruits to match
      [staging](Proposals/Campaign_Staging "wikilink")

    - ShipIt: Is the transition from one stage to another to sudden?
      Should we smooth this by overlapping some interest settings in the
      alienteam_missions.ufo?

    - Check if aliens will use their stun grenade. If not, remove it
      from equipment sets.

    - Adjust XVI timing.

    - Adjust base building timing.

    - Particles and needlers

    - Rethink plasma pistol so it is not such a difficult reaction-fire
      weapon right at the start of the game.

  - Modify research tree paths

    - Add missing items

      - Alien Polymer Armour

      - Alien EW (craft item)

      - Advanced Alien Propulsion

      - Antimatter Bolter Ammo (model provided)

      - Hybrid Missile

      - Hybrid Rocket for RPG

      - [Encased Plasma
        Round](Proposals/Encased_Plasma_Round "wikilink")

    - Modify research times

    - Determine and implement proper storyline research paths

      - XVI map should not be available until rs_xvi_census is
        researched.

        - Does the XVI map appear too early? Check Universal Serum as
          well. User reported seeing it early.

  - Adjust disassembly times, volume of antimatter/alien materials
    received, and antimatter fuel costs for advanced
    interceptors/dropships.

    - Check profit margins on sale of antimatter/alien materials.

- Adjust equipment [weight
  values](Proposals/Equipment_Weights "wikilink")

  - Review alien weight/equipment and TUs

- Configure UFO spawning chances to average about 100 UFOs in 13 months.

- Give RMAs a mission briefing.

- Figure out how to change the equipment available in
  skirmish/multiplayer

  - That'd be equipment.ufo (equipment defs) + gamemodes.ufo (where to
    use what) I think --[DarkRain](User:DarkRain "wikilink") 20:43, 4
    March 2013 (SAST)
  - See:
  - Multiplayer initial has been done.
    --[H-hour](User:H-hour "wikilink") 22:57, 14 August 2013 (CEST)

- Check for possible weight system exploit: if a soldier drops a heavy
  weapon at the end of the turn, then picks it up at the start of the
  next turn, can they gain TU that way? Might be hard with armour to
  make it meaningful, but might be possible.

  - Exploit exists. But how do we get around it? Should it cost more TU
    to pick something up? In my experiment, I had a guy just at 20+%. I
    dropped a laser rifle and got the speed bonus next turn. First turn:
    31 TU. Second turn: 42 TU. If you subtract the TU it cost to pick up
    the weapon, then he gained 9 TU from the exchange. That means we'd
    have to increase the cost of picking something up to 11 TU to cancel
    out the bonus. That seems pretty high... but I guess the act of
    picking something up isn't used a ton. I guess it would be most used
    for medikits, maybe rockets for the RPGs...

    - One possible (but perhaps confusing) workaround. If a soldier
      picks up an item that bumps him from one encumbrance level to
      another, maybe have him lose/gain the same proportion of TU in the
      middle of the turn but just for his remaining TU. So, if I've got
      the TU bonus and I've already spent half of my TUs, then pick up a
      weapon that makes me "normal" encumbrance, half the percentage TU
      effect the remaining half of my TUs. It could work in reverse as
      well. If I have half of my TUs and drop a weapon that takes me
      from "normal" to "fast" weight, I will gain the percentage TU
      effect of my remaining TUs.

- Could we have an airburst mode for the RPG? Would that make it much
  more useful?

- Bolter's high TU cost and low ammo count makes it extremely difficult
  to use. Increase accuracy more to make the trade-off worth it.

  - Look into coilgun as well, and its trade-off with the Sniper Rifle
    with Encased Plasma.

- Revert intra-weapon firemode differentiation between assault/sniper.
  Assault weapons always assault, Sniper weapons always sniper.

- Also revert crouch penalties in all cases. (Make sure MG isn't the
  only one)

- Maybe we could use the Gunboat UFO for a wider range of mission types.
  Right now it´s only used for Intercept missions.
  --[ShipIt](User:ShipIt "wikilink") 09:57, 8 June 2013 (CEST)

- In my campaign the ammo for PB-Rifle and PB-Pistol are available at
  the market at late stage. As we cannot produce it, this shouldn´t
  happen, should it? --[ShipIt](User:ShipIt "wikilink") 13:41, 8 June
  2013 (CEST)

## Items delayed to 2.6

- Production/Market Balance

- Transfer worldspawn values to UMP files for as many RMAs as possible.

- Add crashed ufo tiles and use new tile reference system

  - Check on gunboat status

  - Enough corrupter tiles?

- Players often complain about getting recruits with "mediocre" or
  "poor" stats. Maybe we should change those descriptions to something
  more positive, or even entirely remove them.
  --[ShipIt](User:ShipIt "wikilink")
  ([talk](User_talk:ShipIt "wikilink")) 07:05, 17 June 2014 (CEST)

[Category:UFO:AI Team](Category:UFO:AI_Team "wikilink")