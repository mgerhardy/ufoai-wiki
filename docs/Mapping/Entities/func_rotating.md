![](Entities_settings.jpg "Entities_settings.jpg")

## General

- The object needs a rotation origin - e.g. we have to know at which
  point we have to rotate the object. This is done with a so called
  origin brush. Place this brush as axis and assign the texture.
- Make sure that both the object and its origin brush are part of the
  same func_rotating.
- Also see the warning about extending bounding boxes in
  [func_breakable](func_breakable "wikilink").
- **origin**
  [contentflag](Mapping/Surface_fields#Content_flags "wikilink") has to
  be set for the origin brush. This is being done automatically by
  ufo2map during the compilation phase for faces that have origin
  texture, but there's no harm in assigning the flag in Radiant as well.
- Don't forget to set the [levelflags](Mapping/Levelflags "wikilink").

## Keys

- **health** : damage until destroyed
- **particle**: particle id
- **speed** : The rotation speed in degrees per second
- **angle** : rotate around this angle - pitch = 0, yaw = 1, roll = 2

## Links

- [Entities](Mapping/Entities "wikilink")

[Category:Contribute](Category:Contribute "wikilink")
[Category:Mapping](Category:Mapping "wikilink")
[Category:Entity](Category:Entity "wikilink")