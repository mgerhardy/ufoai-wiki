## Getting the source

Just have a look at our [Getting the
source](Getting_the_source "wikilink") page to get more information
about this.

## Requirements

In order to compile UFO:Alien Invasion under Linux you need to install
some packages. First of all make sure, that you have gcc installed.

- gcc/g++
- OpenGL-header files (usually comes with your graphic card drivers; or
  you may use the 'mesa' source package)
- ogg vorbis header
- libjpeg8 header
- libpng header
- libcurl header
- zlib header version \>= 1.2.3
- SDL (incl. headers)
  - SDL version \>= 1.2.10
  - SDL_ttf (sdl-ttf) version \>= 2.0.7
  - SDL_mixer (libsdl-mixer) version \>= 1.2.7
- make

## Compiling the source

- [Linux (Generic)](Compile_for_Linux "wikilink")
  - [Debian/Ubuntu](Debian "wikilink")
  - [SuSE](Suse "wikilink")
  - [Compile Windows binaries with Linux](MinGW "wikilink")
- [Windows](Compile_for_Windows "wikilink")
- [Mac](Compile_for_Mac "wikilink")
- [Solaris](Compile_for_Solaris "wikilink")
- [FreeBSD](Compile_for_FreeBSD "wikilink")

Don't forget to [compile the maps](Mapping:Compile "wikilink") when you
are not using any pre packaged version. Otherwise the tactical missions
won't start up.

Also make sure, that you [compile the language files](po "wikilink")
(po-files from ). Otherwise you will only see placeholders in the
ufopedia and some other places.

You can now create the pk3 archives by typing

    make pk3

\- also see the [packaging](Packaging "wikilink") notes. This step is
optional.

After compiling the source and maps you will most likely [run the
game](Running_the_game "wikilink").

## Debugging the game

There is a [debugging](debugging "wikilink") article available with more
information about this topic.

The [Debug commands](Coding/Debug_commands "wikilink") will help you
here as well.

## Contributing

If you want to contribute to the project you need an account at
sourceforge.net or submit your patches anonymously to our [issue
tracker](http://ufoai.org/bugs). There is also a
[TODO-list](TODO "wikilink") and a [Changelog](Changelog "wikilink")
available. Please also have a look at the [coding
guidelines](Coding_guidelines "wikilink").

## Documentation

The [Doxygen](Doxygen "wikilink") code documentation can be found
[here](http://ufoai.ninex.info/doxygen). It is most likely out of date,
but you can always generate a current one yourself by typing:

    make doxygen-docs

in the root of your ufoai working directory.

## External Links

- [UFO:AI Project homepage](http://sourceforge.net/projects/ufoai/) at
  [SourceForge](http://sourceforge.net)
- [CIA Bot](http://cia.navi.cx/stats/project/ufoai) - Repository
  changelog with some statistics
- [Pre-defined Operating System
  Macros](http://predef.sourceforge.net/preos.html)

### Coding help

- [Dev-Master](http://www.devmaster.net/)
- [GameDev.net](http://www.gamedev.net/)
- [Game Programming Wiki](http://gpwiki.org/)
- [flipCode Archives](http://www.flipcode.com/archives/)
- [C-Programming articles](http://www.cprogramming.com/)
- [OpenGL Red Book](http://www.glprogramming.com/red/)
- [OpenGL Blue Book](http://www.glprogramming.com/blue/)
- [NeHe OpenGL tutorials](http://nehe.gamedev.net/)

### Tutorials on the net

some of them are Quake1 or Quake3 related but maybe give a starting
point...

- [Coding tutorials](http://webadvisor.aupr.edu/noc/CodingTutorials.htm)
- [Code3Arena](http://www.quakewiki.net/archives/code3arena/)
- [Tutorials](http://www.3delement.com/) for 3D game development
- [OpenGL Tutorials](http://delphi3d.net/)

## Related Wiki Links

- [Getting the source](Getting_the_source "wikilink")

[Category:Coding](Category:Coding "wikilink")
[Category:Contribute](Category:Contribute "wikilink")
[Category:Development](Category:Development "wikilink")