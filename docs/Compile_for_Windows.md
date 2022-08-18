__TOC__

## Building UFO:AI 2.6-dev

To compile UFO:AI you need to set up a build environment: a compiler,
linker, the necessary libraries and headers; then compile the sources.
Compiling can happen from command-line or using IDEs (Integrated
Development Environments)

### Build environment

#### MSYS2

Download and install i686 version of MSYS2 and update its package
repository via **pacman** as described on their . At time of writting
UFO:AI for Windows compiles in 32bit mode only.

Using MSYS console run the following command to install dependencies:

`$ pacman -S mingw-w64-i686-SDL2 mingw-w64-i686-SDL2_mixer mingw-w64-i686-SDL2_ttf \`
`  mingw-w64-i686-libtheora mingw-w64-i686-libjpeg-turbo mingw-w64-i686-libpng mingw-w64-i686-curl \`
`  mingw-w64-i686-xvidcore mingw-w64-i686-libxml2 mingw-w64-i686-openal mingw-w64-i686-gcc \`
`  mingw-w64-i686-gdb mingw-w64-i686-binutils mingw-w64-i686-glib2 mingw-w64-i686-gtk2 \`
`  mingw-w64-i686-gtkglext mingw-w64-i686-gtksourceview2 mingw-w64-i686-atk \`
`  mingw-w64-i686-pkg-config mingw-w64-i686-lua51 mingw-w64-i686-googletest mingw-w64-i686-make`

### IDE / compile

#### Code::Blocks

Download and install (or extract if you prefer the *nosetup* variant) of
Code::Blocks from but **DO NOT** launch it yet.

We have to help Code::Blocks to find the MinGW-W64 compiler and it's
includes/libraries. The easiest way to do this is adding new compiler
definitions via the new(ish) XML interface. If you launched Code::Blocks
already it generated a configuration file and it won't load available
compilers from the XMLs.

Add and to *share\CodeBlocks\compilers\\* directory under Code::Blocks'
installation path.

Add MSYS/MinGW-W64 bin directory to the PATH environment variable. This
makes sure Code::Blocks will find the compiler, also that the game find
the DLLs it need. Depending on your Windows version there are different
ways to set the PATH environment variable. It is also an option to
create a batch script to start Code::Blocks with the PATH extended for
that session only: *(change paths to fit your installation)* ﻿

<div class="toccolours mw-collapsible mw-collapsed" style="overflow:auto;">

**codeblocks.bat**

<div class="mw-collapsible-content">

    SET PATH=%PATH%;C:\msys32\mingw32\bin\;

    "C:\Program Files (x86)\CodeBlocks\codeblocks.exe"
    ﻿

</div>
</div>

Start Code::Blocks, it should find and suggest using the *MinGW-W64
i686* compiler.

If you plan to contribute, please read our
[Coding_guidelines](Coding_guidelines "wikilink") and configure
Code::Blocks properly.

Click File/Open and load from your Git clone ([Getting the
source](Getting_the_source "wikilink") if you don't have it yet). This
will load the individual project files from the same directory.

Hit to compile or to recompile all.

## Building UFO:AI 2.5 and earlier

*(Old documentation, feedback is welcome)* You must first compile the
source code. We recommend using Code::Blocks for this. There is also an
(experimental) compile guide using Eclipse CDT with MSYS/MinGW. More
instructions can be found here:

- [Code::Blocks](Code::Blocks "wikilink")
- [Eclipse](Eclipse "wikilink")

[Category:Coding](Category:Coding "wikilink")