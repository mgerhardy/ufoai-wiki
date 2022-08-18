## General

This is a sliding door. It's a brush entity. The sliding brush must hide
in other brushes once the door is opened (that's also the reason why an
upward opening for the z-axis is not supported, it would be visible for
higher levels).

## Keys

- **dir**: This is a bitmask of the axis and the direction the door is
  opening into.


Possible values are:

\* 6 and 10 (x-axis, left and right)

\* 5 and 9 (y-axis, up and down)

\* 3 (z-axis, down) (no up supported)

- **noise**: Sound that is played once the door opens or closes

## Links

- [Entities](Mapping/Entities "wikilink")

[Category:Contribute](Category:Contribute "wikilink")
[Category:Mapping](Category:Mapping "wikilink")
[Category:Entity](Category:Entity "wikilink")