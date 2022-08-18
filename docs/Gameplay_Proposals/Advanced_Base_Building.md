## Advanced Base Building

This is a (rather radical) proposal for an enhancement to the base
building part of the game.

When building a new facility, the player should be given the opportunity
to rotate the facility he is placing. All facilities, including the
double-size ones, should have four different orientations. When placing
a facility, the player should be able to rotate that facility by
pressing a button. The image underneath the cursor should rotate to
reflect this.

One of the major advantages of having rotatable tiles is that the tiles
no longer require to have an entrance on every side. It is possible for
facilities to have three or even two entrances (in fact, the command
centre could have only one!), and the player can make sure that the
facilities are always connected. In fact, it is possible to enforce
connectivity by requiring that the facility to be placed has at least
one entrance that connects to the entrance of a facility that has
already been placed.

To indicate where the entrances are, markers should be placed on the
image, Ideally, these markers should only show when the player is
placing a facility.

## Cost

- To realize the rotated map tiles in base defence missions, one of two
  things needs to happen:
  - Code needs to be added that can rotate a map tile at map load time.
    This is difficult, but no map tiles need to be duplicated. Or,
  - All the base map tiles need to be reproduced three times, each time
    in a new orientation. This is relatively easy, but will require each
    map to be stored four times. At the time of writing, the base tiles
    take up 4,5MB of space, zipped. Rotating them all will require a
    total of 18MB of space, a 13,5MB increase. Every new base facility
    will increase the space taken by four times its zipped size.
- The base facility images also need to be rotated. This is easy.
- Optionally (preferrably), functionality for showing the entrance
  markers on the base images has to be coded. This can be as easy as
  duplicating all the images with markers, but as they all have to be
  rotated already that would mean 7 new copies of every image have to be
  created. A more elegant solution may be called for.

## Benefits

- Rotating base facilities adds some variety to the base missions.
- If facilities no longer have to conform to the entrances-on-all-sides
  paradigm, designing different facility layouts becomes possible, as
  less space has to be dedicated to keeping the path clear for 2x2
  units.
- Base building becomes MUCH more fun. Remember that a base site may
  have squares where no facilities may be placed. Combine this with
  facilities that may not have the entrances where you want them, and
  you're looking at a veritable puzzle.

## Conclusion

Implementing this addition to base building is not going to be trivial.
However, I'm convinced that the benefits well outweigh the cost, and
would add more shine to an already great game.

[Category:Proposals](Category:Proposals "wikilink")