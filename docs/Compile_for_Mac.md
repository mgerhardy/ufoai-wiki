## macports

### Step 1. Installation

Install Xcode, X11, and MacPorts

Instructions are at This will have you install Apple's X11, the Xcode
development environment (needed for the compiler, etc), and the MacPorts
program.

You can also download the X11.app from

### Step 2: Install dependencies

`sudo port install libsdl-framework libsdl_mixer-framework libsdl_ttf-framework \`
`jpeg libpng XviD libtheora gtk2 gtkglext gtksourceview2 git p7zip python27 \`
`doxygen libsdl2 libsdl2_mixer libsdl2_ttf`

Now you should be able to [fetch UFO-AI](Getting_the_source "wikilink")
and compile it.

### Step 3: Compilation

UFO:AI compilation requires some paths that are not taken care of for
you by the MacPorts installation process. Therefore, a minor edit to
your .profile is needed.

If you don't understand the preceding sentences: (a) Download
TextWrangler (freeware) from ; (b) Use its File \> Open to navigate to
your home folder and enable its "Show hidden files" option; and (c) Open
the ".profile" file you should see now so you can edit it.

Toward the bottom, substitute this export command:

`export PATH=$PATH:/opt/local/bin:/opt/local/sbin:/opt/local`

Save the file, quit Terminal, then relaunch Terminal to make the new
PATH operative.

Now, the following "make" commands should execute without errors. You
should also be able to compile newer versions of UFO:AI without editing
.profile again, i.e., this is a one-time fix.

Change directory into the main ufoai folder.

`cd ufoai`

Establish the appropriate configuration for compiling.

`configure`

To compile the binaries, just type (after the configure call was
successful).

`make`

after that, you need to create the languages and maps

`make lang models maps-sync`

To create the application bundle (i.e., a .dmg), just type

`make macinstaller`

## fink

After installing fink you should just type the following to your
console:

`fink install sdl sdl-ttf sdl-mixer libtheora0 libjpeg8 libpng15 libxml2 libcurl4 xvidcore gtk+2 gtksourceview2-dev gtksourceview2-shlibs gtkglext1 glib2-dev glib2-shlibs`

[Category:Coding](Category:Coding "wikilink")