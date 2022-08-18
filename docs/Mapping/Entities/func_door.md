![](Entities_settings.jpg "Entities_settings.jpg")

## General

- The door needs a rotation origin - e.g. we have to know at which point
  we have to rotate the door. This is done with a so called origin
  brush. Place this brush as axis and assign the texture.
- Make sure both the door and its origin brush are part of the same
  func_door.
- Also see the warning about extending bounding boxes in
  [func_breakable](func_breakable "wikilink").
- **origin**
  [contentflag](Mapping/Surface_fields#Content_flags "wikilink") has to
  be set for the origin brush. This is being done automatically by
  ufo2map during the compilation phase for faces that have origin
  texture, but there's no harm in assigning the flag in Radiant as well.
- Don't forget to set the [levelflags](Mapping/Levelflags "wikilink").

## Keys

- **angle** : determines the opening direction
- **health**: define the needed damage to destroy the door. Door with
  this parameter set can be both opened/closed and destroyed
- **group**: multipart doors can be grouped to open together
- **noise**: Sound that is played once the door opens or closes

![](Func_door.jpg "Func_door.jpg")

![](Doors_step1.png "Doors_step1.png")
![](Doors_step2.png "Doors_step2.png")
![](Doors_step3.png "Doors_step3.png")
![](Doors_step4.png "Doors_step4.png")

## Links

- [Entities](Mapping/Entities "wikilink")

[Category:Contribute](Category:Contribute "wikilink")
[Category:Mapping](Category:Mapping "wikilink")
[Category:Entity](Category:Entity "wikilink")