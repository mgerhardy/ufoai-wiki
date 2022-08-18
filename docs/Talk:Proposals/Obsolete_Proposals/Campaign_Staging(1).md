I felt the discussion was getting a bit long-winded, so I have
summarized our conclusions so far and archived much of it.
--[H-hour](User:H-hour "wikilink") 17:35, 17 June 2012 (SAST)

## Conclusions

### Adopting Alien Weaponry

- Players are able to research and use alien weaponry too quickly. We
  need to devise mechanisms to prevent the rapid adoption of alien
  weaponry.
  - Separate tech trees to somehow make alien weaponry powerful when
    used by them but require human-tech advances to be as powerful for
    Phalanx soldiers. Pros: Prevent immediate adoption. Cons: Difficult
    to find a convincing explanation why alien weaponry is not as
    powerful when used by humans. [ShipIt](User:ShipIt "wikilink")
  - Make some weapons too heavy for players. Pros: Prevent adoption
    completely. Cons: We can't yet restrict weaponry to certain types of
    aliens (Ortnoks, for instance). [H-hour](User:H-hour "wikilink")
  - Make alien armour strong vs. plasma, so player's adoption of plasma
    is not as effective until they complete more research.
    [H-hour](User:H-hour "wikilink")
    - Don't allow player to develop the plasma ammo for the grenade
      launcher as early.
    - Research of alien armour opens up plasma assault rifle round to
      take full advantage of it.
  - Require multiple samples of many weapons before they can be
    researched. Pros: Easily delays research completion. Cons: Will be
    confusing for existing players. [H-hour](User:H-hour "wikilink")

### Early Weapon Research

- The player should be able to completely research and deploy a new
  weapon after the first seven missions.
  [ShipIt](User:ShipIt "wikilink")
- Laser weapons lack a period of usefulness. Plasma weapons can be
  researched almost immediately, making them obsolete before they are
  even finished being researched. [ShipIt](User:ShipIt "wikilink")
  - Make laser weapons strong against alien armour (while plasma is
    weak). Possibly also require alien armour before hand-held laser
    weapons can be researched. See similar proposal in tech tree image
    ShipIt posted below. [ShipIt](User:ShipIt "wikilink")

### UFO Frequency and Stage Duration

- Mid- and late-game stages should have a shorter duration, because UFOs
  will appear more frequently in a given amount of time and will contain
  many more aliens, which means the player will go to the battlescape
  more frequently and for longer durations. Three months in the Late
  Game will probably take five times longer for the player to play than
  three months in the Early Game.
- The Beginning stage should have only Scouts.
  [ShipIt](User:ShipIt "wikilink")

### Soldier Availabilty

- Make more soldiers available at the start of the game and each month.
  Make the battlescape more difficult so that players are more likely to
  lose soldiers.

## Research Times

Currently, it looks like one scientist produces 0.8 hours of research
every hour of game time. In order to make it easier to balance, I am
tempted to raise that to 1.0 since many of the research techs completion
time will need to be adjusted anyway. It could even be something
configurable through the campaign definition in UFO scripts.

Next step: figure out a rough approximation of how many scientists a
player will have on a normal campaign at each stage (ie - not the great
players or the really bad ones). The following are guesses. ShipIt
please make better guesses.

- Beginning: 10 scientists
- Early game: 10-30 scientists
- Mid game: 40-60 scientists
- Late game: 60 scientists

--[H-hour](User:H-hour "wikilink") 18:48, 16 June 2012 (SAST)

- I never had more than 50-60 scientists. Beside that, the numbers above
  look reasonable. [ShipIt](User:ShipIt "wikilink") 12:51, 22 June 2012
  (SAST)
  - IMO, the 70-100 scientists number was low—I'd have pegged it at
    80-120, more if the research tree didn't run so dry currently. [Jon
    dArc](User:Jon_dArc "wikilink") 16:56, 26 June 2012 (SAST)
- Wow, scientists are seriously overworked: 0.8 hours of research for
  every hour of game time means they get less than 5 hours of rest a day
  (unless you have exhausted all research possibilities), well just
  saying. --[DarkRain](User:DarkRain "wikilink") 17:06, 22 June 2012
  (SAST)
  - It's just an abstract number that interacts with the "time" value of
    a research entry. The player will never view the numbers working
    behind the scenes. --[H-hour](User:H-hour "wikilink") 23:42, 22 June
    2012 (SAST)
- Last I checked the research-running function there was a comment
  suggesting that it wasn't clear how often it got called in in-game
  terms—I think the intention was for a scientist to produce 1 research
  per hour from the beginning (comments in research.ufo claim that
  research time is given in man-hours). If it really is 0.8 per hour I
  agree with raising it, but we should double-check that it isn't
  getting called every 48 minutes or something. [Jon
  dArc](User:Jon_dArc "wikilink") 16:56, 26 June 2012 (SAST)
  - It's been checked in the code and mattn made the 0.8 scriptable in
    campaign.ufo, so we can adjust this to our heart's content now.
    --[H-hour](User:H-hour "wikilink") 17:00, 26 June 2012 (SAST)

## Aircraft vs UFO balance and everything related

- All and every craft having the 1100 kph speed is pretty much strange.
  We should have an unique max and cruising speed for every aircraft/UFO
  type. [Sandro](User:Sandro "wikilink")
  - Hmm, I suspect something is wrong in the implementation then. In the
    scripts, all interceptors and UFOs have different speed values.
    --[H-hour](User:H-hour "wikilink") 19:15, 25 June 2012 (SAST)
- Saracen is supposed to be based on the Mach 3 aircraft, so it should
  be able to fly this fast. Also, it's 2 weapon slots (compared with 3
  of Stiletto) will then make an interesting choice for the player:
  heavily armed or fast interceptor. [Sandro](User:Sandro "wikilink")
  - If Google + my calculations are correct, Mach 3 is about 3600 kph.
    --[H-hour](User:H-hour "wikilink") 19:15, 25 June 2012 (SAST)
    - At the sea level. Since for lower apmosphere temperature and
      therefore speed of sound decrease with height (typically), you
      will get somewhat bigger Mach numbers for stratosphere. Anyway,
      got to check if it's still an issue or not (sorry for a bit of
      flooding). [Sandro](User:Sandro "wikilink") 16:14, 11 September
      2012 (SAST)
- Randomize speeds a bit. There are no two identical aircraft or pilots
  in the world. I'd say +- 50 kph for human craft and +- 300 kph for
  UFOs. [Sandro](User:Sandro "wikilink")
  - This is a proposal for a new coding feature, which is a bit beyond
    the scope of what we're trying to do on this page. Here we're just
    trying to identify balance issues and resolve them with the tools we
    have (for the most part). --[H-hour](User:H-hour "wikilink") 19:15,
    25 June 2012 (SAST)
    - To me, aircraft speed IS a balance issue. Consider the "piloting"
      skill: if max aircraft speed will depend on it and UFOs will have
      speed just closely matched by Phanalx aircraft, selecting good
      pilot will seriously affect probability of interception. IMHO
      that's a good piece of micromanagement.
      [Sandro](User:Sandro "wikilink") 16:14, 11 September 2012 (SAST)
      - I wasn't suggesting it's not a balancing issue. I was just
        saying that it is a bit beyond the scope of what I think we're
        trying to accomplish at this moment. I think it should go into a
        separate proposal. I've been trying to work on the aircraft
        numbers over the last few months and I'm convinced our air
        combat system is just not robust enough to accomplish many of
        the things it appears to want to accomplish (effective armour,
        armour-piercing rounds, the utility of long- vs. short-range
        weapons). I'll get into it more once I've got some numbers in
        place for 2.5, but air combat is not really my priority so I
        probably won't want to work on the code. Keep in mind, though,
        that our speed values are not very finely turned at the moment
        (scripts define speed typically between 7 and 16). So with the
        current setup it may be difficult to achieve those crucial
        thresholds where UFO and Phalanx aircraft speed are closely
        matched, increasing the importance of a pilot.
        --[H-hour](User:H-hour "wikilink") 11:08, 12 September 2012
        (SAST)
  - This seems like it goes down the rabbit hole of making changes that,
    even if realistic, no one will ever care about. What would be the
    philosophical difference between this change and, say, random
    modifiers to soldier stats to model off days or a solid night's
    sleep, or individual weapon accuracy modifiers to model subtle
    variations in maintenance or flaws in components? There's no end.
    [Jon dArc](User:Jon_dArc "wikilink") 16:59, 26 June 2012 (SAST)
    - Indeed, there should be a reasonable limit for complexity, since
      UFO:AI is not a Dwarf Fortress clone. But added complexity of
      simple rand() call looks rather small for me, and, I repeat, all
      aircraft having the same speed is ridiculous.
      [Sandro](User:Sandro "wikilink") 16:14, 11 September 2012 (SAST)
      - If all aircraft actually have the same speed, that is a missing
        feature. Each aircraft type is scripted to have different
        speeds. However, we'll need to check if they actually fly at the
        same speed, or if the display just shows the same speed for all
        of them (ie - is it a missing feature of the game mechanic, or a
        broken UI). --[H-hour](User:H-hour "wikilink") 11:08, 12
        September 2012 (SAST)

# Discussion

## Plasma Weapons

- - Keep it as it is. Precision of plasma weapons is pretty bad, so at
    long distance their users will be overpowered by snipers, at
    mid-distance GL is almost comparable, and in case of CQB firethrower
    beats them. So why deprive the player from a joy of mastering some
    alien technology early in the game? [Sandro](User:Sandro "wikilink")
    - I agree with keeping it as it is, but I think you're selling
      plasma weapons very short (and flamethrowers long). Even Plasma
      Pistols are competitive with flamethrowers for damage per TU, and
      do this with one-handed-fire and more firemode flexibility—not to
      mention substantially better range, ammo capacity, and reload
      time. Plasma rifles take a decisive damage-per-TU lead and are a
      more reliable damage type (everything resistant to plasma is also
      resistant to fire, but not the other way around). Grenade
      launchers fill a substantially different role (sacrificing
      single-target damage for AoE, arc rather than direct-fire,
      etc.)—certainly they serve as an argument that giving players
      relatively easy access to plasma weapons isn't unbalancing, but
      they're not a competitor for the same role. Long range is, of
      course, right out. [Jon dArc](User:Jon_dArc "wikilink") 16:35, 26
      June 2012 (SAST)

## Laser Weapons

- The lack of period of usefulness has less to do with how quickly
  plasma weapons show up and more with how weak laser weapons currently
  are. They compare poorly even against starting human weapons like the
  pistol or assault rifle, particularly if we restrict the comparison to
  performance against Bloodspiders and Taman+Ortnok in no or light
  armor. The fact that plasma weapons simply blow them out of the water
  and are available shortly after campaign start is just a final nail in
  the coffin—you need to wait for Shevaar or Medium Alien Armor to show
  up before laser weapons start outperforming human weapons. [Jon
  dArc](User:Jon_dArc "wikilink") 16:46, 26 June 2012 (SAST)
  - I think the decision to move laser weapons farther down the line was
    precisely to respond to this two-sided problem -- they must fit in
    between starting weaponry and plasma weaponry, which is available
    almost immediately. When they are moved farther down the tech tree,
    they will outclass plasma against armoured aliens (which would
    include Bloodspider/Hovernet) and have a longer life in the
    mid-game. --[H-hour](User:H-hour "wikilink") 16:58, 26 June 2012
    (SAST)

## General

- As proposed, the overal time will be 9 - 12 month. This is not enough
  imo. One reason is, if the aliens start to use a certain tech, e.g.
  needler, I would like to have them this advantage for some time. In
  2.4 I always had the feeling turning their own tech against them is
  way too easy (because I could do it very fast).
  [ShipIt](User:ShipIt "wikilink") 07:11, 23 May 2012 (SAST)
  - I agree, but I'm not sure how to do this. Most of the game's weapons
    research involves finding a weapon, then researching it. So as soon
    as an alien begins to use a weapon, Phalanx collects it and can
    research it. Any ideas how we can delay this process?
    --[H-hour](User:H-hour "wikilink") 14:07, 23 May 2012 (SAST)
  - My best idea right now is the hard way. Giving the human race an own
    weapon tech tree. Humans should learn from the aliens. Learn to make
    their own weapons/armour better, improve them. Maybe humans could go
    the projectile-based-weapons way, aliens have their beams. Going a
    way like that could also help to make our tech tree less linear in
    some way. Maybe : humans get shot by plasma pistol, they do some
    research and figure out how to use it, but it was not made for
    humans so its not a great weapon in human hands. On the other hand,
    once scientists know how plasma works, it gives an idea how to
    counter it. So they make better armour. Now aliens show up with
    armour. After research, humans might need to improve their
    weapons/ammo. [ShipIt](User:ShipIt "wikilink") 20:15, 23 May 2012
    (SAST)
  - One possibility that could work in some cases would be to make some
    of the heavy weapons actually too heavy for humans to carry. We
    would need to be able to restrict these weapons to ortnoks or other
    strong alien races, but this should be possible with the planned
    improvements to equipment selection. That would at least force us to
    either not have the most powerful versions of some tech (particle
    cannon) or force Phalanx to devise lighter mechanisms for deploying
    it (longer research times). --[H-hour](User:H-hour "wikilink")
    10:13, 24 May 2012 (SAST)
  - The obvious solution seems to be to lengthen the chain to usable
    weaponry—rather than alien weapons being combat-ready in human
    hands, have them be relatively bad and then stick an additional tech
    on the end for researching retrofits/reconstructions for the weapons
    that have actual usable stats. [Jon dArc](User:Jon_dArc "wikilink")
    14:36, 19 June 2012 (SAST)
    - This is basically what we've decided with the Plasma weapons and
      the Encased Plasma round. By making alien armour excellent against
      Plasma, we make it good for aliens but not as good for Humans
      until they develop a later tech. However, I don't want to
      undermine all of the alien weapons. We could use a good idea for
      how to accomplish something like this (that doesn't feel forced or
      cheap to the player) for needlers and particle beam weaponry.
      --[H-hour](User:H-hour "wikilink") 20:17, 19 June 2012 (SAST)
    - Difficulty: no way to make weapons worse for humans than for
      aliens. Solution: aliens already have enhanced Accuracy relative
      to humans—if aliens can be guaranteed not to use human weapons, we
      can just give base alien weapons bad spread values and compensate
      by cranking up accuracy/skill (will need to do the math to see if
      we have enough wiggle room before hitting skill maximums).
      - I've thought about this and it's not a bad idea. But it would
        have to be done across the board (used for all/none of the
        aliens and all/none of the alien weaponry). I'm not sure I want
        to commit to a solution that isn't very flexible. Still, it's
        something worth considering. --[H-hour](User:H-hour "wikilink")
        20:17, 19 June 2012 (SAST)
    - Difficulty: market, production, and equipment interfaces are
      unwieldy—a significant increase in equipment types threatens to
      make them entirely unusable. A few ideas on how to resolve this,
      but no idea how feasible any of them are given current
      implementation. [Jon dArc](User:Jon_dArc "wikilink") 14:36, 19
      June 2012 (SAST)
      - Have you seen the UI2 window? Still being worked out, but should
        be a little bit easier to use. Also, I don't see a major
        increase in the equipment types. A few new ammos is probably
        enough. --[H-hour](User:H-hour "wikilink") 20:17, 19 June 2012
        (SAST)
- We might want to take into account how many missions the alien will
  start during a month in each certain stage (rarely, frequent, often).
  - UFO mission spawning increases slowly over the game as shown in the
    graphs here:
    [Talk:Gameplay_Proposals/Campaign#2012_Adjustment_Considerations](Talk:Gameplay_Proposals/Campaign#2012_Adjustment_Considerations "wikilink").
    I will try look at current numbers to estimate what alien mission
    frequency will be like at different stages.
    --[H-hour](User:H-hour "wikilink") 14:07, 23 May 2012 (SAST)
  - I have now added average number of UFOs for each stage. This is
    based on the current implementation and is not meant to be a
    recommendation. Looking at the numbers, it looks like the average
    missions over the game would be 159-239. That's a big discrepency,
    but my guess is that over time the averages would gravitate towards
    the center, so we can probably say about 200. What do we think about
    that number? Should we consider reducing it?
    --[H-hour](User:H-hour "wikilink") 11:43, 9 June 2012 (SAST)
    - In the later stages of the game, when the player sees more UFOs,
      they should also be completing research more quickly. Ideally, the
      player would feel about the same number of missions between
      important research completion moments. This raises the question of
      whether the late game should take 5 months. We would need a lot
      more research content to keep the game from feeling like it is
      slowing down. --[H-hour](User:H-hour "wikilink") 11:43, 9 June
      2012 (SAST)
    - I also think we should consider reducing the number of UFOs in the
      Beginning stage. That stage should only go through 3-4 missions
      max, and then the player should enter a "real" game stage. That
      way the player has a quiet first month, they can make headway on
      research, and they get to learn the monthly income/employees
      system without too much pressure.
      --[H-hour](User:H-hour "wikilink") 11:43, 9 June 2012 (SAST)
      - We should also consider another fact beside the number of
        missions. The amount of time the player has to spent on the
        battlescape. In later stages, the bigger UFOs will be harder to
        beat, one mission will take much more time to play than a measly
        scout. With the same number of missions it will take a lot of
        hours (in real time) to see the next research completed. So I
        tend to agree we should try to reduce the total number of
        battlescape missions for a campaign.
        [ShipIt](User:ShipIt "wikilink") 13:53, 9 June 2012 (SAST)
- random thought about alien interests - After their first attacks the
  hive mind decided humanity can, and therefore should, be
  'assimilated'. But the attacks also have shown humans are not
  brainless and defensless creatures. There was atleast some resistance.
  So aliens will mainly scout at this stage, in order to find out more
  about us. During this stage the humans will shoot down several scouts,
  so at the end the first fighters are sent to (?) guard the scouts and
  intercept Phalanx aircraft. [ShipIt](User:ShipIt "wikilink")
  - I like the concept. I'm not sure how mission types are decided upon
    and how to modify this at different times, so it will take some
    digging to bring it out. --[H-hour](User:H-hour "wikilink") 17:43,
    11 June 2012 (SAST)
- Proposed Changes
  - The time until the first research is finished and the results
    (weapons) can be used on the battlefield is too long atm. My goal
    would be to have the player playing around 7(?) missions with the
    original equipment until he can start to use the first new one. This
    means, the player can research and produce the EM-rifle + ammo or a
    laser weapon + ammo or plasma weapon in this time.
    [ShipIt](User:ShipIt "wikilink")
    - I agree. The research time on lasers probably needs to be reduced
      some. --[H-hour](User:H-hour "wikilink") 17:43, 11 June 2012
      (SAST)
    - One problem is : There is no need to research Lasers or EM-Rifle
      right now. The original equipment works very well and Plasma tech
      is within reach. My guess is one could play without any (weapon)
      research until the armoured Ortnoks appear. If this happens even
      later in game as proposed, the player might entirely skip the
      laser tech. (Idea: We possibly could avoid a lot of problems by
      putting the laser tech being superior to the plasma weapons. The
      player would use the original eqipment until he can research and
      use plasma weapons. Plasma weapons are bad versus alien armour at
      which point the player can start to develop and use laser tech to
      beat alien armour.) [ShipIt](User:ShipIt "wikilink")
      - I think you are right about this. Perhaps I overpowered the
        assault rifle because I have a special love of human weaponry
        like assault and sniper rifles. I'm not sure if it would be
        better to up the damage for laser weapons or reduce the assault
        rifle damage. Something to keep in mind is that the unarmoured
        Taman is supposed to be a fairly delicate creature, similar to
        humans. It will not be clear why assault rifles are so bad
        against them. Another possibility would be to introduce light
        alien armour early in Early Game and make it far outclass all of
        the existing human-tech weapons. This way, the player would
        start in Beginning with fairly easy kills, then in early game
        would face a situation where they have to make a jump to better
        weaponry. --[H-hour](User:H-hour "wikilink") 17:43, 11 June 2012
        (SAST)
        - I do not think the original weapons are overpowered. Todays
          weaponry is not that bad and should be able to push an
          unarmoured Alien out of its sandals right away. But the Laser
          Weapons are now badly sandwiched between the initial equipment
          and the Plasma Weapons. Thats why I vote to make them appear
          after the Plasma Weapons.
          ![](TechTree_proposed_modified.png "TechTree_proposed_modified.png")
          [ShipIt](User:ShipIt "wikilink") 20:46, 11 June 2012 (SAST)
          - I would like to keep laser weapons as the first weapon
            research (that's how it was in X-Com, so maybe I am just
            being nostalgic). The key is to find a way to delay the
            introduction of plasma and give it a real advantage over
            assault rifles. --[H-hour](User:H-hour "wikilink") 11:19, 16
            June 2012 (SAST)
      - I just had an alternative idea for delaying plasma -- and all
        alien tech weapons. What if we say that we need more than one
        sample to properly study something. I imagine the first attempts
        to pry open a plasma ammo container could destroy its interior,
        for instance. Maybe we could set the threshold of new weaponry
        up to 10, 15, 20, so that the player must face the weapon
        several times in combat before he can effectively research it.
        It would be a conceptual leap for our existing players, so we'd
        want to find a way to explain it clearly in-game.
        --[H-hour](User:H-hour "wikilink") 11:19, 16 June 2012 (SAST)
  - The number of available recruits is too low. The player is forced to
    retry on losses in early missions simply because he cannot replace
    the dead soldiers. He is also forced to take injured soldiers to
    mission for the same reason, which should not be possible at all. I
    would give at least 15 soldiers to start with.
    [ShipIt](User:ShipIt "wikilink")
    - Agreed. I want to up the number of soldiers available as well as
      the number of aliens faced, to make the battlescape a more
      "painful" experience all around.
      --[H-hour](User:H-hour "wikilink") 17:43, 11 June 2012 (SAST)
  - The Scout version of the 'Hovernet' could be used to accompany the
    Tamans on scout mission. [ShipIt](User:ShipIt "wikilink")
    - Are we still talking about the Beginning stage? If so, I'd like to
      leave it as just Taman and Bloodspiders, because these are two
      VERY easy aliens to kill. The Bloodspider is not really much of a
      threat until the Combat Bloodspider comes along (in my vision for
      it), because the Combat Bloodspider will have many more TUs (not
      implemented yet).--[H-hour](User:H-hour "wikilink") 17:43, 11 June
      2012 (SAST)
      - If the Hovernet is more than just a Scout Drone than I agree.
        [ShipIt](User:ShipIt "wikilink") 20:46, 11 June 2012 (SAST)
  - The aliens using Plasma Grenades does not fit their overal approach
    at this stage. Maybe we could use an Alien Stun Grenade here and
    introduce the Plasma Grenade later on?
    [ShipIt](User:ShipIt "wikilink")
    - I think we could just remove the plasma grenade at this stage.
      Introducing the alien stun grenade too early will also make it
      available for research.--[H-hour](User:H-hour "wikilink") 17:43,
      11 June 2012 (SAST)
      - Is the research of the Alien Stun Grenade useful for the player
        in some way? I could not find anything about this right now. In
        the 'BIG research tree' it seems to be of no use (in terms of
        research). My idea was the Stun Grenade could maybe teach the
        player to be careful without being too dangerous.
        [ShipIt](User:ShipIt "wikilink") 20:46, 11 June 2012 (SAST)
        - It allows the player to use the alien stun grenade, which is a
          pretty powerful stun weapon.
          --[H-hour](User:H-hour "wikilink") 20:57, 11 June 2012 (SAST)
- Aliens will not field Plasma Blaster yet (early game) (starts at
  interest 150). [ShipIt](User:ShipIt "wikilink") 11:17, 9 June 2012
  (SAST)
- I still think we should implement some 'general techs' like the
  "Plasma Weapons Engineering". Those will be useful in two ways - first
  we can stretch the timeline in the research tree in a natural way
  (with the PWE it would be easy to delay/speed up the appearance of
  Laser Weapons), second we can use them as a prerequiste for other
  techs later on. The "Phalanx Archives" could be used to give the
  player something as a first research project until he can recover some
  alien artefacts and corpses from the battlefield.
  [ShipIt](User:ShipIt "wikilink") 10:38, 23 June 2012 (SAST)

## Other Notes

### Alien Interest Thresholds for UFO appearance

The following is a list of mission types with each UFO available (as it
is currently coded). Those with a (\*) are only available if alien
interest has reached a threshold set in the aircraft scripts.

`Base Attack    Fighter, *Bomber`
`Build Base Scout, Supply`
`Harvesting Harvester`
`Intercept  Fighter, Harvester (25% chance of Harvester)`
`Recon      Scout, Fighter`
`Supply     Supply`
`Terror     Harvester, *Corrupter, *Bomber`
`XVI        Scout, Fighter, *Corrupter`

This raises a couple issues. First, because there are no alien interest
thresholds for several mission types, I am not able to implement the
campaign staging as proposed here. I am happy to add the code for alien
interest thresholds, but there is one problem I don't know how to deal
with properly: what to do with a mission for which there should be no
valid UFO types in the early game (say, XVI, Terror, Base Attack). I
think it would be good to simply ignore the mission altogether. Another
option would be to have the game pick the next most desired mission
type. But these are things I don't know how to do in the code.

Second, we don't yet have any role for the new Gunboat UFO. I'd guess it
would be Intercept but if we want it to appear more in the late-game, it
could also be used for Recon.

Third, as I understand the current system, it simply adds all possible
UFOs and then chooses one randomly. In the late-game, I would like to be
able to specify that more difficult UFOs occur more frequently.
Otherwise the player will still be playing too many Scout and Fighter
missions late in the game. I don't know the best way to do this, but one
possibility would be to make the alieninterest parameter of a UFO have a
min and a max value. If it is over the max, that UFO no longer appears.
However, it would be better to reduce the rate of some UFOs later in the
game rather than removing them entirely. I'm not sure what the best way
is to handle this, although we could hard-code the stack like this:

`   ufoTypes[num++] = UFO_FIGHTER;`
`   if (UFO_ShouldAppearOnGeoscape(UFO_CORRUPTER))`
`       ufoTypes[num++] = UFO_CORRUPTER;`
`       ufoTypes[num++] = UFO_CORRUPTER;`
`       ufoTypes[num++] = UFO_CORRUPTER;`
`       ufoTypes[num++] = UFO_CORRUPTER;`

I'm not sure if this is the right way to do it in the code, but I'm
thinking this would make the corrupter 4 times more likely than the
fighter to be selected once it's alien interest threshold is reached.
Ideally, it would be nice to have all of this set through UFO scripts
instead of hard-coded, but this might be an easier solution for 2.5.
--[H-hour](User:H-hour "wikilink") 19:28, 24 September 2012 (SAST)

## Length of time

Now that I've played through it, I felt that the beginning of the game
was too drawn out (Beginning/Early Stage). Six months was just too long
and I felt like it stalled a bit waiting for the Corrupter/Supply ship
to arrive. I am thinking about cutting the Beginning stage to two weeks,
dropping one month from the Early Stage, and cutting out two weeks
before Ortnoks appear and two weeks after they appear (in mid-game).
This will, of course, require adjustments to research times, etc. And
I'm also worried about funding and base construction (it takes time and
monthly income to expand bases). Thoughts?
--[H-hour](User:H-hour "wikilink") 01:26, 21 March 2013 (SAST)

- Do we absolutely need it to go peng-peng-peng? I sometimes felt the
  game was processing too slow because I had to wait for the next payday
  before I could build the next base buildings.
  --[ShipIt](User:ShipIt "wikilink") 12:31, 21 March 2013 (SAST)
  - I think I felt the problem in the beginning of the game because
    there is less diversity in UFOs, aliens and weapons, so the
    repetition is more noticeable. Maybe I am being overly sensitive in
    the mid-stage. --[H-hour](User:H-hour "wikilink") 16:22, 21 March
    2013 (SAST)