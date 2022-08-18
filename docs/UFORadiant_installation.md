## Getting UFORadiant

You may already have UFORadiant depending on how you installed UFOAI
and, if compiled, what options you compiled with. If you go to your
installation directory for UFOAI, look for a subfolder named "radiant".
If it's there, UFORadiant is already installed. Click on the
uforadiant.exe file in the radiant subfolder to load it and skip ahead
to the [Mapping for Dummies](Mapping_for_Dummies "wikilink") tutorial.

If not, you'll need to download or compile UFORadiant. At the moment it
doesn't have a regular release cycle or a "stable" version (although
most versions are pretty stable). This means tracking down the right
installation file is not always that easy, something we hope to do
better on in the future.

For downloading UFORadiant, please visit the [Download
section](Download "wikilink").

## Compile yourself

You are encouraged to get the source from the [Git
repository](Getting_the_source "wikilink") and compile yourself.

Dependencies for compiling under Debian/Ubuntu:

- libgtk2.0-dev
- libgtkglext1-dev
- libxml2-dev

### Linux

compile the mapeditor with:

    make radiant

after you compiled UfoAI itself as described in [Compile for
Linux](Compile_for_Linux "wikilink") with:

    ./configure
    make

### Windows

You can compile UFORadiant by selecting the correct project in the
[Code::Blocks](Code::Blocks "wikilink") project file. There is also a
[downloadable application](MinGW_Win32_(guided_with_GUI) "wikilink") to
help you easily compile the game with UFORadiant.

## Once installed

The first time UFORadiant start, it will ask you for your UFO:AI
installation folder. Just point it to e.g. . Once you've got it setup,
move on to the [Mapping for Dummies](Mapping_for_Dummies "wikilink")
guide.

[Category:Contribute](Category:Contribute "wikilink")
[Category:Mapping](Category:Mapping "wikilink")
[Category:UFORadiant](Category:UFORadiant "wikilink")