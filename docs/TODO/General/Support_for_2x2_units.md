## The Aim

On the one hand we have the need for units that are bigger than 1x1
ground units in the battlescape. Some examples are

- 2x2 The vehicles employed by PHALANX such as the Phoenix and the Ares
  .. this is a must, they are just too useful not to include.
- 2x2 The "Breeder" alien as planned by [Winter](User:Winter "wikilink")
- 2x2 The alien drone "hovernet" or "floater" or how it's called now.
- Maybe another "big" alien?

All these models need to be able to move, attack and be attacked in the
battlescape.

## General

- The hitbox of the 2x2 units are currently still 1x1. Done in
  G_Actor2x2Spawn now. --[Hoehrer](User:Hoehrer "wikilink") 15:59, 26
  February 2008 (CET)

## Pathfinding

If I understand it right the current code depends on the unit size of
1x1 in various places. A short list of related areas is here:

- **pathfinding** (needs to take into account the size of the model).
  See also ...

  - :Grid_MoveCalc

  - :Grid_MoveMarkRoute

  - :Grid_MoveMark

    - Basic support for 2x2 units

    - Diagonal move of 2x2 units should work now (Revision 10422)

    - Check for fall stuff. (done in Revision 10526)

    - Check for height stuff if that is needed at all. See todo text in
      the function

  - :Grid_MoveCheck

  - :Grid_CheckForbidden

    - I was wrong, it isn't the most important, but it has some heavy
      influence on the result of the pathfinding. Nonetheless this was
      the first function that has been extended to support 2x2 units.
      --[Hoehrer](User:Hoehrer "wikilink") 22:58, 23 July 2007 (CEST)

  - :Grid_Fall (Revision 10526)

  - :G_ClientTeamInfo - should search for correct spawn points now.

  - :G_CheckMoveBlock \<- no check seems to be needed.

  - :G_ClientMove \<- no check seems to be needed.

  - :CL_ConditionalMoveCalc \<- undirectly checked via the
    le-\>fieldSize parameter

## Various UI and map stuff

- The display in the battlescape (2x2 cursor display + model placement)

  - According to mattn this is done. See "define BoxSize" and "boxSize"
    in for more info. UPDATE: there still are some issues with the
    cursor+model

  - new 2x2 cursor is shown, but it is centred on a single 1x1 field
    (the 'top-left' origin of the 2x2 field) it has to be moved (and
    maybe extended) to show exactly where the model is. You can check
    the correct location with a 1x1 cursor when hovering over the
    surrounding squares of the 2x2 unit. (Implemented in revision 10432)

  - Same as above but for the model of the 2x2 unit. It is also shown at
    a wrong place. First draft committed with revision 10433 - I'll keep
    this as "wip" because I'm not sure if this'll work with shot-origins
    and stuff.

- UI code (i.e. selecting 2x2 units)

- Add the "spawn points" in the map-files.

  - The **harbour** map should have at least one 2x2 spawn point.
  - BTAxis is adding some spawn points here and there, so I think this
    is also basically 'done' :)

- Special weapons for the various ugvs (very similar to the "Bloodspider
  weapon problem")

  - Buy/sell weapons with tanks.

  - (Auto-)equip the weapons when sending tanks to a mission.

  - Handle tank weapons correctly when transferring.

- There sure are more places and things ... please add them to the talk
  page if you find some.

## Turrets

- Add support for turrets (currently 'heads' of a tank do not rotate,
  but the body+head do it at the same time.)

  - Body rotation is stored in le-\> angles (and le-\>dir)
  - The le is then converted to an ent: cl_le.c:LE_AddToScene \[le -\>
    ent\]
  - The resulting ent then seems to end up in R_CalcTransform - see the
    following flow:

<!-- -->

    V_UpdateRefDef [cl.refdef.entities = r_entities;]
    |
    v
    V_RenderView [re.RenderFrame(&cl.refdef);] (-> re.RenderFrame = R_RenderFrame;)
    |
    v
    R_RenderFrame(refdef_t)
    |
    v
    R_RenderView(refdef_t)
    ->  R_TransformEntitiesOnList();
            -> R_CalcTransform(entity_t) [e->angles]
    ->  R_DrawEntitiesOnList();

- - My suggestion is to add something like le-\>angles_look (and
    le-\>dir_look if needed) that is then handled differently in
    TransformEntitiesOnList. Normal "angles" are used to rotate the
    whole model and "angles_look" are calculated (do not forget
    tag-influenced transform-stuff) to let the child mesh always point
    to the wanted direction. This is only needed for actors that have a
    "has_turret" flag (also new).

## etc

- Map compiler (possible changed bsp=map format? Only needed if we want
  to information for pathfinding pre-calculated)
  - See among other places
  - I think changing the map compiler might not be necessary after all.
    -- [Hoehrer](User:Hoehrer "wikilink") 22:58, 23 July 2007 (CEST)

<!-- -->

- Just a note to myself - the pathfinding aka. "can i walk there"
  calculation calltree:

<!-- -->

    cl_actor.c:CL_ConditionalMoveCalc
    g_client.c:G_MoveCalc (as gi.MoveCalc)
    (In both calls "distance" is given as MAX_ROUTE)
    +-> void Grid_MoveCalc (struct routing_s *map, pos3_t from, int size, int distance, byte ** fb_list, int fb_length)
        +-> static void Grid_MoveMarkRoute (struct routing_s *map, int xl, int yl, int xh, int yh)
            +-> static void Grid_MoveMark (struct routing_s *map, int x, int y, int z, int dv, int h, int ol)
                +-> static qboolean Grid_CheckForbidden (struct routing_s * map, int x, int y, int z, int actor_size)

## The Plan

Since neither mattn nor myself ([Hoehrer](User:Hoehrer "wikilink")) know
a lot about pathfinding we currently see no way how to implement this.
Help on this subject is would be greatly appreciated.

Some ideas that we have come up with on how it *could* work in theory:

- Each unit is stored only by origin (x,y,z) and its size (e.g. 1x1 or
  2x2).
- Ok, to refine this I have to state how I'm currently thinking about
  this when writing/changing code. A 2x2 unit consists of 4 squares on a
  2-dimensional level. the origin (x,y) and 3 more squares as follows:
  (**x, y**) (**x+1, y**) (**x, y+1**) and (**x+1, y+1**)

<!-- -->

    +--> x
    |O#
    |##
    V
    y

- Do not mind the alignment (left/right and up/down) of the x and y
  axis - I do not know yet how they relate to the drawn map currently.
  :)
- All of the above is independent of how the displayed model is rotated.
  The origin is **always** at the same place. And we do not plan to
  include asymmetrical units!
- Check all 4 squares for each step in the pathfinding process (whatever
  it does that is :)).

[Category:Contribute](Category:Contribute "wikilink")
[Category:TODO](Category:TODO "wikilink")
[Category:Development](Category:Development "wikilink")