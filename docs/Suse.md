## Prerequisites

(Zypper is a command-line alternative interface to the same system as
YaST - see below for a one-liner that should get all dependencies)

Note that where there are packages that depend on the devel packages,
they are not mentioned here, as YaST will select them for install
automatically. Use YaST to install (if you haven't already):

- gcc
- gcc-c++
- make
- git-core
- libSDL-devel
- libSDL_ttf-devel
- libSDL_mixer-devel
- libogg-devel
- libvorbis-devel
- libjpeg8-devel
- libpng-devel
- libcurl-devel
- zlib-devel
- gettext-tools
- gettext-runtime
- libtheora-devel (configure grumbled under opensuse 11.1. when I
  installed ffmpeg2theora (packman repo), it was fine - no idea why this
  fixed it)
- libxvidcore-devel

Some more dependencies for radiant (may be disabled via './configure
--disable-uforadiant')

- gtk2-devel
- gtkglext-devel — Note that with the gtkglext in recent OpenSUSE
  versions (12.x at least) radiant won't compile.
- glib2-devel
- gtksourceviewmm2-devel
- openal-soft-devel
- libxml2-devel

You also need the X11 development packages, on 10.1 they're called
xorg-X11-devel (just search for X11 and select the package with the
-devel extension).

For our test suit (disable with './configure --disable--testall')

- cunit-devel (For versions 2.3 to 2.5)

Yast will automagically sort out any dependencies.

As root, this command should install all dependencies.

`zypper install gcc gcc-c++ make zlib-devel libcurl-devel libjpeg8-devel libogg-devel libvorbis-devel libtheora-devel libSDL-devel libSDL_mixer-devel libSDL_ttf-devel libpng-devel libxvidcore-devel gtk2-devel glib2-devel gtksourceviewmm2-devel gtkglext-devel openal-soft-devel libxml2-devel`

Even though I had libxvidcore, ./configure failed with

    checking for xvid_decore in -lxvidcore... no
    configure: error: You must have libxvidcore!!!

the configure script is missing the .so.4.2, so adding this symlink
fixed it.

    sudo ln -s /usr/local/lib/libxvidcore.so.4.2 /usr/local/lib/libxvidcore.so

I did this after building my own xvid, but this may work on xvid from
the videolan repo.

## Download the latest development version

See [Getting the source](Getting_the_source "wikilink") for more
information

You can also get a specific 'stable' version instead of the most recent
(often unstable) code.

## Compile

type

    ./configure
    make
    make lang

Now compile the maps:

    $ make maps

**WARNING: This process might take some time (even a couple of hours or
so!)(Or All Day!).** It is often recommended instead to use the
maps-sync target, which will download the latest compiled versions of
the maps from the ufoai server:

    $ make maps-sync

NOTE: If you have multiple cpus/cores you might want to use the -j
option to make. The number of jobs should be cpus/cores + 1, so if you
have a dual-core cpu use make -j 3. You could also use -j 2 on single
core/single cpu machines to speed things a little bit.

## Running

Run the game

    $ ./ufo

See [debugging](debugging "wikilink") if you happen to find a bug.

## Packaging for SUSE

See [Packaging/SuSE](Packaging/SuSE "wikilink").

[Category:Distributions](Category:Distributions "wikilink")