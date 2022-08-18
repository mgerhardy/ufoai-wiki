Can we have a troubleshooting section for map compiliation?

I had this problem: qbsp3 couldn't manage to create a .bsp for
rocketsilo.map. I don't know where to report this... I didn't want to
report this to SVN since it doesn't seem to be a "game" bug.

I also installed the perl interpreter and ran the perl script in
base/maps, but again, it seems to compile all maps except
rocketsilo.map.

Also its obvious for advanced users that the maps have to be drag'd and
dropped on the qbsp3.exe (if they don't ıse Perl to do it all in one),
but if Mattn hadn't told me, I think I never could have figured out how
to use qbsp3 and qrad. So maybe it'll be nice to have a bit more info on
the how-to's.


You shouldn't use qbsp3 or q3rad - use ufo2map instead. If you still
have problems with compiling some maps (btw. rocketsilo is not playable
at all - so it's save to remove the map file) then please file a bug
report with as much as possible information (which system, arch and so
on) --[Mattn](User:Mattn "wikilink") 08:00, 9 May 2007 (CEST)

## Errors

One of the errors listed on this page deals with having different
textures on different faces of the same brush (mixed face contents).
Besides the obvious prefabs that DON'T adhere to this rule, is this hard
and fast? Would it be better to use 2 brushes against each other with
different textures to 'wallpaper' the inside of a house instead of using
a facial texture? --21:34, 8 May 2007 (CEST)


mixed face contents is no error - only a warning (and even that is
untrue for the latest version in svn) - and it has nothing to do with
different textures - but only different content- and surfaceflags.
Please don't use 2 brushes against each other - keep the brushcount low
(the most important rule)!! e.g. if a brush in level 1 isn't visible in
level 2 then remove the level 2 flag from this brush. then it won't be
drawn at all (which means lower r_speeds =\> fast rendering).
--[Mattn](User:Mattn "wikilink") 07:57, 9 May 2007 (CEST)


I get this warning when I build brushes with textures on different
faces... is it possible that this is because of different 'stretch'
fittings for the texture, and these are content flags?
--[Wanderer](User:Wanderer "wikilink") 08:24, 10 May 2007 (CEST)


No, but as i said - these are only warnings - you can in most cases
saftly ignore them (that's why i disabled the output of those warnings
in current development version - they are now only shown in verbose
mode) --[Mattn](User:Mattn "wikilink") 11:28, 10 May 2007 (CEST)