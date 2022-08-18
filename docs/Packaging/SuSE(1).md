If you're a [SUSE](Suse "wikilink") User, you don't have to worry about
Installation, not even about upgrades!

This Tutorial is based on YAST2, but if you're using another package
manager within SUSE Linux / openSUSE, you probably figure out how to do
it.

Steps to get UFO:AI Installed

- Open YAST2 as superuser
- Choose **Sotware** in the left menu and **Installation source** in the
  right pane
- Add the following repository:

`Type: `*`HTTP`*` - Servername: `*`download.opensuse.org`*` - Directory: `*`repositories/games/`<SUSE_Version>`/`*
`   For the moment, `<SUSE_Version>` can be one of`
`   * openSUSE_10.2`
`   * openSUSE_10.3`
`   * openSUSE_Factory`

In latest SUSE versions you can add repository URL, which is faster and
easier to do. Just add the URL :

[`http://download.opensuse.org/repositories/games/`](http://download.opensuse.org/repositories/games/)<SUSE_Version>`/`

There are even some mirrors around, so in case you experiance bad speed
when installing the game (especially on the data blob), try to point to
a mirror. Normally, there should be no need for this, as
download.opensuse.org is redirecting to international mirrors for
downloads.

- Confirm possible appearing dialogs about GPG Keys (The repository is
  signed for your security)
- Click **Finish** (this might take a while, especially on SUSE Linux
  \>= 10.1)
- Go to **Software Management**
- In the searchbox, enter **ufoai**, then click **search**
- UFO:Alien Invasion is shown as a result (three hits, including map and
  music files). Select the package **ufoai**
- Click **Accept** (This will start the Dependency check and
  automatically select ufoai-data and possible other packages.
- The game will be installed (maybe you even have to insert the
  installation CD of SUSE Linux)

When this step is done, you can leave YaST and start UFO: Alien Invasion
from the Startmenu. You should find it in Games/Strategy

Commandline installation using smart (apt-like package manager):

`su`
`smart channel --add games type=rpm-md name="games" baseurl=`[`http://download.opensuse.org/repositories/games/`](http://download.opensuse.org/repositories/games/)<SUSE_Version see above>
`smart update`
`smart install ufoai`

Have a lot of Fun!

--[DimStar](User:Dimstar "wikilink") 12:49, 16 November 2006 (CET)

[Category:Packaging](Category:Packaging "wikilink")
[Category:Contribute](Category:Contribute "wikilink")