![](Entities_settings.jpg "Entities_settings.jpg")

## General

A **func_breakable** will mark a brush as being destroyable. To turn a
brush into a **func_breakable**, select it and right click on the brush.
Select **Create entity** and choose **func_breakable** from the list.

Now you can go to the Entity side panel (shown right) to modify the
entity.

Don't forget to set the [levelflags](Mapping/Levelflags "wikilink") as
needed.

## Keys

- **health** : define the needed damage to destroy this brush.
- **particle**: [particle](UFO-Scripts/ptl_*.ufo "wikilink") id
- **material**: material id (glass = 0 (default), metal = 1, electrical
  = 2, wood = 3)

## Warning

Always use only one brush when converting to func_breakable. Otherwise
the bounding box might screw up the pathfinding. See the screenshot for
more information. Also don't copy func_breakables - might lead to one
entity with more than one brush. Also don't copy func_breakable objects.
This will also be in the same object. Thus the bounding box will
increase with every copy to move in the world. The same counts for the
[func_door](func_door "wikilink") entity.

![Image:Func_breakable_1.png](Func_breakable_1.png "Image:Func_breakable_1.png")

## Links

- [Entities](Mapping/Entities "wikilink")

[Category:Contribute](Category:Contribute "wikilink")
[Category:Mapping](Category:Mapping "wikilink")
[Category:Entity](Category:Entity "wikilink")