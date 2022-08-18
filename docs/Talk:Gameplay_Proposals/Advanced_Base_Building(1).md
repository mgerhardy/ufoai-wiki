What about just let the user place the entrances to neighboring
buildings and place walls where there are no entrances. This would not
need much changes but would also allow to structure the base to be
defended more easily. Of course all buildings would still need to be
reachable.

- This is not easy to do. The nature of the maps is such that this isn't
  a practical way of doing things. And even with basic functionality, it
  would be a lot of work to make all the different map tiles.
  --[BTAxis](User:BTAxis "wikilink") 15:12, 28 September 2007 (CEST)
  - I have to admit that I have only limmited clue about the engine, but
    I would suggest to just add 3 spaces between the existing buildings
    and either place an wall or an tunnel element between them. So 5 new
    elements would be needed: Wall h/v, Tunnel h/v, 3x3 Square. As the
    engine should already support placing map pieces it should be quite
    easy to implement - or at least much easier that the suggestion on
    the main page. Although the result is not as beautiful as a hand
    planned base, one could argue that the base buildings are planned
    for further extention and for adding connections between building
    when needed. --[Ffesti](User:Ffesti "wikilink") 16:08, 29 September
    2007 (CEST)

Additionally there could be "blast doors" that are shut and sealed in
case of an attack. Soldiers in sealed areas cannot leave and don't need
to be killed by the attackers to win the base. There could also be
lighter doors that are operated from the command center, but can be
breached by the invaders (may be using an yet to introduce
weapon/explosive). Of course alien bases would protect themselves in a
similar way.

- Again, this is not easy. I experimented with blast doors in the
  shelter map, and I ran into all sorts of problems. The most notable
  problem is pathfinding. It can only find a route over a fairly short
  distance (some 30 spaces, I believe). That means the game can't know
  which areas are sealed and which aren't. I have proposed a macro
  pathfinding algorithm that can find paths over large distances, but
  that wouldn't really be useful for this.
  --[BTAxis](User:BTAxis "wikilink") 15:12, 28 September 2007 (CEST)