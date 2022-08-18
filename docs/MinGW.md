## Dependencies

You will need to install several non standard mingw libs:

- [SDL MinGW
  packages](http://cefiro.homelinux.org/resources/list/SDL-binary-mingw32.html)
- [Freetype developer (-lib)
  package](http://gnuwin32.sourceforge.net/packages/freetype.htm)
- [LibIntl developer (-lib)
  package](http://gnuwin32.sourceforge.net/packages/libintl.htm)
- [LibIconv developer (-lib)
  package](http://gnuwin32.sourceforge.net/packages/libiconv.htm)
- [LibJPEG developer (-lib)
  package](http://gnuwin32.sourceforge.net/packages/jpeg.htm)
- [ZLIB 1.2.3 (-lib)
  package](http://gnuwin32.sourceforge.net/packages/zlib.htm)
- [libpng 1.2.8 (-lib)
  package](http://gnuwin32.sourceforge.net/packages/libpng.htm)
- SDL-image
- SDL-mixer

NOTE: There is a little bash script in current trunk (in ) named to set
your mingw build environment up.

## Compile natively

You'll need [MSYS](http://www.mingw.org/msys.shtml) to run the configure
script, it should then hopefully just be a case of

    ./configure
    make

## Cross Compile with Linux

You have to install the **mingw** package to compile the windows
binaries from within Linux. You'll also need to install all the above
dependencies correctly. Then do

    ./configure --host=i586-mingw32msvc --with-sdl-config=i586-mingw32msvc-sdl-config
    make

This assumes that the sdl-config for the mingw is called
**i586-mingw32msvc-sdl-config** replace with whatever the correct
sdl-config is (it must also be in your PATH). Note: don't try and use
linux's standard sdl-config as this definitely won't work if you don't
use.

you can also use:

`./configure --host=i586-mingw32msvc --with-sdl-prefix=/usr/i586-mingw32msvc`

then a symlink to is enough, too

## Links

- [Compiling](Coding#Compiling_the_source "wikilink")
- [MinGW-Cross-Env](http://www.nongnu.org/mingw-cross-env)
- [IMCROSS](http://www.sandroid.org/imcross/) (has also cross compile
  support for MacOSX)

[Category:Coding](Category:Coding "wikilink")