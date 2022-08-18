This is a proposal for enhancements to multiplayer setup. It is inspired
by the way [UFO2000](http://ufo2000.sourceforge.net/) does things.

## What is the basic idea?

A multiplayer game is played with teams created out of nowhere from the
multiplayer menu. In theory, all equipment in the game is at the
players' disposal. This is fine, but it does invite the player to equip
only the most powerful items. This could be solved by balancing, but
that's not desireable. Weapons that show up later on in the singleplayer
campaign are **supposed** to be stronger than weapons you get at the
start.

The best solution is to introduce a point-based system to the
multiplayer game that puts restrictions on what equipment a player can
take into battle. An unlimited supply of all equipment should be
available to the player, but every piece of equipment, from ammo clips
to heavy suits of armor should have a value assigned to them. When
building a team, the values of all equipment that's equipped on a
soldier will be added together, and this sum will be the Team Cost.

The Team Cost will influence what games that team is allowed to
participate in. A 400-point team will be unable to join a 300-point
game. A player should either re-equip his team to use less points, or
build a different team that does meet the point criteria. The result is
that the player will be forced to make concessions. A powerful suit of
armor on one soldier might mean reduced firepower elsewhere, and taking
Plasma Grenades instead of regular grenades could mean a lack of
IR-vision for the team.

## How would the various parts of the game handle this?

Firstly, let us consider the server-client aspect of things. When
creating a server, a point limit should be set for that game. The value
of this limit should be taken from a set of possible values, for example
100, 200, 300, 400, 600 and unlimited. When a client connects to the
server, it communicates the team the player is using in terms of a list
of equipment. The server will then calculate the Team Cost, and if the
Team Cost exceeds the limit, refuse the client.

Secondly, let us consider the interface.

### Equipment menu

When equipping a soldier, the images for the weapons and equipment
should have their cost displayed in the corner in small yet readable
numbers. The total cost for the current soldier as well as the Team Cost
should also be displayed at all times. This will help the player in
deciding what equipment to add to which soldier.

### Soldier menu

Every soldier should have their individual point total displayed next to
their name. This can be useful when temporarily disabling some members
of the team to meet a point limit.

### Join menu

The list of servers should display the point limit for every game. When
a player tries to connect with a team that exceeds the server's point
limit, a dialog should appear telling the player his team is not allowed
to participate. When a player tries to connect from the console, a
console message will probably suffice.

### Create menu

In addition to the current options, there should be a setting for the
game's point limit.

### Team menu

Saved teams should have their Team Cost displayed next to their name for
easy reference.

## Conclusion

Adding this system or a system similar to what I've described here will
add depth to multiplayer games. More restrictive point limits will
require the players to either field smaller teams or poorly equipped
ones. Of course, for players who like a high-tech slugfest there should
be an "unlimited" setting, so everyone will still be happy.

[Category:Proposals](Category:Proposals "wikilink")