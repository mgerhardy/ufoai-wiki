### Concept

I think the key in domination is to accumulate points from each target.
Each map should have at least 3 target zones. So it's not a "camp a
single zone" kind of game but one in which you must spread out your
forces. This way, even if a player is down to his last soldier against
an opponent with four, he can still try to sneak around and capture
points. The other player will not be able to simply group all his units
together for safety and count on winning the game.

I imagine it working like this, though it is probably a 2.5 feature:

1\. Map contains 3 or more misc_mission entities (target zones).

2\. When the player enters the target zone, he "captures" this zone and
it turns to the player's color. For a quicker implementation, we can
just have a text display on the UI that says:

Target Zone 1: \[player name\] Target Zone 2: Uncaptured Target Zone 3:
Uncaptured

Each turn that a player controls a target zone, the player gets a point
(if he has two zones, he gets two points, etc).

If both players have a soldier within the zone it should be "uncaptured"

3\. Victory will come when one player reaches a certain score (ideally
the players could choose this when setting up the game) or if one player
kills all the other team's soldiers.

### Domination as Gametype, not Maptype

On a separate note, I really think domination should be an option on a
map. The map I just added will make a good 1v1 or skirmish map in
addition to a domination map, and it's our only properly mirrored
multiplayer map.

### Original questions

Some questions:

1\. What exactly are we setting when we set the time? Amount of time
before what happens?


This is the amount of rounds that you must be the only one in the target
zone to win the game.

2\. Does this mean that a map that has a misc_mission will always be
played in domination mode?


There are other options, not only domination via *misc_mission* - but
currently: if a map has a *misc_mission*, you have to play this
*misc_mission*. But it is no problem to ignore a specific entity on map
loading. So we can e.g. add a multiplayer-only flag to this entity.

3\. How can we configure things like the number of points given per
turn, the number of points that result in a victory, etc? This seems
like something to be chosen through the UI.


This is currently not possible - but we can set this via the UI - and
store it in [cvars](Cvars "wikilink")