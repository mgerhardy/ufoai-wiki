# TODO/Renderer

## Code

- Fix md2 model rendering - sometimes still problems exist (some plants'
  trunks are still rendered in front of the leaves for example, some
  models are still not displayed 100% correctly, sometimes rendering
  order is still confused)

<!-- -->

- Fix md2 model realtime lighting (seems to work, but effects do not
  disappear)

<!-- -->

- Fix md2 model normalmapping which does not seem to work 100% correctly
  at the moment

<!-- -->

- Fix ir-goggles special effect (the effect is white instead of red when
  shaders are used)

<!-- -->

- Fix the material system's default values for bump, specular and
  hardness settings and make normalmapped surfaces appear less shiny

<!-- -->

- Optimize rendering speed, because graphics are slow at the moment and
  make 3d rendering less CPU-bound (use 3d graphics hardware more)

<!-- -->

- Fix and apply the Stencil Shadows patch from Q2World or some other
  lighting/shadow system

  - Light and Shadows (jdolan):
    <https://sourceforge.net/tracker/?func=detail&aid=3302916&group_id=157793&atid=805244>

<!-- -->

- Re-add or fix support for roughness maps

<!-- -->

- Re-add or fix support for specular maps

<!-- -->

- Look at the renderer_work branch and merge fixes & working stuff from
  there (realtime lighting and shadows were already working in this
  branch)

<!-- -->

- Fix in-game and UFORadiant support for md3 models (at the moment both
  error out trying to use md3 models)

[Category:Contribute](Category:Contribute "wikilink")
[Category:TODO](Category:TODO "wikilink")