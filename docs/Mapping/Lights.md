## Day and night lighting

As of revision 15024, the lightmaps for day and night maps are stored in
the same bsp. You do not have to set the lighting in the worldspawn
anymore - the compiler will do this automatically.

## Surface lights

- Mark the face that should emit light, open the surface inspector (),
  tick the light checkbox and enter the light value in the *value* field
  at the bottom of the surface inspector. Use values \~10000.

## light entity

- **_color**


color for the light [RGB](RGB "wikilink") - this value must be set -
otherwise the light is ignored

- **light**


intensity a value between 1 and 255

- **origin**


the position of the light in the map (is set if you create/move your
light)

- **classname**


light

**Warning** Light entities only work at night by default. If you want to
make them emit light by day as well, you must check the day checkbox on
the entity inspector.

## General

Area lights do not exist in UFO:AI. If you are mapping [random map
parts](Mapping:Random_map_parts "wikilink"), you should read the
suggestions for lights in the articles about [random map
parts](Mapping:Random_map_parts "wikilink").

[Category:Mapping](Category:Mapping "wikilink")
[Category:Contribute](Category:Contribute "wikilink")