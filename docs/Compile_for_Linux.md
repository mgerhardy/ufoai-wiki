## General

Just run `./configure` and `make` to compile the game.

For the Debian and Debian-based distributions (Ubuntu etc.), refer to
the [Debian](Debian "wikilink") page. [Suse](Suse "wikilink") users
might want to look [here](Suse "wikilink").

## Compile

There are some options available on how to compile the code. Please have
a look at the **`./configure --help`**. After compiling there will be a
dir (where `ARCH` may be `i386`) which includes the binaries. They are
copied by the **makefile** to the right folders. Now you are ready to
run the game by typing **`./ufo`** at the ufoai root directory.

If you use a recent development snapshot from our source code repository
with no separate data package, remember to compile the maps, too (as
described in the document for [Debian](Debian "wikilink")). You can also
grab pre-compiled maps from [mattn.ninex.info](http://mattn.ninex.info)

### Compile for development

After getting the code you just need to do:

    $ ./configure
    $ make

If the compilation fails or strange errors show up, you could try a
"make clean" and afterwards a simple "make", which would build the
source from scratch.

If you are willing to compile the maps ("make maps"), consider the "-j "
(jobs) option to enable parallel compilation.

you will get the number of processor using the following sequence:

    $cat /proc/cpuinfo | grep processor | wc -l

You can create an alias to make change permanent (edit \~/.bashrc )

    alias make='make -j '`cat /proc/cpuinfo | grep processor | wc -l`

### Compile for release

After getting the code you just need to do:

    $  ./configure --enable-release
    $ make

### Compile uforadiant

You have to run configure script with an option to before compiling
uforadiant.

    $  ./configure --enable-uforadiant
    $ make uforadiant

## Distribution notes

- [Debian](Debian "wikilink")
- [Suse](Suse "wikilink")

[Category:Coding](Category:Coding "wikilink")