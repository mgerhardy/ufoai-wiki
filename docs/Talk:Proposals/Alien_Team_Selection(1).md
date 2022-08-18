In the alien team selection, I'd like some way to specify which aliens
should be able to equip armour. This would allow us to specify a team
that might have armoured tamans, but not armoured ortnoks. This would be
good for balancing the appearance of more difficult alien teams
throughout the game.

What about a new block to the team definition:

`armoured_aliens {`
`   taman`
`}`

--[H-hour](User:H-hour "wikilink") 11:29, 8 June 2012 (SAST)

------------------------------------------------------------------------

What about instead of

`   /*`
`    * Valid alien types`
`    */`
`   aliens {`
`       taman`
`       ortnok`
`       bloodspider`
`   }`
`   `
`   /*`
`    * Equipment to give aliens`
`    * This would reference equipment definitions`
`    * described below.`
`    */`
`   equipment   assault`

We write

`   members {`
`       taman           assault_withalienarmour`
`       ortnok          assault`
`       bloodspider     none`
`   }`

Or

`   members {`
`       taman {`
`                       primary     plasmaweaponset`
`                      secondary   kerrbladeset`
`                     armour      basic_alien_armourset`
`                }`
`       ortnok {`
`                      primary     plasmaweaponset`
`                      secondary   kerrbladeset`
`                      misc        alien_grenades`
`                }`
`            bloodspider {`
`                }`
`       }`

--[Geever](User:Geever "wikilink") 11:54, 8 June 2012 (CEST)

Guys, you are missing the important fact: the way how game code
interprets those scripts; you can find the source in
src/inventory.cpp::I_EquipActor().

To put long story short, if you ever want to change the way NPCs are
loaded, you change the code there, since it holds a hardwired way of
autoequipping combatants.

--[Sandro](User:Sandro "wikilink") 22:54, 10 September 2012 (SAST)

- Yes, we know it will take code changes. That is the idea of this
  proposal. Geever plans to rework it some day, so this was just setting
  down our ideas on the scripting side of it somewhere so they wouldn't
  be lost. --[H-hour](User:H-hour "wikilink") 10:03, 11 September 2012
  (SAST)