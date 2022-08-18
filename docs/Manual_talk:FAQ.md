## Sytem specs

Everywhere you are telling about latest graphic cards. What exactly are
minimal requirements?

i think we should release your system data to get the minimum specs.
--[84.131.227.208](User:84.131.227.208 "wikilink") 20:57, 11 September
2006 (CEST)

## Mesa

I've just tested the game on a system with Mesa-only OpenGL drivers:

`VGA compatible controller: ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]`
`GL_VENDOR: Tungsten Graphics, Inc.`
`GL_RENDERER: Mesa DRI R300 20060815 TCL`
`GL_VERSION: 1.2 (1.3 Mesa 6.5.1)`

Runs very smooth - first Mesa installation i've seen that works with an
acceptable speed


\-[Mattn](User:Mattn "wikilink") 12:16, 5 June 2007 (CEST)

\> always \~ 80fps --[84.131.227.208](User:84.131.227.208 "wikilink")
20:57, 11 September 2006 (CEST)

Have you got sync-to-blanc and your monitor runs at 80Hz? If so, now
wonder. Moreover, there is a cvar, I don't remember the name, that
limits FPS to 90, IIRC, so you wont get more without raising the cvar.

I get about 500FPS on battlescape and 300PFS on menus, with a similar
setup to mattn's but NVIDIA 5900XT (with MMX enabled in the makefile,
IIRC).

--[Bandobras](User:Bandobras "wikilink") 21:12, 11 September 2006 (CEST)


It's
`set cl_maxfps "90"`
--[Hoehrer](User:Hoehrer "wikilink") 23:42, 11 September 2006 (CEST)

## Show FPS

run

    set cl_fps 1

in [commandline](commandline "wikilink") or add this line to