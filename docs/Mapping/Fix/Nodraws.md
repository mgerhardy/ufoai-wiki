Each face of each brush has a SURF_NODRAW flag. If it is set, the
renderer knows that it never has to be drawn. This makes rendering
faster.

     ufo2map -check nodraws base/maps/foo

ufo2map will set nodraws automatically in three ways.

1.  If the side is near (at revision 19664, within 10 degrees) pointing
    down, then it will not be shown. (note this currently causes a bug
    in FPV. FPV will be changed or removed in the future).
    ![Image:DownwardSideNodraw.png](DownwardSideNodraw.png "Image:DownwardSideNodraw.png")
    If the angle shown in blue is less than 10 degrees, then the side
    will be set to nodraw.
2.  The side is pressed flush against another side that is the same
    shape, or larger.
    ![Image:SingleBrushAutoNodraw.png](SingleBrushAutoNodraw.png "Image:SingleBrushAutoNodraw.png")
    Here the dark brush has a side that will never be drawn.
3.  The side is pressed against a composite face.
    ![Image:CompositeSideAutoNodraw.png‎](CompositeSideAutoNodraw.png‎ "Image:CompositeSideAutoNodraw.png‎")
    The sides of the line of three brushes abut. These form a composite
    side, which prevents one of the sides of the dark brush from ever
    being rendered. Note that most terms in UFO:AI rendering are common
    with other Quake-derived engines, but I made up "composite side".

[Category:Mapping](Category:Mapping "wikilink")