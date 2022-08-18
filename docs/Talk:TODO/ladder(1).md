Just some random thoughts about climbing ladders:

- Do we allow shooting when the unit is located *on* a ladder?
  - If not wouldn't it be best to only let a unit climb a ladder if it
    has enough TUs to climb all of it? -\> No unit will ever be 'stuck'
    on it.
    - exactly what you wrote - there is no possible to "stuck" on the
      ladder, because in any point an actor cannot stop "on the ladder";
      when he has enough TUs he climbs, when he does not, he cannot
      climb--[Zenerka](User:Zenerka "wikilink") 15:34, 7 August 2007
      (CEST)
    - Ok, just what i thought then.
      - What about RF? Will that properly fail to trigger?
        --[BTAxis](User:BTAxis "wikilink") 16:14, 7 August 2007 (CEST)
        - Since this means we do not let people stay on the ladder on an
          enemy turn no RF will every be triggered (on our side). At
          least that is the plan, I'm sure there are people who would
          want this (staying on a ladder) though ;)
          --[Hoehrer](User:Hoehrer "wikilink") 16:31, 7 August 2007
          (CEST)
          - RF doesn't trigger on \*your\* turn. So while the enemy
            climbs the ladder on their own turn, \*we\* might shoot. And
            vice versa. It's not about staying on the ladder, it's about
            shooting while someone is climbing.
            --[BTAxis](User:BTAxis "wikilink") 16:53, 7 August 2007
            (CEST)
            - Yes, I know when RF is triggered. Why would we *not* want
              to shoot climbing enemies with RF? The only thing we need
              to make sure is to prevent people that are currently
              climbing the ladder to shoot. If that is not what you
              meant I really do not understand your point right now - I
              hope to be online on IRC later this afternoon so we can
              discuss this. --[Hoehrer](User:Hoehrer "wikilink") 17:04,
              7 August 2007 (CEST)
              - Oh, so that's not a problem. For some reason, I thought
                firing at climbing enemies would be problematic with
                aiming and death animations and falling corpses and
                whatnot. But if that's not the case then all is well.
                --[BTAxis](User:BTAxis "wikilink") 17:05, 7 August 2007
                (CEST)
              - I understand your point, now thanks for pointing this
                out. Animations will look wrong as long as we do not
                make new ones. Letting the corpse fall down is quite
                possible from the code-side of view. Since we need
                animations for climbing as well it's more very likely
                that we'll include stuff like this ("falling dead from a
                height" and "hit while climbing" animations) as well as
                soon as we can animate all the (older) models. Until
                then we *could* just use dummy animations for this -
                that's up for debate.
                --[Hoehrer](User:Hoehrer "wikilink") 17:13, 7 August
                2007 (CEST)
- Programming issue: How is this 'climb' information from the brush put
  into pathfinding data (i.e. routing_t struct?)
  - I don't know yet. I hope mattn will give a clue here in the future.
    :-\>--[Zenerka](User:Zenerka "wikilink") 15:34, 7 August 2007 (CEST)
    - I'll have a look at this then. I do not know much about the
      map-compiler though (and the routing/pathfinding preparations in
      it). But as soon as we have information in the routing_t struct
      (not to self: something like `R_CONN_UP` and `R_CONN_DOWN`) I
      think I could manage to hack the map/grid functions to support the
      climbing calculations (TUs). --[Hoehrer](User:Hoehrer "wikilink")
      15:50, 7 August 2007 (CEST)
- Advanced stuff
  - Weight limitations?
  - Elevators? (seperate issue I think?)
  - Checks for actors standing at the destination square?
    - Yes, but does anything change in that? It will be like the current
      situation - if destination tile is not free, stop
      moving--[Zenerka](User:Zenerka "wikilink") 17:26, 7 August 2007
      (CEST)
  - In team play, what if two players want to use the same ladder, but
    the first player ends up obstructing the second player AFTER the
    second player has confirmed his move?
    - Bad luck for the second one and he has to stop before entering the
      ladder, I suppose?--[Zenerka](User:Zenerka "wikilink") 17:26, 7
      August 2007 (CEST)
- animations - so, what new animations would we need? currently i can
  think about:
  - actor climbing
  - actor falling down after being killed at the ladder
  - how about that: if an actor has holdtwohanded weapon, play an
    animation when the actor moves the rifle to the back to make his
    hands free?