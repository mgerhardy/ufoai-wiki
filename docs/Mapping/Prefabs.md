## Creating new prefabs

To integrate new prefabs into the prefabs sidebar of UFORadiant you need
two things - the [map](Mapping/map_file_file_format "wikilink") file and
a screenshot. The screenshot must be in the format 128x100px. Using
in-game screenshots here is prefered. The map is a normal \*.map file
that you can create with the map editor. The only thing you should keep
in mind is that you should align the prefab to the world origin. As an
example see all the other existing prefabs.

### Prefabs for models

The models that can be used in a map are usually located in .

A prefab of a [misc_model](Mapping/Entities/misc_model "wikilink")
should also contain all the clips that are needed.

- One layer of nodraw brushes. It is important that those clips have no
  levelflags set, else they will cause black holes in the world geometry
  when touching other brushes. This layer is used to break both the Line
  of Sight and the Line of Fire.
- One layer of lightclip brushes for the shadows. It is recommended to
  set proper levelflags here. This is not needed for the the
  mapcompiler, but it prevents the clips from getting invisible when
  using the levelselector in UFORadiant.
- Actorclips, to prevent actors from walking into the model. Placing
  those clips should follow the guidlines proposed
  [here](Mapping/Checklist#Brush_alignment "wikilink"). It is
  recommended to set proper levelflags here. This is not needed for the
  the mapcompiler, but it prevents the clips from getting invisible when
  using the levelselector in UFORadiant.

[Category:Mapping](Category:Mapping "wikilink")
[Category:Contribute](Category:Contribute "wikilink")