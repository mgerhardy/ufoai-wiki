## .deb

is there a way to build a debian package? I mean, a .deb file (or
several .deb)????

[201.211.68.206](User:201.211.68.206 "wikilink") 07:06, 9 September 2006
(CEST)

yes, use the makefile target for this task

\-[84.132.164.196](User:84.132.164.196 "wikilink") 08:33, 10 September
2006 (CEST)

## PATH

There is a reference to "the modification of PATH above" but, as far as
I understand things -- which is admittedly not greatly well -- there is
no mention of PATH. If this is to be an explanation for those who are
having trouble installing, it should be better spelled
out.[Gluon1](User:Gluon1 "wikilink") 02:48, 4 June 2007 (CEST)

## Why is libopenal-dev commented out in the build deps?

As far as I can tell, configure checks for it and doesn't find it unless
this package is here (on Ubuntu Gutsy). Is it a bad thing for openal to
be there?

No, but openal is currently not completly implemented
-[Mattn](User:Mattn "wikilink") 14:45, 8 September 2007 (CEST)

I've reverted the recent openal edit because we are no longer using
Openal --[Mattn](User:Mattn "wikilink") 18:05, 15 November 2007 (CET)

According to Destructavator, OpenAL is requierd now. See
<http://ufoai.ninex.info/forum/index.php?topic=3936.30> for more.
--[Dcross](User:Dcross "wikilink") 20:34, 24 August 2009 (UTC)

## Not sure about

..
[these](http://ufoai.ninex.info/wiki/index.php?title=Debian&curid=1488&diff=14302&oldid=13860&rcid=13002)
changes - we are using sdl now, no glx renderer. so this should no
longer be needed, no?

Well, I needed them for the ufoai_2.1 branch. Dunno about trunk.
([Cypher](User:Cypher "wikilink") 20:52, 15 November 2007 (CET))

I've done this now - please check back whether it's ok
--[Mattn](User:Mattn "wikilink") 08:12, 16 November 2007 (CET)

## libs

libcurl3-dev is out-dated on Unstable (Sid). It chooses
libcurl4-openssl-dev here. But also libcurl4-gnutls-dev seems to
compile. I will report back here if I e.g. cannot play the
game.--[Quix0r](User:Quix0r "wikilink") 02:23, 14 June 2008 (CEST)

libcurl4-gnutls-dev works for me too. --[Tex](User:Tex "wikilink")
03:19, 4 June 2009 (UTC)

## pretty sure the prereqs list is incomplete

on a generally un-fooled-with somewhat-recent ubuntu I have to install
more than what is presently listed in the list of prerequisite dev
packages:

` $ sudo apt-get install \`
`   libsdl1.2-dev libsdl-ttf2.0-dev libvorbis-dev zlib1g-dev gettext \`
`   libjpeg62-dev libpng12-dev libncurses5-dev libcurl3-dev libsdl-mixer1.2-dev libxml2-dev`

Specifically I also have to install dev packages for zlib, xvid, and
theora.

Also ./configure --disable-gtkradiant didn't seem to work because the
configure script still whined about various gtkradiant-related things
and still exited with an error even with the flag.

After all that, though, the compile finally worked, so yay for *mostly*
correct docs. Much better than no docs at all! :\]
--[Tex](User:Tex "wikilink") 03:18, 4 June 2009 (UTC)

## more packages

Also needed libsdl-image1.2-dev for SDL_image.h
--[Amishaa](User:Amishaa "wikilink") 06:56, 28 March 2010 (UTC)

## Fedora :)

yum install gcc-c++

yum install xvidcore-devel libtheora-devel binutils-devel
libjpeg-turbo-devel zlib-devel libpng-devel CUnit-devel lua-devel
mxml-devel SDL-devel SDL2-devel SDL_ttf-devel SDL_mixer-devel
libxml-devel libxml2-devel openal-devel

aftrer that ./configure, line 238: lua5.1 change to lua-5.1

run ./configure

--[Sotnikov123](User:Sotnikov123 "wikilink")
([talk](User_talk:Sotnikov123 "wikilink")) 17:00, 1 December 2013 (CET)