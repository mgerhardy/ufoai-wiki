There are several inventory bugs discovered by BTAxis and me during the
multiplayer tests. These are hard to fix, so to not forget things i will
note everything I know here.

## Empty floor while items there

- Empty floor while items there

Sometimes when throwing a lot of stuff to the one specific tile, one of
the player see empty floor there, but it seems that items in fact ARE on
the floor. The player cannot drop an item to the container tiles where
other items already are dropped. If the player finally find the place on
the floor with empty space, he can drop the item, but that item
dissapears. Till now, I managed to gather some debug info which brings
me to some conclusions:

:\* the full debug log i managed to get:

    Com_MoveInInventory()... now we will remove: pbeamcannon from: right
    Com_MoveInInventory()... now we will add: pbeamcannon to: floor
    Com_AddToInventory()... adding item: pbeamcannon to container floor
    G_ClientInvMove()... server sends information to client about inventory change (NOT FROM the floor): pbeamcannon
    G_ClientInvMove()... server sends information to client about inventory change (TO the floor): pbeamcannon
    G_ClientInvMove(1)... we will now send EV_INV_ADD event for ent->number: 13
    InvAdd: message ignored... LE 26 not found (type: 0)
    InvAdd: ignoring:
    Item: pbeamcannon
    ... name          -> Ręczne działo cząsteczkowe
    ... type          -> rifle
    ... category      -> 49
    ... weapon        -> 1
    ... holdtwohanded -> 0
    ... firetwohanded -> 1
    ... twohanded     -> 0
    ... thrown        -> 0
    ... usable for weapon (if type is ammo):

:\* the from and to containers are correct ones, because I am printing
this here:

    Com_MoveInInventory()... now we will remove: pbeamcannon from: right
    Com_MoveInInventory()... now we will add: pbeamcannon to: floor

and I indeed was moving pbeamcannon from right hand to the floor

:\* the item was correctly handled by G_ClientInvMove():

    G_ClientInvMove()... server sends information to client about inventory change (NOT FROM the floor): pbeamcannon
    G_ClientInvMove()... server sends information to client about inventory change (TO the floor): pbeamcannon

:\* the server send the EV_INV_ADD event to the client:

    G_ClientInvMove(1)... we will now send EV_INV_ADD event for ent->number: 13

note the ent-\>number: 13

:\* the client received such event, and parsed it, but the ent-\>number
was wrong:

:\*\* Höhrer: I think this might be a bit-shift: 13d = **1101b** and
26d=**11010**b

:\*\* Höhrer: Also: CL_InvAdd is the only CL_Inv\* function that does
not parse the data with MSG_ReadFormat (most likely because of the "s\*"
definition of the data (mind the "\*")

    InvAdd: message ignored... LE 26 not found (type: 0)

:\* Now, the G_ClientInvMove(1) printf is here:

    /* add it */
            if (to == gi.csi->idFloor) {
                gi.bprintf(PRINT_HIGH, "G_ClientInvMove()... server sends information to client about inventory change (TO the floor): %s\n",
                gi.csi->ods[ic->item.t].id);
                if (newFloor) {
                    assert (FLOOR(ent));
                    FLOOR(floor) = FLOOR(ent);
                    /* send item info to the clients */
                    G_CheckVis(floor, qtrue);
                } else {
                    /* add the item; update floor, because we add at beginning */
                    FLOOR(floor) = FLOOR(ent);
                    gi.bprintf(PRINT_HIGH, "G_ClientInvMove(1)... we will now send EV_INV_ADD event for ent->number: %i\n", ent->number);
                    gi.AddEvent(G_VisToPM(floor->visflags), EV_INV_ADD);
                    gi.WriteShort(floor->number);
                    gi.WriteShort(6);
                    G_WriteItem(item, to, tx, ty);
                }
            } else {

note, that this event is being issued when if (newFloor) is not true.
When it can happens? Look:

    /* "get floor ready" */
        floor = G_GetFloorItems(ent);
        if (to == gi.csi->idFloor && !floor) {
            floor = G_SpawnFloor(ent->pos);
            newFloor = qtrue;
        } else {
            newFloor = qfalse;
        }

(newFloor) can be qfalse only if (!floor) is true, because (to ==
gi.csi-\>idFloor) is true for sure (see my debug prints above). Note:
floor = G_GetFloorItems(ent);

:\* conclusion: G_GetFloorItems() for some reason returns NULL (so
(!floor) is true) when there is many items on the floor

:\* when i am receiving the (InvAdd: message ignored...) messages (see
cl_parse.c/CL_InvAdd())for items being dropped to the floor and
dissapearing, it is always the case of my debug printf
G_ClientInvMove(1), thus it is always the case of
G_SpawnFloor(ent-\>pos) returning NULL. And in every such case there
were items on given floor tile.

:\* the items are (usually) invisible only for one player - when the
player drops the item to the floor with invisible items, the second
player is (usually) able to see (and use) both "old" items on the floor
and newly added item

:\* the items can reappear "after some time" - did not figure out yet
what exactly are the circumstances

## items "visible but not useable"

- items "visible but not useable"

:\* [note two items on the floor covering
itself](http://voovoos.killfile.pl/roznosci/inv.jpg)

:\* the item was "visible" for the player, but the player cannot pick it
up

:\* case study, the game hosted by me (Zenerka), the second player
connecting was BTAxis

::\* how it looks in BTAxis' ufoconsole.log:

    Zenerka: try now
    Team 1 ended round, team 2's round started!
    Com_RemoveFromInventoryIgnore()... removing item: laserpistol from container: floor
    Com_AddToInventory()... adding item: laserpistol to container backpack
    Com_AddToInventory()... adding item: plasblaster to container floor
    ]I see a bolter
    BTAxis|ufo: I see a bolter
    ]And I can't pick it up

::\* how it looks in my ufoconsole.log:

    ]try now
    Zenerka: try now
    Team 1 ended round, team 2's round started!
    Com_AddToInventory()... adding item: plasblaster to container right
    Com_RemoveFromInventoryIgnore()... removing item: bolterrifle from container: floor
    Com_AddToInventory()... adding item: bolterrifle to container floor
    Com_RemoveFromInventoryIgnore()... removing item: laserpistol from container: floor
    Com_MoveInInventory()... now we will remove: laserpistol from: floor
    Com_MoveInInventory()... now we will add: laserpistol to: backpack
    Com_AddToInventory()... adding item: laserpistol to container backpack
    G_ClientInvMove()... server sends information to client about inventory change (FROM the floor):
    G_ClientInvMove()... server sends information to client about inventory change (NOT TO the floor):
    Com_RemoveFromInventoryIgnore()... removing item: laserpistol from container: floor
    Com_AddToInventory()... adding item: plasblaster to container right
    Com_MoveInInventory()... now we will remove: plasblaster from: right
    Com_MoveInInventory()... now we will add: plasblaster to: floor
    Com_AddToInventory()... adding item: plasblaster to container floor
    G_ClientInvMove()... server sends information to client about inventory change (NOT FROM the floor):
    G_ClientInvMove()... server sends information to client about inventory change (TO the floor):
    Com_AddToInventory()... adding item: plasblaster to container floor
    BTAxis|ufo: I see a bolter
    BTAxis|ufo: And I can't pick it up

::\* on BTAxis' side there were Com_RemoveFromInventoryIgnore() call for
laser pistol - he picked it up from the floor

::\* on my side, BEFORE SUCH CALL, there were three other calls - two
for bolterrifle

::\* the question is, what caused that

## Dying soldier removes floor-items

- Dying soldier removes floor-items

  - One more bug I've noticed (next to some fo the above) after a quick
    test is the following: drop a few items on the floor and let a
    sodlier get killed in this spot/square -\> all the items are now
    gone.
    - They are not gone IMO - they are there but client does not see
      them. To make sure go there with another soldier and try to put
      big weapons in various places - if the items are there, the server
      won't allow you to do so.--[Zenerka](User:Zenerka "wikilink")
      01:19, 23 April 2007 (CEST)
  - It may very well be related to one or more bugs from above. Will
    test this further --[Hoehrer](User:Hoehrer "wikilink") 02:17, 21
    April 2007 (CEST)
  - When an actor is being killed the G_InventoryToFloor() is being
    called; it should destroy items which does not fit to the free space
    on the floor (which is stupid btw. and i take it as temporary
    behaviour); i suspect that the problem is G_GetFloorItems() being
    called from G_InventoryToFloor()... in case it returns null, we
    have: floor = G_SpawnFloor(ent-\>pos) which - of course - would mess
    with the items on the floor--[Zenerka](User:Zenerka "wikilink")
    01:19, 23 April 2007 (CEST)
    - this is needed - there maybe are already items on the floor - so
      there is already a container entity at that pos - if so, we only
      want to add the actors items to this container.
      -[Mattn](User:Mattn "wikilink") 07:19, 23 April 2007 (CEST)

<!-- -->

- I think this is also fixed (at least the few cases I checked) with
  r7954 in trunk. See below. --[Hoehrer](User:Hoehrer "wikilink")

## Reproduceable "light armour" bug

- Reproduceable bug [inv01.log](http://mattn.ninex.info/files/inv01.log)
  (in **2.2-dev**) --[Hoehrer](User:Hoehrer "wikilink")

  - Summary: Drop something to ground, then move it a few squares to the
    left/right.
  - And I think I know why the light armour (among other things) is
    often displayed even if it isn't existing in the current game ...
    the index of the light armour seems to be the first (0) :)
    --[Hoehrer](User:Hoehrer "wikilink")
  - The debug messages in inv01.log are the output that the server gives
    ... so the data at server-side looks very good to me. The
    client-side may be screwed up though.
    --[Hoehrer](User:Hoehrer "wikilink")

--[Hoehrer](User:Hoehrer "wikilink")

Ok, what happens right now in the code (mainly `G_ClientInvMove`):

- Player: drop a weapon to the floor.
- server+client: a floor-container is created in server and sent to the
  client (ent-number xxx) as well.
- Player: move an item inside the floor (inv-menu still open; same
  round)
- server: the item is moved ok (ent xxx) and info is sent to client
- client: the floor (ent xxx) does not exist anymore.

There just _has_ to be code somewhere that sends an `EV_ENT_PERISH`
event to the client. It's just a matter of finding it and check why it
sends it.

My suspicion would be `G_AppearPerishEvent` -\> wrong
visibility-setting/check of the floor? (called indirectly via
`G_CheckVis` when `newFloor` is true in `G_ClientInvMove`) ... but the
code just gets confusing here.

--[Hoehrer](User:Hoehrer "wikilink") 13:17, 26 April 2007 (CEST)

Ok, `CL_EntPerish` isn't called anywhere according to my last debugging
info: [inv03.log](http://mattn.ninex.info/files/inv03.log). But
**something** has to delete the edict again, since it looks like it is
created correctly (see the successful InvAdd after the Appear). This is
getting slightly annoying.

--[Hoehrer](User:Hoehrer "wikilink")

Revision 7954 in trunk should fix this bug. Some edicts are set to
"ent-\>inuse = false" so they are not found when adding items in
mid-move. Needs some testing, but I'm sure this is quite an improvement.

--[Hoehrer](User:Hoehrer "wikilink")

## Grenade bug in internet games

It has been confirmed in internet games only, no LAN games or
singleplayer. See below for more.

To reproduce: move a grenade from backback, belt, holster etc. to a
hand-slot.

The problem: a "ghost" image of the grenade will stay in the original
position. The server gets the info correctly.

This is very similar to a bug zenerka fixed recently, but this time it
seems to be network-lag depending or something along this line.

--[Hoehrer](User:Hoehrer "wikilink") 16:14, 27 April 2007 (CEST)

Some thoughts by mattn:

- could be related to `CL_ParseEvent` and the event timetable
- some events might get lost somewhere, they are sent for sure.
- could also be happening on slower computers

Should be fixed with the new netcode --[Mattn](User:Mattn "wikilink")
12:04, 22 November 2007 (CET)

[Category:Contribute](Category:Contribute "wikilink")
[Category:TODO](Category:TODO "wikilink")
[Category:Development](Category:Development "wikilink")