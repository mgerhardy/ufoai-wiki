after checking out UFO:AI from [SVN](Getting_the_source "wikilink") you
will have a new directory with the following structure:

<code>

`\-ROOTDIR OF UFO:AI SVN`
`  \-build`
`    \-projects`
`      \game.cbp        `[`Code::Blocks`](Code::Blocks "wikilink")` project file for `**`game.dll`**
`      \ufo.cbp         `[`Code::Blocks`](Code::Blocks "wikilink")` project file for `**`ufo.exe`**
`  \-base`
`    \-debian`
`    \-i18n             home of the compiled language files`
`    \-maps             source of maps and after `[`compiling the maps`](Mapping:Compile "wikilink")` also home of bsp files`
`    \-media            true type fonts`
`    \-models           source of models and models in md2 format`
`    \-music            music folder *.ogg`
`    \-pics             folder for menu pics`
`    \-sound            weapon, ambient... sounds`
`    \-textures         textures for the tactical missions`
`    \-ufos             script files for menu, campaigns,...`
`    \default.cfg       e.g. renderer settings`
`    \`[`keys.cfg`](keys.cfg "wikilink")`          key bindings`
`    \mapshots.cfg      exec this when you want to make base tiles mapshots`
`  \-src                sourcecode of UFO:AI (programming language is C)`
`    \-client`
`    \-debian`
`    \-docs             design docs`
`    \-game`
`    \-po               home of `**`ufoai.pot`**` and po files (`[`translations`](Translating "wikilink")`)`
`    \-common`
`    \-ports`
`      \-linux`
`      \-macosx`
`      \-unix`
`      \-solaris`
`      \-windows`
`    \-renderer`
`    \-server`
`    \-tools            sourcecode of `[`ufo2map`](Mapping:Compile "wikilink")

</code>

    .
    |-- AUTHORS
    |-- COPYING
    |-- README
    |-- TODO
    |-- base
    |   |-- default.cfg
    |   |-- game.so <<<< game lib for ufo - just copy from src/debugi386
    |   |-- i18n
    |   |   |-- cs
    |   |   |-- da
    |   |   |-- de
    |   |   |-- en_GB
    |   |   |-- fr
    |   |   |-- it
    |   |   |-- pl
    |   |   `-- ru
    |   |-- [[keys.cfg|keys.cfg]]
    |   |-- maps
    |   |   |-- africa04d.bsp
    |   |   |-- africa04n.bsp
    |   |   |-- b
    |   |   |-- compile.pl
    |   |   |-- const05d.bsp
    |   |   |-- const05n.bsp
    |   |   |-- [...]
    |   |   |-- tropicd
    |   |   |-- tropicd.ump
    |   |   |-- villaged
    |   |   |-- villaged.ump
    |   |   |-- villagen
    |   |   `-- villagen.ump
    |   |-- mapshots.cfg
    |   |-- media
    |   |   |-- COPYING
    |   |   |-- DejaVuSans.ttf
    |   |   `-- FreeSans.ttf
    |   |-- models
    |   |   |-- aircraft
    |   |   |-- aliens
    |   |   |-- animals
    |   |   |-- civilians
    |   |   |-- objects
    |   |   |-- soldiers
    |   |   `-- weapons
    |   |-- music
    |   |   `-- license.txt
    |   |-- pics
    |   |   |-- air_dropship.tga
    |   |   |-- air_interceptor.tga
    |   |   |-- air_ufo.tga
    |   |   |-- althud
    |   |   |-- armor
    |   |   |-- base
    |   |   |-- base.tga
    |   |   |-- black.tga
    |   |   |-- circle.tga
    |   |   |-- circleactive.tga
    |   |   |-- colormap.pcx
    |   |   |-- conback.jpg
    |   |   |-- conchars.pcx
    |   |   |-- cross.tga
    |   |   |-- cursor1.tga
    |   |   |-- ducked.tga
    |   |   |-- f_big.tga
    |   |   |-- f_big.xcf
    |   |   |-- f_menu.tga
    |   |   |-- f_menu_small.tga
    |   |   |-- f_small.tga
    |   |   |-- f_small.xcf
    |   |   |-- hud
    |   |   |-- loading.jpg
    |   |   |-- maps
    |   |   |-- menu
    |   |   |-- net.jpg
    |   |   |-- pause.jpg
    |   |   |-- sensor.tga
    |   |   |-- sfx
    |   |   |-- techs
    |   |   |-- tutorial
    |   |   |-- ufoai.jpg
    |   |   `-- wait.tga
    |   |-- sound
    |   |   |-- misc
    |   |   `-- weapons
    |   |-- textures
    |   |   |-- exterior
    |   |   |-- interior
    |   |   |-- tex_base
    |   |   |-- tex_buildings
    |   |   |-- tex_buildings_snow
    |   |   |-- tex_doors
    |   |   |-- tex_effects
    |   |   |-- tex_furniture
    |   |   |-- tex_lights
    |   |   |-- tex_material
    |   |   |-- tex_misc
    |   |   |-- tex_nature
    |   |   |-- tex_pics
    |   |   |-- tex_shop
    |   |   |-- tex_streets
    |   |   |-- tex_tech
    |   |   |-- tex_ufo
    |   |   `-- tex_vehicles
    |   `-- ufos
    |       |-- armor.ufo
    |       |-- basemanagement.ufo
    |       |-- campaign.ufo
    |       |-- menu_ufopedia.ufo
    |       |-- [...]
    |       |-- names.ufo
    |       |-- seq_tutorials.ufo
    |       `-- weapons_tachyon.ufo

[Category:General](Category:General "wikilink")