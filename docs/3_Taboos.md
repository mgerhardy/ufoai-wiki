### 3 Taboos

There are 3 things in UFO:AI which are often asked for by new users:
battlescape saves, destructible terrain and engine switch. These things
have been discussed to death on the forums and most devs are really
tired of talking about them, because those three things simply will not
happen in UFO:AI. Here is why:

## Battlescape Saves

The dev team made an 'eternal' design decision not to offer this feature
many years ago.

Of course missions can take rather long - several hours for beginners -
and there is of course the wish to interrupt a battle without losing the
progress you made if you need to work the next day. But if there was a
way to save in the middle of battle, it could also be abused to
'scum-save' your way through the battle, exploiting the randomness of
the shots. And not the smartest mechanism could keep them from doing
that.

Also the lack of saves is said to add to the atmosphere, making your
decisions much more important to your soldiers.

Besides all that, we are talking about quite a lot of additional coding,
because the status of a battle is describe by many parameters that are
not needed in normal saves.

Interestingly, nobody ever came up with a mod/patch that implements
these saves.

## Destructible Terrain

It's weird if you throw an incendiary grenade and the aliens are fried
in their armour and die eventually, but the wooden shack and the small
bush nearby come out of this event without a scratch. But if some things
are destructible, everything you see must be more or less destructible,
or we'll get an inconsistent playing experience. We already made
exceptions for glass and doors, but they cause more than enough
problems.

When something is destroyed, we need to show the broken remains of the
item. So for everything destructible in the maps, we need the artwork
for its broken state. And it's not just one state. A destroyed item will
look very different depending on how it was destroyed. Projectiles,
explosives, fire,...you name it.

As you probably know, our maps are pre-compiled. This process takes
several hours for all the maps and can take up to 20 minutes for a big
single map. This is done to do certain calculations in advance, because
a player wouldn't want to wait for them to be done at runtime. The most
prominent among those things are routing/pathfinding and lighting.
Modern hardware is able to do the lighting 'on the fly', but there is an
old 'eternal' decision that UFO:AI should not rely on fancy hardware. So
after a map is loaded, most of the routing and lighting is static.

After you have blown a big hole into the wall of a building, you will
want to walk through that hole. And you would expect the sun to shine
though that hole. That is, both the routing tables and the lightmaps
(which we thought to be static) will need adjustments, which defeats the
purpose of pre-calculation. More than that, several parts of the code
rely on the destinction between static and dynamic parts of the map.

## Engine Switch

This was never seriously discussed, but instead was used in statements
like "if your engine doesn't support that, why don't you switch to XYZ,
they can do it". Users (and even devs) typically underestimate the
effort needed to migrate an existing application from one engine to
another. You end up with a 80-90% rewrite. And 'rewrite' does not just
refer to the code but - more important - to the artwork.

If there was a dev who made a prototype based on Ogre, idTechX or
whatever that shows a little map with a soldier, an alien, a weapon and
a few buildings which proves that everything is oh so much better with
that engine, several ufoai devs would take a closer look at that
prototype and either drive it to its limits or decide that it's time for
ufoai to switch the engine. Interestingly, nobody ever did...