## Prerequisites

For Debian and Debian-based distributions (Ubuntu etc.), you first need
to install the standard GNU gcc stuff and GIT. Open your favourite
console and type:

` $ sudo apt-get install make gcc g++ git`

You also need the following development packages (hope I didn't forget
any - if make fails, that's probably the reason):

` $ sudo apt-get install \`
`   libsdl2-dev libsdl2-ttf-dev libvorbis-dev zlib1g-dev gettext libtheora-dev \`
`   libjpeg-dev libpng-dev libcurl4-openssl-dev libsdl2-mixer-dev \`
`   libxml2-dev libopenal-dev p7zip-full binutils-dev libxvidcore-dev libmxml-dev libiberty-dev `

To compile the test suite, which is enabled by default (disable with
./configure --disable-testall)

For versions 2.3 to 2.5

` $ sudo apt-get install libcunit1-dev`

You need these development packages if [radiant](Mapping "wikilink")
should be built, which can be disabled via './configure
--disable-uforadiant'.

` $ sudo apt-get install \`
`   libglib2.0-dev libgtk2.0-dev libgtkglext1-dev libgtksourceview2.0-dev`

If You are using versions prior 2.5 you need libsdl-image1.2-dev and
libjpeg62-dev but not libjpeg8-dev.

` $ sudo apt-get install libjpeg62-dev libsdl-image1.2-dev`

If you plan to compile version prior to 2.2 you maybe also need
*libxxf86vm-dev* and *libxxf86dga-dev*.

If you have issues with finding 'GL/gl.h' (later in the build) the
following may also help

` $ sudo apt-get --reinstall install mesa-common-dev`

*Note: You also need to install gettext to compile languages (following
the standard procedure on Ubuntu without that results in almost no texts
in game).* [Wrwrwr](User:Wrwrwr "wikilink") 03:04, 7 December 2007 (CET)

''Note: An easy way to get all build deps is to install the
ubuntu/debian packages "equivs" and "devscripts" and run the following
commands : (this will also provide the option to make the .deb files for
ufoai later) --[Ranyardm](User:Ranyardm "wikilink") 00:16, 1 May 2010
(UTC)

` mk-build-deps`
` sudo dpkg -i ufoai-build-deps_1.0_all.deb`
` sudo apt-get install -f`

If the game's sound is choppy, goes fast, and dies soon after starting,
install **libsdl1.2debian-pulseaudio**. Set PulseAudio to use an
internal sample rate of 48000 Hz by adding this line to
/etc/pulse/daemon.conf:

`  default-sample-rate = 48000`

## Downloading the latest development version

See [Getting the source](Getting_the_source "wikilink") for more
information

## Compiling game, language files and maps

Compile the game with:

    $ ./configure
    $ make

NOTE: You might want to use the -j option to make. This option will
start multiple jobs to speed up compilation on modern CPUs. The number
of jobs should be cpus/cores + 1, so if you have a dual-core cpu make -j
3, on a quad-core CPU make -j 5 is recommended. You could also use -j 2
or -j 4 on single core/single cpu machines to speed up things a little
bit. Be aware that using all cores for map compiling will use up all of
your processing power, so other applications will slow down to a crawl.

Compile the language files with:

    $ make lang

NOTE: Ofc you can use multiple jobs here as well.

Now compile the maps (see also
[Mapping/Compile](Mapping/Compile "wikilink")):

    $ make maps

WARNING: Compiling all the maps takes a very long time, even on today's
fastest machines !

NOTE: It is highly recommended to download compiled maps from the server
instead of compiling them, but if you want to test the cooling of your
CPU using multiple jobs is recommended for this task as well.

NOTE: You can use the python script update.py in to save time and CPU
power and download all the latest compiled maps (.bsps) from our server.
You need to have Python installed to make this work:

    $ python ./contrib/map-get/update.py

NOTE: You can also start the map-get update-maps script with:

    $ make maps-sync

After you've aquired the maps and compiled the binary you are ready to
start the game:

    $ ./ufo

## Compiling UFORadiant (optional)

NOTE: To be able to create maps for UFO:Alien Invasion's battlescape you
need to compile UFORadiant (our map-editor). These steps are optional if
you do not intend to modify maps or help with mapping, otherwise they
are essential.

    $ ./configure --enable-uforadiant
    $ make uforadiant

NOTE: To start the mapeditor you have to change directory into radiant
and start the compiled executable from there.

    $ cd radiant
    $ ./uforadiant

## Installation (optional)

    $ make pk3
    $ sudo make install

NOTE: You just need to create the pk3 files (which are simple .zip files
containing the data for the installation like maps, ufos, pics,
textures, models) if you want to install the game. For running the game
from source and helping with development these installation steps are
not needed.

## Starting the game

In master run the ufo executable:

    $ ./ufo

The [Debugging](Debugging "wikilink") section also provides useful
advice if something goes wrong.

## Known problems and solutions

If a black screen occurs and if you previously have installed the game :
remove the ufoai directory () in your home directory:

    $ rm -R ~/.ufoai

## Building Debian packages

Use e.g. to build a clean chroot environment in which you can generate
the debian packages with:

`sudo apt-get install devscripts`

Just type:

    $ make deb

This will build all maps and compile the game (if not already done) and
create deb packages (you need the devscripts package, too). If you want
to build the maps with this command, make sure, that you already have
ufoai-tools installed. To install them before creating the maps you can
type:

    $ make debbinary

and install the ufoai-tools package via:

    $ dpkg -i ufoai-tools[...].deb

You also have the ability to create only the data packages by typing:

    $ make debdata

[Category:Distributions](Category:Distributions "wikilink")