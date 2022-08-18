Can/will or are we willing to extend this mechanism also to include
other events? Like elevators, moving vehicles in a convoy, water running
out of broken reservoir, engines flaring, cows on the loose, ...
[Punkiee](User:Punkiee "wikilink") 14:44, 5 January 2008 (CET)

Looking at the technical structure behind the "timed events" these are
two different things. What you describe here are generic "animations"
(which of course also have to be timed loosely) but are not dependent on
round numbers (Some stuff for such animations also need to be still
running in the next round, but it can be made more general), square of
the map and (mostly) have no influence on the gameplay/game-mechanics. I
could go into more detail here, but it boils down to that the basics are
very different :)

If we are going to implement stuff like this I guess we'll use something
that matches the requirements for animations/triggered events/etc...
better. No promise, just a technical statement. ;)

Also: IIRC elevators may already be possible, but I think mattn has more
info on that.

--[Hoehrer](User:Hoehrer "wikilink") 18:30, 6 January 2008 (CET)