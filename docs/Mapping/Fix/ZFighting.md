     ufo2map -check zfighting base/maps/foo

When brushes overlap and have sides in a common plane, the sides compete
to be drawn. This looks ugly. Note that ufo2map will never be able to
auto-fix this, as there is no way of it knowing which brush to adjust.
![Image:Z-fighting.png](Z-fighting.png "Image:Z-fighting.png")
Stripes that result from z-fighting, rendered in UFORadiant. The
appearance is similar in-game.

Why Z? This can happen if the sides are parallel to X, Y, Z or any
arbitrary plane. Wikipedia mentions a Z-buffer, though I am not sure if
UFO:AI uses those. [wikipedia z-fighting
article](http://en.wikipedia.org/wiki/Z-fighting)

[Category:Mapping](Category:Mapping "wikilink")