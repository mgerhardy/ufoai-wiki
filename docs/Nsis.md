We use a [nsis](http://nsis.sourceforge.net) installerscript. You can
find it in .

Make sure that you have compiled the source and the other needed dll
files (see [running the game](running_the_game "wikilink")) and that
they are located in root-dir (see [directory
tree](directory_tree "wikilink")).

You can use the Windows version of nsis or the linux version () to build
the installer.

There is also a makefile target named `win32installer` - so you can type
`make win32installer` to build the installer (if you have nsis
installed). The maps are automatically compiled, the languages are
automatically updated and the **[pk3](pk3 "wikilink")** files are build,
too. All you have to do is to place the windows binaries in the right
places (everything to the game root - except the which goes into the
dir).

## Links

- [nsispatchgen](http://sourceforge.net/projects/nsispatchgen) - nsis
  plugin to create patches
- [Packaging/Windows](Packaging/Windows "wikilink")

[Category:Coding](Category:Coding "wikilink")
[Category:Packaging](Category:Packaging "wikilink")
[Category:Contribute](Category:Contribute "wikilink")