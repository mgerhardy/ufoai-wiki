## Macro Pathfinding

<font color="#FF0000">This article is obsolete. ffesti has implemented a
Dijkstra algorithm that can plot routes over large distances quickly, in
most cases.</font>


Just FYI:
If you are speaking about this patch here: ** Implement Dijkstra
algorithm for Grid_MoveCalc**
This is not yet in the game, but will be as soon as some minor things
are solved I imagine. --[Hoehrer](User:Hoehrer "wikilink")


It is in now. --[BTAxis](User:BTAxis "wikilink") 22:33, 13 December 2007
(CET)

Currently, AI pathfinding suffers from a range limitation. This range
limitation is rooted in the amount of CPU time necessary to calculate
the path, and in the byte size. This range limitation also applies to
human-controlled soldiers. A good way to visualize this is by turning on
order confirmation in the options and experimenting with how far you can
set the path. This limitation is referred to in this article as the
"short-range pathing range".

This article describes a system that will allow for AI pathfinding
across large distances (large being defined as larger than the
short-range pathing range). With this system, the AI will be able to
find its way around obstacles and through mazes. This is especially
important on random map assemblies, because the terrain layout on random
map assemblies is uncertain until the game has assembled one.

This system is a generalization of the civilian waypoint system that has
already been implemented. This system allows civilians to follow a long
path to a destination by short-range pathing towards the next highest
priority waypoint in range. To extend this to be dynamic, the following
conditions must be met:

- Waypoints placed on the map must not have a priority value assigned to
  them at compile time.
- Waypoints placed on the map must be in short-range pathing range of at
  least one other waypoint, preferrably more than one. This is the
  responsibility of the map makers.
- Every actor on the map must have a table of waypoints with priority
  values assigned to them.
- It must be possible to update the waypoint table ingame.

## How it works

In order to allow the AI to use the waypoints, the waypoints must be
connected to a graph. In the graph, each node is a waypoint and nodes
will share an edge if the two waypoints can find a path ot each other
using the short-range pathing algorithm. This graph is constructed at
load time. For random assemblies, it must happen after the assembly is
complete. Note: on map assemblies it is VERY IMPORTANT that waypoints
try to find waypoints outside their own tile!

With the graph in place, actors can be assigned their waypoint tables.
When the AI moves an actor, it can do so in two ways:

- Locally. The AI moves the actor as it does in the current game. The AI
  should choose to move locally if:
  - There are no waypoints within the search radius (the search radius
    should reflect the short-range pathing range). Ideally, this
    shouldn't happen.
  - Enemies are in the area, and movement should focus on combat.
- By waypoints. The AI will use the waypoint graph to find a route to a
  remote destination.

When the AI moves by waypoints, it should first decide where on the map
it wants the actor to go.\* For example, the actor could be on a mission
to free aliens from Alien Containment. In that case, the AI will select
a waypoint on the Alien Containment map tile. Next, the AI gets a list
of the waypoints inside the search radius of the actor. Finally, the AI
uses the waypoint graph to plot the shortest route (in the graph, not on
the map!) from the destination waypoint to all of the waypoints near the
actor. If there are multiple shortest routes, it just picks one. Given
this path in the graph, the actor's waypoint table will be updated with
new waypoint priorities, starting with the waypoint near the actor that
is part of the path and ending at the destination waypoint. All other
waypoints will be given priority -1 (or some other value - magic numbers
are against the coding policy). The AI will then proceed to move the
actor towards the waypoints analogous to the civilian waypoint system.

<FONT SIZE=1>\* Deciding where the actor should go is a whole different
story. However, the point is that wherever it does choose to go, it will
be able to find its way there efficiently.</FONT>

## Algorithms and data structures

The following is a description of some of the algorithms and data
structures inolved, including pseudocode. Whenever an identifier uses
underscores, like next_node, that means it's an abstract for a more
correct coding syntax, used for better readability.

### Graph representation

The graph is represented by an array of structs. Each struct represents
one waypoint, and contains a list of waypoints within short range
pathing range.

    typedef struct graphNode_s {
      edict_t *thisWaypoint; /**< This should directly reference to the waypoint entity. */
      /* Arrays are of size 16 here. It is unlikely that there are that many waypoints in range of each other, but it still calls for robustness. */
      struct graphNode_s *nodesInRange[16]; /**< elements in the overall array of nodes. */
      int distanceTo[16]; /**< each element holds the pathfinding distance to the node referenced to by nodesInRange with the same index. */
      int distanceFromActor; /**< used only when copied when the path must be found.
    } graphNode_t;

    /* 256 waypoints is probably a good limit */
    graphNode graph[256];

### Waypoint numbering

Each waypoint entity has a variable that represents the index in
graph\[\] that references this waypoint (inverse referencing).

    int indexForThisWaypoint;

### Waypoint representation per actor

Each actor has a single array that represents all waypoints on the map.
Each element of the array represents one waypoint. The waypoint
referenced by a given index is the same waypoint referenced by graph\[\]
with the same index. The value of the element is the waypoint's priority
for that actor.

    int waypoints[256];

### Building the graph

As stated above, the graph is constructed when the map is loaded. Note
that the following pseudocode abstracts from exactly how the list of
candidate waypoints is retrieved, as well as from how the pathfinding
involved is called.

    /* First we must link the waypoint entities to the graph data struct: */
    for (waypoint_entities_on_the_map) {
      waypoint.indexForThisWaypoint = counter;
      graph[counter].thisWaypoint = this_waypoint;
      counter++;
    }

    /* Next, we build the actual graph. */
    for (waypoint_entities_on_the_map) {
      candidate_waypoints[] = getCandidateWaypoints(this_waypoint);
      for (candidate_waypoints) {
        if (temp = pathTo(this_waypoint, candidate_waypoint)) {
          graph[this_waypoint.indexForThisWaypoint].nodesInRange[nodes_index] = candidate_waypoint.indexForThisWaypoint; //Save edge
          graph[this_waypoint.indexForThisWaypoint].distanceTo[nodes_index] = temp; //Save length of edge
        }
        else {
        /* Do nothing. This node does not share an edge with the candidate node. */
        }
      }
    }

    int pathTo(entity, entity) {
      !! Black box! I know nothing about how pathfinding works, so this is left as an excercise to the coder. !!
      /* return -1 if the pathfinding code can NOT find its way from the first waypoint to the candidate waypoint. Otherwise, return the pathfinding distance. */
    }

    entity[] getCandidateWaypoints(waypoint) {
      !! Black box !!
      /* return an array of waypoints that are within "candidate range" */
    }

### Finding a path in the graph

The following assumes a destination exists. The graph used here is a
temporary copy of the one built at load time and is discarded once the
path has been found.

    int nextNodes[] = setStartWaypoints(this_actor);
    graphNode tempGraph = graph; //Make a copy.
    memset (this_actor.waypoints, 0); //clear out previous path
    if (sizeOf(nextNodes) == 0) {
      /* No nodes in range! Local movement. */
    }
    else {
      /* First a one-off bootstrapping loop that sets the distance to the starting waypoints from the actor. */
      for (nextNodes) {
        tempGraph[next_node].distanceFromActor = pathTo(this_actor, tempGraph[next_node].thisWaypoint);
        /* Mark these as the starting waypoints. starts holds indices for tempGraph[]. */
        int starts[starts_index] = next_node;
      }
      /* Now for a more iterative process: Expand the "walked" part of the graph and mark the nodes with their total pathing distance. */
      for (nextNodes) {
        for (tempGraph[next_node].nodesInRange) {
          /* Now comes a tricky bit. The node in range is updated to be the next "step" when it hasn't been walked yet,
           * OR when it has but the previous path to it was LONGER. This allows us to find the shortest path.*/
          if (tempGraph[node_in_range].distanceFromActor > tempGraph[next_node].distanceFromActor + tempGraph[next_node].distanceTo[index_of_nodesInRange]) {
            tempGraph[node_in_range].distanceFromActor = tempGraph[next_node].distanceFromActor + tempGraph[next_node].distanceTo[index_of_nodesInRange];
            newNextNodes[n3_index] = tempGraph[node_in_range];
            n3_index++;
          }
          else {
            /* Do nothing. The node in range was already pathed with a path that was as long as or shorter than the one we're attempting. */
          }
        }
        nextNodes = newNextNodes; //copy the next iteration to newNodes
        memset(newNextNodes, 0); //empty
        n3_index = 0; //reset
      }
    }
    /* This process terminates. When it has, the shortest path from the actor to the destination waypoint is known,
     * and the destination waypoint knows how far it is from the actor. Now all we have to do is walk back to the
     * actor by steepest slope approach: */

    int priority = 1; //1 being the destination priority in this case.
    int nextNearest = destination_index;
    while (!elementOf(destination_index, starts)) {
      this_actor.waypoints[nextNearest] = priority;
      priority++;
      int newNextNearest = tempGraph[nextNearest].distanceFromActor;
      for (tempGraph[nextNearest].nodesInRange) {
        if (newNextNearest > tempGraph[index_of_nodesInRange].distanceFromActor) {
          newNextNearest = tempGraph[index_of_nodesInRange].distanceFromActor);
        }
      }
      nextNearest = newNextNearest; //Choose the node that is next nearest the actor as the next step in the graph
    }
    this_actor.waypoints[nextNearest] = priority; //This one is for the starting waypoint, which is skipped by the while loop.

    /* Done! The actor now has priorities assigned to the waypoints. */

    int[] setStartWaypoints(actor) {
      !! Black box !!
      /* return an array of indices for tempGraph[]. The indices are for those waypoints that this actor can path to. */
    }

    int elementOf(int, int[]) {
      /* Elementary. Returns 1 if the first argument is an element of the second argument, 0 otherwise. */
    }