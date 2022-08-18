--[Plouj](User:Plouj "wikilink") 18:45, 23 April 2007 (CEST): You didn't
provide any game-related disadvantages of the second type of RF. I would
like to know if there are any. Being a novice player I sort-of use the
current RF system as if it was the second RF system that you described.
Having a full TU bar at the beginning of the turn I first select my RF
mode (1 or multi) and then use the remaining TUs to do my movements. The
next turn I mostly ignore the fact that some of the TUs were used for
RF.

--[BTAxis](User:BTAxis "wikilink") 19:16, 23 April 2007 (CEST): The
disadvantage would be that it takes more planning and anticipation on
the part of the player. After all, if you carelessly use up all your TUs
on moving between buildings, you lose your RF opportunity. So it makes
gamepley more, well... You could say strategic, or you could say
cumbersome. It depends on your point of view.

## Method 2 - Coding thoughts

I just had some time to look at the code-side of "method 2" (i.e. the
UFO:EU) way again.

Note: This is not about the actual reaction fire scenario (who shoots
when and how), this only covers the TU-reservation stuff for RF (and
other things). All of this can be done on the client side (except maybe
the check of weapon-changing mentioned later on).

This means among other things that this ...


*A soldier who is set to use one Reaction Fire mode but has not enough
TUs to use it will shoot using another Reaction Fire mode if he has
enough TUs for that.
Note that a soldier who has TUs to spend on Reaction Fire will ALWAYS do
so if able. Reaction Fire cannot be disabled except by using up enough
TUs.*

... is kinda irrelevant for TU-reservation itself. We can discuss this
elsewhere though - be sure to comment on problems the reservation may
cause to the RF-handling here though.

The basic functionality (client side) would be to block actions when a
certain value of unused TUs is reached. This value is defined by the
player - he reserves an "action" for his soldier to either use after he
is done with his other actions (think: he moved around a bit and now
tries to crouch and shoot) or for reaction fire (shooting at spotted
alien(s)).

So the core issues are:

- Provide the player with an intuitive way to tell the game what to
  reserve. Each of the below needs to have it's own button (or similar
  UI element) since they could be combined in any way. The state of each
  should carry over to the next turn (if possible and sane).
  - Most important: RF is easy (relatively) - reserve the TUs for the
    selected firemode - no additional UI needed. RF button is either ON
    or OFF. "Multi" will be removed (Until I figure out an easy way to
    *reserve multiple shots* that is ;))
    - Actually, this is what I was trying to explain with the bit you
      pasted above: RF cannot be turned off. The reasoning was that
      there was no point in doing so. However, I have in the mean time
      been thinking about visibility support, and I think stealth can be
      a good reason why you would NOT want to use RF even if you could.
      So let it be known that although the above point contradicts what
      I originally wrote, it is nevertheless a sensible design choice.
      --[BTAxis](User:BTAxis "wikilink") 12:40, 25 September 2007 (CEST)
    - Hm, thanks for clearing this up. So basically the "react on enemy
      turn" is always on but the player has to make sure there are
      enough TUs left for it.
      I see 2 'problems' with that behaviour: First one is as you
      mentioned "stealth" and the second is ammo-depletion (i.e. the
      soldier might choose badly and empty the weapon (not an issue for
      cheap ammo of course) you needed for some choices of your own).
      A possible solution for this would do the following: RF is default
      on ON (only one shot of the selected firemode will be fired, no
      matter what) - (This would also meant that RF-reservation is
      always on in my current draft - dunno if that's a good thing). The
      player has the choice to disable RF -\> OFF (for stealth) or turn
      on MULTI mode where as many shots (of the selected firemode) are
      fired and the rest of the TUs is wasted on the next cheaper
      firemode. --[Hoehrer](User:Hoehrer "wikilink") 18:17, 25 September
      2007 (CEST)
    - I had thought of ammo depletion, but I don't consider it a big
      issue. It's true that the player may run into an ammo shortage
      because of reaction fire if he doesn't pay attention, but I still
      think a simple ON/OFF state of RF will suffice, where ON is what
      you describe as MULTI. A simple interface is preferable over a
      complex one, and I think situations where unintended ammo
      depletion will cause serious problems for the player will be
      sufficiently rare for them to become a memorable "oh shit" moment
      rather than an annoyance that reduces the game's playability.
      --[BTAxis](User:BTAxis "wikilink") 21:26, 25 September 2007 (CEST)
  - Nice to have: Reserve TUs for firing after the other actions is a
    bit more tricky since the player may want to fire a different
    firemode than the one defined in the RF dialog (and he sure is lazy
    so constantly switching it to achieve this is kinda out of
    question).
    - I believe this is the responsibility of the player. If he reserves
      a snap shot, moves, then decides he wants an aimed shot after all,
      then tough luck. Should have reserved the most expensive one. I
      see no reason to code a failsafe mechanism for this.
      --[BTAxis](User:BTAxis "wikilink") 12:40, 25 September 2007 (CEST)
    - If the player chooses wrongly so be it. That's not the thing I
      want to prevent here. This can be done additionally to the RF-TU
      reservation (at least in my plan ;) Don't think of it as failsafe,
      it's similar thing as reserving TUs for crouching. the basic
      functionality should be there and not be mixed up with stuff I
      reserved for RF. Te way I planned it one could reserve x TUs for
      RF, y TUs for crouching and z TUs for shooting after that. Might
      sound more complex than it is.
      --[Hoehrer](User:Hoehrer "wikilink") 18:17, 25 September 2007
      (CEST)
  - Nice to have: Crouching (since it's related I'll handle this here as
    well) It has the benefit of having a fixed value , so the
    disadvantage of choosing a "mode" is non-existent.
  - (Nice to have: reserving a player-defined value of TUs.)
    - BTAxis: *By the way, about reserving a fixed amount of TUs, maybe
      you can somehow do this by clicking on the TU bar directly?
      With a mouseover tooltip that displays the exact amount at that
      position.
      The basic node (for sliders) is already implemented - see the
      gamma slider bar. It's just a matter of making it look good and of
      course making it work right.*
- Add a way to store and check the stored info. Some things that need to
  be stored somehow:
  - Number of TUs.
  - Type of reserved action.
- What happens to the RF and "shoot in same turn" reservations if the
  weapon is changed - or more precise: is the code up for handling this?

Oh, and I think gotta play ufo:eu, tftd, ufo:apoc and ja2 again to see
if there are improvements to this we can steal ;)

--[Hoehrer](User:Hoehrer "wikilink") 10:09, 25 September 2007 (CEST)

The tracker-item (and some patches & code snippets) is available here:
<http://sourceforge.net/tracker/index.php?func=detail&aid=1807978&group_id=157793&atid=805244>

--[Hoehrer](User:Hoehrer "wikilink") 12:34, 5 October 2007 (CEST)