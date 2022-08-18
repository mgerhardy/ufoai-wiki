## Installer or packages

To generate the pk3 game archives you should type `make pk3`. The
[pk3](pk3 "wikilink")-files are normal zip files (this step is
optional - you don't have to pack the data into pk3 files).

- [Windows](Packaging/Windows "wikilink")
- [SuSE](Packaging/SuSE "wikilink")
- [Debian](Packaging/Debian "wikilink")
- [Fedora](Packaging/Fedora "wikilink")

## Special cvars

Packagers can add these cvars to their start script to change the game
data path and/or the locales path.

- fs_basedir \[string\]


The path of the gamedata files

- fs_i18ndir \[string\]


The path of the gettext files

- fs_usehomedir \[0\|1\]


Use the homedir to save screenshots and savegames (default)

Just start UFO:AI e.g. via

    ./ufo +set fs_basedir /usr/games/ufo +set fs_i18ndir /usr/share/locales

## Links

- [Create release notes](Coding/Create_Release "wikilink")

[Category:Packaging](Category:Packaging "wikilink")
[Category:Contribute](Category:Contribute "wikilink")