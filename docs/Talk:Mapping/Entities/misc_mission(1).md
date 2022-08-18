## General

- \[\]
- Having this feature would help in many ways:
  - We could have something other than "kill all aliens" in our
    missions.
  - A second way to win could shorten some missions for the player.
    There are often complaints about very long missions on maps like
    'Mansion' or base defence missions, where people crawl through huge
    maps searching for the last single alien. Those missions could be
    won by the player securing some 'key points' of the map for long
    enough.

## Q&A

- If 'radius' is given, does this count only horizontally or is it meant
  to be a sphere? --[ShipIt](User:ShipIt "wikilink")
  ([talk](User_talk:ShipIt "wikilink")) 11:23, 26 July 2015 (CEST)
  - Horizontally only, and it results in a **square** not a circle as
    the name radius might suggest.
    --[DarkRain](User:DarkRain "wikilink")
    ([talk](User_talk:DarkRain "wikilink")) 22:05, 26 July 2015 (CEST)
- We have a message property for the misc_mission, what should we do
  with it? (Currently it does nothing at all) Should we go with the
  description and show it upon victory? Or we could use it to fill the
  mission briefing with objectives (might be difficult to code as we
  aren't assigned a team until the mission starts), we could also use to
  have a message to display somewhere on the HUD (along with a turns
  remaining count if applicable) --[DarkRain](User:DarkRain "wikilink")
  ([talk](User_talk:DarkRain "wikilink")) 16:55, 1 August 2015 (CEST)
  - Showing a message if the player won the mission by achieving the
    objective given in the misc_mission (instead of killing all
    opponents) would oc be nice. It could also be used to show a message
    upon entering the target zone (instead of the default one from the
    code). This might be more practical, in case of multiple mission
    objectives, and if I could have only one of them, I´d take this.
    --[ShipIt](User:ShipIt "wikilink")
    ([talk](User_talk:ShipIt "wikilink")) 10:15, 2 August 2015 (CEST)
- Giving the player the information he needs might be a task of its own.
  So, what information should the player get and how do we display them?
  --[ShipIt](User:ShipIt "wikilink")
  ([talk](User_talk:ShipIt "wikilink")) 10:15, 2 August 2015 (CEST)
  - Whatever it is, in order to show usefull info, we need to identify
    the misc_mission somehow. --[ShipIt](User:ShipIt "wikilink")
    ([talk](User_talk:ShipIt "wikilink")) 10:32, 2 August 2015 (CEST)
    - So we need to give them a name? --[ShipIt](User:ShipIt "wikilink")
      ([talk](User_talk:ShipIt "wikilink")) 10:32, 2 August 2015 (CEST)
  - My best idea right now is to have a info screen showing a table.
    This table would identify the mission targets in the map by name and
    description, and show their current state. Oc this would require to
    add some properties to the entity ('name' and 'description'). The
    'message' could then be shown once the objective is achieved.
    --[ShipIt](User:ShipIt "wikilink")
    ([talk](User_talk:ShipIt "wikilink")) 11:32, 24 August 2015 (CEST)
    - I guess adding a couple properties to the entity shouldn't be that
      bad, and will make thing less confusing
      --[DarkRain](User:DarkRain "wikilink")
      ([talk](User_talk:DarkRain "wikilink")) 22:31, 9 September 2015
      (CEST)

<!-- -->

- To both of the above points: Should we consider multi player
  implications here (messages/info we show the player will likely need
  to be different from single player) or should we leave that for a
  later time? --[DarkRain](User:DarkRain "wikilink")
  ([talk](User_talk:DarkRain "wikilink")) 20:20, 4 August 2015 (CEST)
  - Taking mp into account would really complicate thing a lot, so I
    would simply treat the misc_mission as campaign-only for now. E.g.
    there might be spawnpoints for up to six mp-teams in a map. The team
    numbers are given randomly to 2 - 4 teams, so in the map there might
    be no Team 1. Not sure how to solve this. The player would not even
    know about his team number. --[ShipIt](User:ShipIt "wikilink")
    ([talk](User_talk:ShipIt "wikilink")) 11:32, 24 August 2015 (CEST)
- After winning the mansion map, the victory screen marked two alien
  survivors, but only one alien came to the Containment (I assume it is
  the one that got stunned during the mission). Should not they all be
  dead? In case the players loses, his soldiers are all considered to be
  dead, no? --[ShipIt](User:ShipIt "wikilink")
  ([talk](User_talk:ShipIt "wikilink")) 11:49, 24 August 2015 (CEST)
  - Well depends on how we want to handle the results of a non standard
    victory, which depends on the kind of mission, it might be that
    surviving not stunned aliens are considered to flee the area — in
    which case we would get to keep the stunned aliens, in other cases
    one could say that PHALANX goes in meet the objective and then pull
    out — in which case all alive aliens should be considered survivors
    and we wouldn't keep stunned ones, we could also say PHALANX rounds
    all surviving aliens and... does what? Subdues and captures them,
    kills them all? In the case of the player soldiers, originally there
    was a count of soldiers missing in action, of course it was always
    0, as all soldiers left alive when the player loses a mission are
    killed by the game (except those at the rescue zone if you abort the
    mission) again what should we do in the case of an alien
    non-standard victory consider surviving soldiers MIA, KIA or even
    have them flee depending on the mission?
    --[DarkRain](User:DarkRain "wikilink")
    ([talk](User_talk:DarkRain "wikilink")) 22:31, 9 September 2015
    (CEST)
    - As we can always adjust this later on, I'd propose this approach
      as a start. --[ShipIt](User:ShipIt "wikilink")
      ([talk](User_talk:ShipIt "wikilink")) 08:13, 9 February 2017 (CET)
      - Player wins - Alien survivors get killed, civilian survivors are
        saved, player gets all alien equipement and UFO.
      - AI wins - Surviving human soldiers, pilot and civilians KIA,
        dropship lost. Mission disappears from geoscape.

## Goals

- Make this feature work in campaign as the description implies, and use
  it within the maps. --[ShipIt](User:ShipIt "wikilink")
  ([talk](User_talk:ShipIt "wikilink")) 11:06, 26 July 2015 (CEST)
  - If only a 'target' is given, destroy it once the conditions are met.

    - "Occupy area to destroy target."
    - Right now, this destroys the target AND wins the mission, which
      makes no sense.
      - Should be fixed now, if a target is given it won't cause you to
        win the mission. --[DarkRain](User:DarkRain "wikilink")
        ([talk](User_talk:DarkRain "wikilink")) 16:47, 1 August 2015
        (CEST)

  - If only an 'item' is given, win the mission once the conditions are
    met.

    - "Bring item to win mission."

  - If a 'target' and an 'item' are given, destroy the target once the
    conditions are met.

    - - Note: Default radius if none given for misc_mission is three map
        grid wide (always was that way, it's just that before a bug
        prevented it from being correctly set and all misc_mission ended
        being one grid wide) this might not give the intended results
        see for example fueldump with the fixed code (the item will be
        placed upon entering the area — a few steps before reaching the
        door) --[DarkRain](User:DarkRain "wikilink")
        ([talk](User_talk:DarkRain "wikilink")) 06:38, 29 July 2015
        (CEST)

    - "Bring item to destroy target."

    - This is used in fueldump map and already works.
      - Note that (if I read the code right) if this is the only
        objective in the mission this will win the mission too
        --[DarkRain](User:DarkRain "wikilink")
        ([talk](User_talk:DarkRain "wikilink")) 06:31, 29 July 2015
        (CEST)
        - No longer the case --[DarkRain](User:DarkRain "wikilink")
          ([talk](User_talk:DarkRain "wikilink")) 16:47, 1 August 2015
          (CEST)

  - If none of the above paramters is given, win the mission once the
    conditions are met.

    - This works, but with civilians around it doesn´t. See = Bugs =
      section below. --[ShipIt](User:ShipIt "wikilink")
      ([talk](User_talk:ShipIt "wikilink")) 07:16, 28 July 2015 (CEST)
    - "Occupy area to win mission."

  - Status report window.

    - As an overview for the player, I propose a gui element that can be
      opened (like inventory or soldier stats window). This should show
      a table which contains the **targetname**, **group**, **team**
      properties and current status (either "Occupied", "Open" or
      "Contested") for each mission target on the map.
      --[ShipIt](User:ShipIt "wikilink")
      ([talk](User_talk:ShipIt "wikilink")) 09:36, 9 February 2017 (CET)
      - There's more than one mission type, you know? So this might not
        be an easy task. --[ShipIt](User:ShipIt "wikilink")
        ([talk](User_talk:ShipIt "wikilink")) 09:36, 9 February 2017
        (CET)

  - Depending on the type of the mission, a status needs to be
    determined. --[ShipIt](User:ShipIt "wikilink")
    ([talk](User_talk:ShipIt "wikilink")) 09:52, 9 February 2017 (CET)

    - status = triggered - "Occupied"
    - status = blocked - "Blocked"
    - status = untriggered and not blocked - "Open" (or maybe "Free"?)
    - status = triggered and blocked - "Contested"

## Current state

- As given by DarkRain:
  - ... in theory there are the "bring object", "occupy area" and
    ~~"destroy object"~~ objectives available ...
  - The AI actually already takes misc_mission into account in its
    calculations.
  - All objectives must be accomplished to win the mission.
    - This is not yet the desired behaviour. It should be enough to
      reach one of the given goals, unless they are grouped together.
      --[ShipIt](User:ShipIt "wikilink")
      ([talk](User_talk:ShipIt "wikilink")) 11:56, 26 July 2015 (CEST)

<!-- -->

- - The AI moves to the general area of a misc_mission — within a
    predefined radius of the entity, which, depending on the radius
    assigned to the misc_mission (if any), might not be close enough to
    activate the objective.
  - The AI doesn't know how to handle the 'bring object' type
    misc_mission at all.

<!-- -->

- Need to check each possible mission type to confirm current state.
  - mission type "Occupy area to win mission."

    - Mandatory keys set to default, team, message and targetname
      properties set. Item and target properties are not set.
      - Works as expected, but ignores the radius (only works if
        standing in the trigger spot).

      - Alien team

        - Had a case where the alien stood next to the trigger, ending
          in an infine loop. Game was still responsible, can move camera
          around, open inventory and such. Could not reproduce this so
          far.
        - Often the alien ends the turn standing next to the trigger and
          nothing happens (radius set to 3), finally alien ends at the
          spot in the trigger and the mission ends as intended.

## Known problems

- The fact that the AI can only plan for their current turn, they will
  have all kinds of trouble trying to path to anything that is beyond
  their TU's.

<!-- -->

- It was reported that winning a mission this way resulted in an overall
  loss in nation happyness. We need to look into this and make sure
  mission targets are a valid way to win a mission.
  --[ShipIt](User:ShipIt "wikilink")
  ([talk](User_talk:ShipIt "wikilink")) 06:47, 9 February 2017 (CET)

## Bugs

- In my testmap it works fine, but adding a civilian breaks it.
  --[ShipIt](User:ShipIt "wikilink")
  ([talk](User_talk:ShipIt "wikilink")) 17:01, 27 July 2015 (CEST)
  - It actually works, but there's a catch: If anyone from any team
    other than the target team enters the area the turn counter is
    reset, I'm guessing the idea was that if so the area is considered
    contested instead of occupied, we could probably use an exception
    here for non hostiles --[DarkRain](User:DarkRain "wikilink")
    ([talk](User_talk:DarkRain "wikilink")) 06:07, 29 July 2015 (CEST)
    - Furthermore if someone from other team enters the area of a 'bring
      object' mission the counter will also be reset! Which might or
      might not make sense (I still consider it a bug), in any case we
      also need to add a message to the player that they have lost
      control of the area, instead of silently resetting the counter
      --[DarkRain](User:DarkRain "wikilink")
      ([talk](User_talk:DarkRain "wikilink")) 06:29, 29 July 2015 (CEST)
      - Resetting the counter might not make sense in case of a 'place
        bomb to destroy gate' kind of mission. But I think this will
        rarely happen in game, because the radius will be small and the
        player should usually control the area around the mission
        target. So I am not sure if it is worth the effort to find/do a
        better solution for this. About the messages - what happens if
        there is more than one mission target? The player will have a
        hard time to find out where he is in control and where not.
        --[ShipIt](User:ShipIt "wikilink")
        ([talk](User_talk:ShipIt "wikilink")) 21:26, 30 July 2015 (CEST)

## Next step

- We need to give the player more usefull information about what is
  going on.
  - status report for mission type "occupy area"

    - At beginning of the round, we give the status of each mission
      target.
      - "Team **team** target **targetname** (of **group**) is currently
        occupied/open/contested."
      - "Team **Alien** target **Firebird Dropship** is currently
        contested."
      - "Team **Phalanx** target **Entrance** of **Alien base important
        locations** is currently open."

  - status update for mission type "occupy area"

    - Whenever the status of a mission target changes, we inform the
      player.
      - "Team **team** target **targetname** (of **group**) changed
        status from \[former status\] to \[new status\]."

## Obsolete

- Make the "occupy area" feature work for all teams. So, if a team
  reaches one of the given objectives, it wins the mission.
  - Provide some maps using this feature. This should aim for testing in
    the first place and maybe getting feedback. We can decide whether to
    keep them or not later on.
    - Imo the best map for this is the baseattack map. Aliens should try
      to reach either the Power plant, Antimatter storage or Command
      centre and blow up the base. Players are forced to play those
      missions, so we get feedback? --[ShipIt](User:ShipIt "wikilink")
      ([talk](User_talk:ShipIt "wikilink")) 11:06, 26 July 2015 (CEST)
      - This is probably the best use we can make of misc_mission right
        now, giving the aliens some threatening objectives in base
        attacks is long overdue IMHO, and we'd get the much needed
        feedback on this feature, but of course this will need to deal
        with the AI pathing problem if we are to see any real effects
        here --[DarkRain](User:DarkRain "wikilink")
        ([talk](User_talk:DarkRain "wikilink")) 04:58, 27 July 2015
        (CEST)
      - I added mission targets for team 7 to the Command centre, Power
        plant and Antimatter storage tiles of the base map.
        --[ShipIt](User:ShipIt "wikilink")
        ([talk](User_talk:ShipIt "wikilink")) 07:33, 28 July 2015 (CEST)
    - The alien base could be used for the player the other way around.
      Secure the Command centre and win.
      --[ShipIt](User:ShipIt "wikilink")
      ([talk](User_talk:ShipIt "wikilink")) 12:03, 26 July 2015 (CEST)
      - Yes, giving some variety to missions should be nice
        --[DarkRain](User:DarkRain "wikilink")
        ([talk](User_talk:DarkRain "wikilink")) 04:58, 27 July 2015
        (CEST)
      - Unfortunately the alienbase has no Command centre. So I added
        mission targets for team 1 to the Power plant and Wormhole tiles
        of the base map. --[ShipIt](User:ShipIt "wikilink")
        ([talk](User_talk:ShipIt "wikilink")) 07:33, 28 July 2015 (CEST)
    - What about making the dropships a target for the aliens?
      --[ShipIt](User:ShipIt "wikilink")
      ([talk](User_talk:ShipIt "wikilink")) 11:06, 26 July 2015 (CEST)
      - This is an interesting idea, specially if we can make the AI
        pull a sneak attack on the dropship while the team is somewhere
        else, but that would require some further AI tweaking
        --[DarkRain](User:DarkRain "wikilink")
        ([talk](User_talk:DarkRain "wikilink")) 04:58, 27 July 2015
        (CEST)
      - I added a mission target for team 7 to each Firebird dropship.
        --[ShipIt](User:ShipIt "wikilink")
        ([talk](User_talk:ShipIt "wikilink")) 07:33, 28 July 2015 (CEST)
    - I added a mission target for team 7 inside the building of
      fueldump. So aliens win if the player is too slow.
      --[ShipIt](User:ShipIt "wikilink")
      ([talk](User_talk:ShipIt "wikilink")) 07:33, 28 July 2015 (CEST)
    - I added a mission target for team 1 inside the main building of
      the Mansion map. So the player wins if he secures the area for
      some turns. --[ShipIt](User:ShipIt "wikilink")
      ([talk](User_talk:ShipIt "wikilink")) 07:33, 28 July 2015 (CEST)

<!-- -->

- - ~~It does not work for aliens (team 7) at all.~~
    - First round of fixes is in, should work now for aliens too.
      --[DarkRain](User:DarkRain "wikilink")
      ([talk](User_talk:DarkRain "wikilink")) 04:58, 27 July 2015 (CEST)

- What is the misc_mission_alien good for at all? It does the same as
  misc_mission, doesn´t it? --[ShipIt](User:ShipIt "wikilink")
  ([talk](User_talk:ShipIt "wikilink")) 11:06, 26 July 2015 (CEST)
  - In-game it actually spawns a misc_mission, but sets the team
    property to the alien team, sets the radius to 3 map tiles (96
    units) and ignores all properties set with uforadiant (yes, **every
    single one** of them, even radius is always set to 96).
    --[DarkRain](User:DarkRain "wikilink")
    ([talk](User_talk:DarkRain "wikilink")) 22:05, 26 July 2015 (CEST)
    - After the first round of fixes the 'time' property should be
      recognized, still I'm not sure about having two entities that do
      nearly the same thing (you can create alien mission objectives
      with just misc_mission, and it is more flexible and less broken)
      --[DarkRain](User:DarkRain "wikilink")
      ([talk](User_talk:DarkRain "wikilink")) 04:58, 27 July 2015 (CEST)
      - I would rather have one thing that works as expected than having
        two that both do not. It is simply confusing and does not make
        any sense to me. --[ShipIt](User:ShipIt "wikilink")
        ([talk](User_talk:ShipIt "wikilink")) 06:48, 27 July 2015 (CEST)
        - Removed misc_mission_alien, we can concentrate on getting
          misc_mission to work instead
          --[DarkRain](User:DarkRain "wikilink")
          ([talk](User_talk:DarkRain "wikilink")) 18:20, 30 July 2015
          (CEST)
  - Destroy object' type misc_mission are mostly useless, since
    misc_mission aren't brush based they aren't tangible and can't be
    damaged by the player.
    - I almost always think things like that (does not work, no
      intention to get it working) should be removed, simply to avoid
      confusion. --[ShipIt](User:ShipIt "wikilink")
      ([talk](User_talk:ShipIt "wikilink")) 11:06, 26 July 2015 (CEST)
      - Probably the best option for now, I can't think of a way to make
        this work without making it convoluted and counter-intuitive to
        map. --[DarkRain](User:DarkRain "wikilink")
        ([talk](User_talk:DarkRain "wikilink")) 04:58, 27 July 2015
        (CEST)
      - Removed this kind of mission, if we really want a 'destroy
        object' mission we'll have to implement some
        func_breakable_mission or something like that
        --[DarkRain](User:DarkRain "wikilink")
        ([talk](User_talk:DarkRain "wikilink")) 18:26, 30 July 2015
        (CEST)