## Generic information about the AI

The AI is a score maximization algorithm that performs a depth-first
complete search over the tree of possible actions. There's a catch here
ofc, it doesn't calculate the entire set of possible gamestates (that'd
be a whole lot larger than the chess tree), it just takes turns for each
of it's actors and creates/searches/executes a tree for all possible
moves only for this turn. Given that the outcome of a shot is
non-deterministic (we can't know it's result prior to taking it), the
scoring algorithm evaluates damage dealt with some human-like metrics:
'is it worth it?' etc. A whole series of other metrics like 'did I get
to hide well enough?' are also added ontop of the possible damage metric
to give us the final score for each of the tree's leafs.

## Alternative AI

In this topic, we're discussing the default C-based AI used by default
in the game. There is also a [LUA-AI](LUA-AI "wikilink") that has some
support, but it is not yet considered functional.

## Cheating

Here are the basic 'cheats' that the current AI employs in order to give
it some boost in performance:

- It will know if a target will be visible and shoot-able from a
  position before visiting that spot. update: This may not be entirely
  true
- (minor) The AI will not consider moving to a spot occupied by another
  entity, even if said entity is not yet visible.

## A walk-along with diagrams

Here we will take a look to the core AI functions, all included in
src/game/g_ai.c The diagrams are also available as an ArgoUML project
file in the contrib folder of the svn. You can spot the keyword
'IMMEDIATE' in some parts of the AI. This is done to differentiate
between the thinking part and the execution part of the algorithm. We
will only be referring to sane alien behaviour here, leaving
insane&civilian units out of the picture.

### AI_Run

This is the main entry point for the AI, called once for each Server
Frame (function immediately exits for all but %10 Server Frames). All
that happens here is getting to call AI_ActorThink() for each of the
actors of the currently moving ai team.

### AI_ActorThink

This can be considered the main AI function for every actor.
![<File:AI_ActorThink.png>](AI_ActorThink.png "File:AI_ActorThink.png")
The main reason of existence for this function is the execution of the
shooting & final hiding parts of the best found action. When
AI_PrepBestAction has returned, the actor has already moved to a
shooting position if needed. The diagram is pretty self-explanatory.

### AI_PrepBestAction

This part of the code calculates all the possible moving positions for
the actor and requests the scoring of what can happen from that
position. It finds the best (by score) spot to move to with it's
resulting actionSet (like move there, shoot that, then move over there)
and executes only the moving part.
![<File:AI_PrepBestAction.png>](AI_PrepBestAction.png "File:AI_PrepBestAction.png")

Pretty clear-cut I believe. Notice the dual-path of scoring. I believe
the right one is the traditional one and the left one was added for
supporting mission targets. Do we even have mission targets in the game?
At least we got support for those ;)

### AI_FighterCalcBestAction

This function is called once for every possible spot each actor can move
to. At the search tree we're at the last level of nodes before the
leaves start. The whole goal of this function is to find what's best to
do from a position. This usually entails shooting someone, but it may
end up being just a nice hiding spot. All of the action completion and
scoring happens here aswell.
![<File:AI_FighterCalcBestAction.png>](AI_FighterCalcBestAction.png "File:AI_FighterCalcBestAction.png")
This is where it gets kinda complicated. Don't get confused at the 2nd
level of cute baloons. I didn't know how to depict this properly without
creating a huge diagram. I'm only trying to depict a set of nested
while's there. It essentially says
foreach_possible_target{foreach_possibly_firestyle{calculate_damage}} to
find the maximum damage possible. So, we can see that the basis and
first hint at the scoring system is the possible damage dealt. After
applying some of the bonii/malus to the damage expected, we have a
semi-complete action (up to now it only had a moving part from
prepBestAction) and it's basic scoring. I say semi-complete because we
may end up adding more moving to it by the end of this function. After
this we start adding/subtracting scores according to some principles we
make our fluffy little aliens like: hide, hide, hide and then try to
close in the distance.

## Values that heavily impact the AI

src/game/g_ai.h contains a set of \#def's that start with 'GUETE'. These
heavily influence the score each leaf of the tree receives, and thus the
preferred action. The rest of the \#def's are also included in the
calculations, but have a much smaller impact.

## Discussion

This wiki page is a short version of the first post of the following
thread: <http://ufoai.ninex.info/forum/index.php?topic=5056.0> All
questions, notes, requests and general information can be forwarded
there.

## Development

The AI is currently being reviewed and expanded wherever possible. The
following page contains notes on the updates of the development trunk:
[Combat AI development](Combat_AI_development "wikilink")