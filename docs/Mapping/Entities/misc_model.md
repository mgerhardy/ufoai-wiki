![](Entity_misc_model_settings.png "Entity_misc_model_settings.png")

## Models

To add a model right click on any 2D view window to bring up the Context
menu. Choosing 'Create model' will open the 'Model Selector' screen.
These folders contain all models (\*.md2 or \*.md3 files) available, but
not all of them are usefull for maps. The map models are in the
directory (if you are using a working copy of the repository) or the
pk3-file (if you are using an installer).

With the model selected, open the 'Entities' tab in the sidebar. onto
the properties window will open the dialog window. This way you can add
or remove properties for the model.

The spawnflags property is used to set levelflags for the model. Note
that models with no levelflags set do not appear at all (whereas brushes
with no levelflags set will be shown on every level).

## Keys

- **model**: arbitrary .md2 file to display
- **origin**: the position of the model
- **spawnflags**: level flags etc
- **skin**: the number of the skin attached to the model (default 0)
- **angles**: direction of the model \[pitch yaw roll\]
- **modelscale_vec**: scale of the model (vector of 3 values)
- **anim**: if this is this an animated model you can set the animation
  name from the \*.anm file here
- **frame**: frame nummer (default 0) - use frame or anim - but not both
- **tag**: the tag to place the model to (a target of a misc_model must
  be given, too)
- **targetname**: the id of this misc_model in case you want to place a
  tag
- **target**: the target must match the given targetname of the parent
  misc_model entity

## Links

- [Entitylist](Mapping/Entities "wikilink")

[Category:Contribute](Category:Contribute "wikilink")
[Category:Mapping](Category:Mapping "wikilink")
[Category:Entity](Category:Entity "wikilink")