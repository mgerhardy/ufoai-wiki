This article provide a way to set up an environment for compiling on
Windows, willing to use Eclipse CDT as development environment. For
Windows, you also need [MinGW and MSYS](MinGW "wikilink").

## Configure MSYS/MinGW for Windows

On Windows Eclipse need MinGW and MSYS to compile sources. See also the
[MinGW](MinGW "wikilink") article.

1.  first preparations:
    1.  use prepackaged version for MinGW/Code::blocks, extract MinGW
        where you want (I used E:\MinGW)
    2.  [install MSYS](http://www.mingw.org/wiki/MSYS) (E:\MSYS)
    3.  update MSYS with compiled versions found in MSYS download
        section: (perhaps these are only needed if I want to run
        autoconf from configure.ac; in the end that led to another error
        not being able to run configure, so I used configure version
        from trunk)
        - m4-1.4.7-MSYS
        - msys-autoconf-2.59
        - msys-automake-1.8.2
2.  started configure, realized that SDL.h was not found because of
    missing path
3.  create missing path/link. You must have [Microsoft
    junction](http://technet.microsoft.com/en-us/sysinternals/bb896768.aspx):
    - in MSYS command shell
      1.  `cd /usr` (E:\MSYS\1.0)
      2.  `mkdir local`
      3.  `mkdir local/cross-tools`
    - in Windows command shell
      1.  `cd E:\msys\1.0\local\cross-tools`
      2.  `junction i386-mingw E:\MinGW`
4.  restarted configure, realized that SDL libraries are not found
5.  change sdl-config (if you have problems with SDL lib checking)
    1.  sdl-config is located in E:\MinGW\bin
    2.  add "-lmingw32 -lSDLmain -lSDL -mwindows" from --libs to
        --cflags
6.  now configure and make will run, further steps are needed to get it
    running in eclipse:
    1.  add MinGW and MSYS bin folders to PATH variable, I placed it at
        front because there is a windows version of find which uses
        wrong syntax to let make run under Eclipse
    2.  to get rid of massive warnings about unused linker files: Edit
        Makefile in root directory, remove the -l parts from CFLAGS

## Configure Eclipse

For useful work with Eclipse I use Ganymede (3.4) package for C++
developers, added SVN Connector + JavaHL implementation (found on
[polarion](http://www.polarion.com/products/svn/subversive.php?src=eclipseproject)
To enable C features for UFO:

1.  add SVN repository to list
2.  check out as new project
3.  Use "New"-\>"Convert project to C/C++ project" to add c project
    nature

This way I now can compile/debug UFO directly from Eclipse, having SVN
support for easy updating. I don't add this to main page because I want
to hear your comments whether this is a "clean" solution.
[RudolfoWood](User:RudolfoWood "wikilink") 20:01, 13 August 2008 (CEST)

### Make, run and debug on Windows

Make all to create binaries (hammer icon). If it dont work, be sure
Eclipse know the MinGW and MSYS binary path.

- Window -\> Preferences -\> C/C++ -\> Environment
- Add a "path" variable with MinGW and MSYS binary path

Fix binary parser if need.

- Project -\> Properties -\> C/C++ Build -\> Settings -\> Binary Parsers
- check "PE Windows Parser"

Add a "run configuration"

## Radiant compile

These steps I did to prepare radiant building. I actually can't compile
it yet, so I will add more steps...

1.  added GTK dependencies by installing([all in one
    bundle](http://ftp.gnome.org/pub/gnome/binaries/win32/gtk+/2.14/gtk+-bundle_2.14.4-20081108_win32.zip),
    unzip to MinGW directory)
2.  added GtkGLExt (followed
    [this](http://gcam.js.cx/index.php/MinGW_MSys_GTK_Configuration_Guide#Install_GtkGLExt)
    instructions)
    1.  download and untar 1.2.0 file from
        [here](https://sourceforge.net/project/showfiles.php?group_id=54333&package_id=48997)
    2.  removed all lines with pangox from untared (last one
        GDKGLEXT_PACKAGES="gdk-2.0 pango pangox gmodule-2.0" just remove
        pangox from this line)
    3.  configure (./configure --prefix=/mingw)
    4.  remove the lines with
            --fprod "/* enumerations from \"@filename@\" */\n" \

        and

            --fprod “\n/* enumerations from \"@filename@\" */" \

        from
    5.  make && make install
3.  follow
    [this](http://wiki.gnustep.org/index.php/Installation_on_Windows#Install_XML_support)
    instruction to install xmllib2 - just untar, configure, make and
    make install.
4.  now ufoai "configure --enable-uforadiant" works

- for radiant compile I had to change from gcc to g++ - I'll try to
  provide a change to makefiles after I figure out how this would be
  done clean. I'll add further notes later

[RudolfoWood](User:RudolfoWood "wikilink") 19:16, 17 November 2008 (UTC)

Radiant makefile changes are in trunk, so nothing to be done for that.
--enable-uforadiant is no longer needed. One thing I had to do to get
radiant running:

- copy libxml2.dll to (mine was in )

[RudolfoWood](User:RudolfoWood "wikilink") 14:50, 27 December 2008 (UTC)