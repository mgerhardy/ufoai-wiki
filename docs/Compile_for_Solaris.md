## General

Just run `./configure` and `gmake` to compile the game.

**Note :** I'm using Solaris Express Developer Edition 05/07
([SXDE](http://developers.sun.com/sxde/)) with
[oss](http://www.opensound.com) Drivers, with Solaris 10, you may have
others steps to do.

## Requirements

- gcc <sup>1</sup>
- gmake <sup>1</sup>
- a PATH to use gcc ( PATH=\$PATH:/usr/sfw/bin:/usr/ccs/bin )

<sup>1</sup> : included in SXDE

## Compile

After getting the code you just need to do:

` $ ./configure`
` $ gmake`

There are some options available on how to compile the code. Please have
a look at the **./configure --help**. After compiling there will be a
**debugARCH/** dir (where ARCH may be *i386*) which includes the
binaries. They are copied by the **makefile** to the right folders. Now
you are ready to run the game by typing **./ufo** at svn root.

**Note :** the `gmake update-po` fails

If you use a recent SVN snapshot with no separate data package, remember
to compile the maps, too. You can also grab pre-compiled maps from
[mattn.ninex.info](http://mattn.ninex.info)

## OpenSolaris

<https://sourceforge.net/apps/mediawiki/pkgbuild/index.php?title=Pkgbuild_on_OpenSolaris>

[Category:Coding](Category:Coding "wikilink")