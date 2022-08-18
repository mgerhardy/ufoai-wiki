In order to have your map cutaway at different levels in the game, you
have to give all of your brushes and some of your entities level flags.

To set a level flag for a brush, go to the
[Mapping/Surface_inspector](Mapping/Surface_inspector "wikilink")
sidebar and find the level flags. You can click to set which levels the
brush should appear on. **This must be set for the whole brush. You can
not set some faces of a brush to appear on a level and some faces to not
appear on that level.**

For some entities, [func_breakable](func_breakable "wikilink"),
[misc_model](misc_model "wikilink"), and
[misc_particle](misc_particle "wikilink"), you will need to set level
flags. Go to the [entities panel](Mapping/Entities "wikilink"). Now, you
can either select the entity in one of the views, or find it in the tree
of entities listed in the sidebar. Once selected, you will see
checkboxes to select the levels.

## Tips and Best Practices

- You must set the flag for all levels you want an object to appear on.
  Just because you've set your road to appear on level 1 doesn't mean it
  will appear on level 2.
- To improve the performance of your map, it's always a good idea to not
  show brushes and entities that can't be seen. For instance, if you
  have a chair inside of a room on level 1 and it's not visible when the
  player is looking at level 2, you should only assign level 1 to the
  chair. That way the engine can hide it when it can't be seen, and
  there will be less for the engine to handle at once.

## Tutorial

Here are some [step-by-step
screenshots](Mapping/Tutorials/Levelflags "wikilink") to show you how to
handle the levelflags.

## Links

- [Surface inspector](Mapping/Surface_inspector "wikilink")

[Category:Mapping](Category:Mapping "wikilink")
[Category:Contribute](Category:Contribute "wikilink")