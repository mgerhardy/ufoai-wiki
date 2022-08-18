## Multiplayer Game Types

This is a proposal for more multiplayer game types.

### Introduction

As it stands, we have two game types in multiplayer. The first is
deathmatch, the second is team deathmatch. I feel the game could be made
a lot more versatile if we expanded the amount of game types, because
differnt game types mean different ways to achieve victory, which means
using different strategies with the same basic means.

The different game types will, of course, have to be coded. Checks have
to be made and new map elements may need to be introduced to the game as
well as the editor. It may not have the highest priority, but I strongly
believe it will be worth the time and effort.

### Game Types

- **Deathmatch**

This game type we have already. The goal is to destroy all enemy
soldiers before all your soldiers are destroyed.

- **Team Deathmatch**

This game type we have already. The goal is to destroy all enemy teams
before your team is destroyed.

- **Assault**

In this game type, one team takes the role of the defenders while
another team takes the role of the attackers. The attackers must bring
at least one soldier to a certain area of the map within a set number of
turns to win. The defenders must either destroy all attackers, or
survive the set number of turns.
The defenders should have a disadvantage in numbers. For example, they
could only have four soldiers while the attackers have eight. On the
other hand, the defenders should have an advantage when it comes to
terrain. Their "fort" should be easy to defend.
This game type will require code (to check for the victory conditions,
as well as the imbalance in numbers) and possibly specialized maps,
though some existing maps could be adapted for the purpose.

- **Team Swarm Defense**

This is a game type that pits one or more human players against the
computer, much like the current "cooperative" variant on Team
Deathmatch. In this game type, the player(s) are given a central,
fortified position. Each turn, a number of armed hostile soldiers are
spawned somewhere on the map, who then proceed to attack the players. To
win, the players must survive for a number of turns.
This game type will require code (to check for the time limit victory
condition as well as a specialized "aggressive" AI) and specialized
maps.

- **Infiltration**

In this game type, one player takes on the role of the infiltrator, and
the other player takes on the role of the police. The infiltrator only
gets a single soldier, the police gets more. The infiltrator's goal is
to reach a certain area of the map. This area, as well as the starting
position of the infiltrator, are variable. Furthermore, the infiltrator
can always see the entire map, including the police soldiers. The police
player's goal is to kill the infiltrator before he reaches his goal. The
police player does not know where the goal is. The police player also
does not know where the infiltrator starts. Furthermore, the police
player follows the normal line of sight rules.
This game mode requires code (to check victory conditions, to account
for the imbalance in numbers, to allow the infiltrator to "cheat" and to
randomize the locations on the map. Aditionally,
[visibility](Gameplay_Proposals/Visibility "wikilink") support will be
essential to this game type). Existing maps can easily be used for this
game type.

- More?

Please use the talk page to suggest more game types. Game types must
provide a real alternative to the ones described above, so don't
propose, for example, Capture The Flag, since that's just the same as
Deathmatch with an extra victory condition that's never going to be met
in practice.

[Category:Proposals](Category:Proposals "wikilink")