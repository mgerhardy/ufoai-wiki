### Prefabs of models

"A prefab of e.g. a [misc_model](Mapping/Entities/misc_model "wikilink")
should also contain all the clips that are needed."

This may need some discussion, as currently those prefabs are made very
differently. Some of them use weird combinations of clips that do not
make sense at all. One example: The actual prefab of the Raptor dropship
uses nodraw, actorclip and weaponclip brushes, all without levelflags.
The nodraw brushes without levelflags will block actor movement and
shots, but will not cast a shadow. The weaponclip brushes only blocks
shots, duplicating one property of the nodraw, while the actorclip only
blocks actor movement, again a duplication. This way we have three
layers of clips and still miss the shadow.

- Some of this is wrong. The nodraw brushes without levelflags will
  block shots and also block the Line of Sight. They will not block
  actor movement and they will not cast a shadow.
  [ShipIt](User:ShipIt "wikilink") 13:20, 18 April 2012 (SAST)

Also, using the clips without levelflags will hide them in UFORadiant
when using the Levelselector.

- This is not true for the nodraw brushes. Those will stay visible all
  the time. [ShipIt](User:ShipIt "wikilink") 13:20, 18 April 2012 (SAST)

Another drawback is, without levelflags the Level up/down tool cannot
handle those clips correctly. Of course there might be a reason for this
that I am not aware of.

So, if making a prefab of a model, I suggest we use one of the following
combinations, with proper levelflags set.

1\. Just nodraw brushes.

- The drawback here is that in some cases the nodraw brush will cause
  black holes in other brushes if touching them.

2\. Three layers, a combination of actorclip, lightclip and weaponclip
brushes.

- None of those breaks the Line of Sight.
  [ShipIt](User:ShipIt "wikilink")

--[ShipIt](User:ShipIt "wikilink") 09:56, 17 April 2012 (SAST)

I don't think level flags matter for nodraw/clip brushes. They are
handled entirely separately. --[H-hour](User:H-hour "wikilink") 11:39,
18 April 2012 (SAST)

- Well, I did some testing. Do you just think it should not matter, or
  did your tests give different results ? Maybe the current behavior of
  the nodraws is not like it should be ? In fact not a single one of the
  Raptor dropships actually casts a shadow for some reason. I just don´t
  want more things like that spread over the maps.
  --[ShipIt](User:ShipIt "wikilink") 13:20, 18 April 2012 (SAST)
  - By all means, test it out. But my guess is that Raptor dropships
    don't cast shadows because the lightclip didn't exist when they (or
    the prefab) was set up. It's a relatively new thing (like, a couple
    years). But in my experience a lightclip brush casts a shadow (as do
    all brushes) regardless of the levelflag, because something on one
    level should still cast a shadow even if the viewer is not viewing
    that level. Same with weaponclip/actorclip. The way they effect
    collision does not depend on what level they are supposed to appear
    on. --[H-hour](User:H-hour "wikilink") 17:28, 18 April 2012 (SAST)
    - For the actor-, light and weaponclip brushes levelflags only
      affect the way they are handled in UFORadiant. The nodraw brushes
      show different behavior in game depending on levelflags, as
      described. \<-- This is not a guess nor what I think it could or
      should be, but the result of tests I made when updating the
      [Informations about surface- and
      contentflags](Mapping/Surface_inspector "wikilink"). Of course I
      might be wrong. [ShipIt](User:ShipIt "wikilink") 07:04, 19 April
      2012 (SAST)
      - Interesting, did not know that.
        --[H-hour](User:H-hour "wikilink") 09:19, 19 April 2012 (SAST)

The point is "A prefab of e.g. a
[misc_model](Mapping/Entities/misc_model "wikilink") should also contain
all the clips that are needed."

The question is : "Wich clips are needed?"
[ShipIt](User:ShipIt "wikilink") 07:04, 19 April 2012 (SAST)