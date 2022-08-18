## General

List of bad scaling in ufopedia:

- Stun rod
- machine pistol
- micro shotgun
- laser rifle
- stealth intercepter
- heavy laser

Fix scaling for all models integrated into the game; examples of broken
things [here](http://voovoos.killfile.pl/roznosci/ufo07.jpg),
[here](http://voovoos.killfile.pl/roznosci/ufo08.jpg),
[here](http://voovoos.killfile.pl/roznosci/ufo12.jpg) and
[here](http://voovoos.killfile.pl/roznosci/ufo13.jpg).

- [Mattn](User:Mattn "wikilink") 21:08, 20 December 2006 (CET) please
  don't scale these models - they are used in our maps files already -
  define a scale and rotate factor in our models.ufo to make them work
  via menu
  - now with scale and angle parameters in ufo files aircraft models can
    be easily adjusted to fit into proper menus, but i somehow find lack
    of position parameter per model type, however I am not sure if this
    cannot be done by already implemented scale and
    angle--[Zenerka](User:Zenerka "wikilink") 12:14, 3 January 2007
    (CET)
- We really need a more general solution for all those scaling issues.
  we currently have at least 5 places where models (that are used in the
  inventory) are shown ...
  - the battlescape (uses the original model-size afaik)
  - ufopedia
  - production menu
  - the inventory
  - and the aircraft menu (should be fixed already?)
    - yes and no; you can scale and rotate models, but you cannot fix
      the position for them (which put models too high or too
      low)--[Zenerka](User:Zenerka "wikilink") 13:04, 8 January 2007
      (CET)
      - Ok good, so the only thing left is a "center" setting then.
        --[Hoehrer](User:Hoehrer "wikilink") 13:29, 8 January 2007 (CET)
  - (is the aircraft-**equip** menu planned to show 3d models?)
    - aircraft equip menu already shows 3d models, and they are nicely
      rotated (like view from above)--[Zenerka](User:Zenerka "wikilink")
      13:04, 8 January 2007 (CET)
      - Sorry, i wasn't verbose enough here ... i was talking about the
        upgrades themself, not just the aircraft. Is it planned to
        display upgrades in 3D? --[Hoehrer](User:Hoehrer "wikilink")
        13:29, 8 January 2007 (CET)
        - If we ever get models for them - yes definitly
          [Mattn](User:Mattn "wikilink") 17:05, 10 January 2007 (CET)
        - We already have at least one (See the shiva model in
          [Changelog/2.1](Changelog/2.1 "wikilink")) Which meant it is
          one more place wher3e we need nice placement of a 3d model.
          --[Hoehrer](User:Hoehrer "wikilink") 17:33, 10 January 2007
          (CET)

## Related Bugs

- *Ufopedia - too big images/models*

- *Oversized research graphics* (duplicate)

- *Huge stun rod image* (duplicate)

## Possible solutions

### Seperate definition for all menus

Either add the functionality so we can **tweak size, placement and
rotation for each** of them --[Hoehrer](User:Hoehrer "wikilink") 16:22,
7 January 2007 (CET)

- My personal favourite so far would be a model-scale-list for each
  model that gets displayed. This list has the scale, position and
  rotation for each place the model is displayed (I can provide a
  code-mockup if s/b would like that). You just hand the pointer to this
  list to the renderer and he then uses the correct scale for each
  model. This would be in a common place (e.g. the research list or
  something completely separate) so it only needs to be parsed in one
  place. --17:33, 10 January 2007 (CET)

**Update**: There already seems to be basic support for menu-depending
scaling in the code. See :

    menuscale <x,y,z>

and this in and

    menuModel->menuScaleCnt
    menuModel->menuScaleMenusPtr[]
    menuModel->menuScaleValue[]

Looks pretty useable already, but I dunno how advanced implementation is
right now though. --[Hoehrer](User:Hoehrer "wikilink") 14:39, 6 August
2007 (CEST)

### use images

... or we may have to **resort to images** to make the task easier.
--[Hoehrer](User:Hoehrer "wikilink") 16:22, 7 January 2007 (CET)

### Autoscaling

Or we could get good autoscaling to work. Currently it does not display
menu_models with tags at all (i.e. Models that consists of more that one
part: crafts, aliens, ugvs etc..) --[Hoehrer](User:Hoehrer "wikilink")
13:21, 6 August 2007 (CEST)

### Possible (temporary) workaround

We could deactivate autoscaling in ufopedia for now and scale every
single entry with a "menu_model" entry in models.ufo.
--[Hoehrer](User:Hoehrer "wikilink") 13:21, 6 August 2007 (CEST)

[Category:Contribute](Category:Contribute "wikilink")
[Category:TODO](Category:TODO "wikilink")
[Category:Development](Category:Development "wikilink")