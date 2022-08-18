\[medium priority\] [TODO/General/IR
Goggles](TODO/General/IR_Goggles "wikilink") - make sure no sunglasses
are used in default head-models. The intended goggles are the new
'swimming goggle' type model by Hoehrer, NOT the old binocular-type
model. See: [IR
Goggles](http://ufoai.ninex.info/gallery/weapons-and-equipment/goggles.jpg.php).
There are currently 3 (sane) ways to do this (remember that
texture-changes affect all existing camo-skins as well):

- Versions of all current soldier heads with non-green sunglasses and
  without anything.
  - The easy way - Texture-wise only colors need to be changed to
    non-green.
  - IR-goggles not displayed as model in battlescape
  - IR-goggles are visible in equip screen and as a symbol somewhere
    (e.g. cursor)
- Versions of all current soldier heads with 1) IR goggles & 2)without
  anything.
  - The middle course in terms of work.
  - IR-goggles displayable in battlescape/equip with extra code (mattn,
    you got ideas here?).
  - IR-goggles are visible in equip screen and as a symbol somewhere
    (e.g. cursor)
  - Downside: No variations of heads with sunglasses (or other neutral
    new geoemtry) possible.
  - Upside: Only the existing head with sunglasses have to be disabled
    (there are duplicates without them already)
- Versions of all current soldier heads with 1) IR goggles & 2)
  variantions with and without non-green sunglasses.
  - **Update**: After having a quick look on the head-textures it's
    clear that this way is only possible if not only the uv-map is
    changed for each head but also the texture-files have to be made
    bigger and/or re-arranged quite a bit. Crap on a stick, this is far
    from being worth it :(
  - Most work
  - IR-goggles displayable in battlescape/equip with extra code (mattn,
    you got ideas here?).
  - IR-goggles are visible in equip screen and as a symbol somewhere
    (e.g. cursor)
  - Additional space in texture to display sunglas AND goggles (remember
    that this effects all skins)
  - No downside aside from the additional work .. though I still need to
    check if we have enough space in all textures.

<!-- -->

- New IR-goggles model.

- 'Headgear' slot for inventory. (code & menu)
  --[Hoehrer](User:Hoehrer "wikilink")

- IR icon in HUD or at 3D cursor. (code & HUD-art)

- Update head-models (see also the 3 ways above)

  - A list of existing head models (as of 2.1.1) and if/what goggles
    they have - mind you that the color is the one in the default
    texture, there are more variations for each head, but these are
    quickly checked. --[Hoehrer](User:Hoehrer "wikilink")

  - - head01: n=head01a.md2 sung=head01b.md2

    - head02: n=head02a.md2 sunb=head02b.md2

    - head03: n=head03a.md2 sw1bl=head03b.md2

    - head04: n=head04a.md2 sung=head04b.md2

  - \- see

    - head01: n=head01a.md2 sung=head01b.md2

    - head02: n=head02a.md2 sung=head02b.md2

    - head03: n=head03a.md2

    - head03: sw2bl=head03b.md2

    - head04: n=head04a.md2

    - head04: n=head04b.md2 sw1bl=head04c.md2

    - head05: n=head05a.md2

    - head05: n=head05b.md2 sung=head05c.md2

  - and

    - All the models have goggles strapped to the helmet - including the
      strap (texture)!! () and a second version with the same goggles in
      front of the eyes () ... the glass-color of the goggles is a
      variation of brown/black.

  - and

    - All the models have a black "visor"-like thing extending out from
      the helmet () or nothing at all ()

  - (quasi) and

    - Currently these models have a fully enclosed head (until I find a
      way to make it transparent that is). So we'll look into IR stuff
      with that suit later on.

<!-- -->

    sung=with sunglasses-style (green) goggles
    sunb=with sunglasses-style (blue) goggles
    sw1bl=with DIFFERENT swimming-goggles style (black)
    sw2bl=with DIFFERENT swimming-goggles style (black)
    [g=with swimming-goggles style (green)]
    [b=with swimming-goggles style (blue)]
    n=no goggles

[Category:TODO](Category:TODO "wikilink")