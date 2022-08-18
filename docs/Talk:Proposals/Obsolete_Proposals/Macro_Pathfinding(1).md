## Additional thoughts

Possibly, there could be different *types* of waypoint for the AI in
addition to the regular waypoint that only serves to be part of the
graph. For example:

- Attack waypoints could help the AI determine where strategic targets
  are. Actors that have been given an attack role would randomly select
  one attack waypoint as their destination, attempt to fight their way
  there and destroy wahtever target is in that area. On successfully
  completing their attack mission, they would proceed to the next target
  or if no target was available, revert to the default alien behaviour.
- Defense waypoints could be used by mappers to ensure that the aliens
  spend some of their manpower to defending their own positions. This
  would be especially useful in UFO recovery missions and alien base
  missions. Aliens with a defensive role would proceed to a randomly
  chosen defense waypoint and then idle in that area, reserving their
  TUs for Reaction Fire. Enemies approaching closely enough should be
  engaged.
- Patrol waypoints could be used by mappers to ensure that areas of the
  map are visited by the AI. Actors on a patrol mission would proceed to
  a randomly chosen patrol waypoint and, upon arriving, proceed to a
  randomly chosen other waypoint, repeating the process until they were
  killed or encountered an enemy. This type of waypoint would probably
  not result in a noticeable difference in behaviour of the AI.

The amount of aliens assigned attack, defense and patrol roles should
depend on the mission type and the existence or nonexistence of the
relevant waypoints. --[BTAxis](User:BTAxis "wikilink") 22:11, 19 August
2007 (CEST)

## Alternative Suggestion

I am still quite clueless about the code base, but having a look at
cmodel.c (which I suspect to be the path finding algorithm) I have the
feeling things could more easily improved by switching the algorithm and
not by adding another layer ontop of it.

First thing would be to us [Dijkstra's
algorithm](http://en.wikipedia.org/wiki/Dijkstra%27s_algorithm) instead
of looping over and over again over terrain that's not of interest.
Second step would be to use the [A\*
algorithm](http://en.wikipedia.org/wiki/A%2A_search_algorithm) for long
range path searches or simply any path searches that have a known target
and don't need to create a path map for a whole area. As most maps are
not very mazelike A\* should give quite good results using the [Taxicab
Distance](http://en.wikipedia.org/wiki/Taxicab_geometry) as heuristic.

- Sounds like a good idea. Of course the trouble is finding someone who
  can implement it... By the way, do you think that approach would be
  sufficiently fast for the (time-critical) application of plotting a
  path when the user clicks on a part of the map? A noticeable delay
  here really isn't acceptable. Perhaps using another layer may be
  required to speed up the calculation by doing two short-range plots
  (from actor to nearest waypoint and then from waypoint nearest
  destination to destination) and one long-range plot per a waypoint
  system, as described in the article or by a more efficient means.
  --[BTAxis](User:BTAxis "wikilink") 01:03, 4 October 2007 (CEST)

<!-- -->

- Depends a bit an the layout of the map. A\* is quite good if walking
  into the right direction helps. A\* doesn't like dead ends that have a
  huge area.
  - Shelter is one such map (in fact, it was built around the very
    concept). Other maps are better in this respect, though I don't know
    how maze-like A\* considers large buildings to be, like the one in
    the estate map. Base assemblies may also prove to be a bit
    problematic, especially with advanced base building.
    --[BTAxis](User:BTAxis "wikilink") 12:42, 4 October 2007 (CEST)
- What's the maximum size of a map in squares?
  - I think the maximum is pretty big. I don't know what the largest
    reasonable size is for a map (taking FPS and such into account), but
    it can have at most 8 levels.
- It should be possible to create the path map in the background
  following the mouse cursor or even for the whole map. That way the
  path would be ready before clicking. But this is a bit more tricky.