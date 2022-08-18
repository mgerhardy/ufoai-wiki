Some actors should be able to climb up/down using a ladder on the map.
Few thoughts about implementation:

- there should be new type of brush; one put such brush on two tiles,
  where first tile is at levelX and the second is at (levelX+1)
- player cannot manualy put an actor "to the ladder", but the
  pathfinding should be able to find a way through the ladder (in both
  ways, up and down)
- player can step on tile at (levelX) and by clicking on the tile at
  (levelX+1) he orders the actor to climb up - at the end of such
  climbing an actor should stay on tile at (levelX+1)
- the code should simply play new "climb" animation, and the actor
  should smoothly move from (levelX) to (levelX+1)

There are few conditions which should be checked before we will allow an
actor to climb

- the actor which is able to use a ladder, should have proper boolean
  definition (in teamDesc most probably) - mostly humans and organic
  aliens only
- we allow to use ladder when an actor has holdtwohanded weapon in hands
  and/or the second hand is "empty"
- we do not allow to use ladder when an actor has firetwohanded weapon
  in hands (big weapon, you cannot just temporary move it to your back)
- of course MOST OF ACTORS SHOULD HAVE NEW ANIMATIONS which is the
  reason why we won't have ladders in the nearest future ;-)