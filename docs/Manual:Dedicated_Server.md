## General

To set up the dedicated server you have to install the pk3 files that
are included in the installer or download the
[data.tar](http://sourceforge.net/project/downloading.php?group_id=157793&filename=ufoai-2.1-data.tar)
from one of the sourceforge.net mirrors. Of course you can also use the
data from our [Subversion](SVN "wikilink") repository.

You need the binary to start a dedicated server. The first map started
is the map that is the first one listed in the mapcycle. Use the
[command](commands "wikilink") to start a map - use the command to list
all valid and installed maps.

The command is here to list all predefined gametypes from the [ufo
script files](UFO-Scripts "wikilink") from or the
[pk3](pk3 "wikilink")-files. You can change the gametype before you
start a map - just type and then start the map with the above given
[command](commands "wikilink").

## Mapcycle

There is a where you can define the maps that you want to play on the
server. The format of this file is:

    mapname gametype

and comments are allowed here (/\* comment \*/).

You can show the current mapcycle from the dedicated server console by
typing  - you can load the next map on this cycle by typing and clear
the list by typing .

If the mapcycle is empty the server will restart the current map with
the current gametype.

You can also add the command to the in your directory - this ensures
that always the first map of the mapcycle is loaded when the server was
started.

## Maps

You have to make sure that you are using the correct maps. If you are
hosting a dedicated server for a developement release, make sure to use
the python map-get-script from to be always up-to-date. Also note that
if you compile the maps yourself, you have to compile them on an intel
pc. This is due to the fact that different CPU vendors have a different
floating point precision - that will not survive the crc check.

## Downloading of maps

UFO:AI supports downloading of maps (and other files) via http. There
are some [cvars](cvars "wikilink") you have a look at:

-

-

-

-

### Filelists

If a map needs other files like ambient sound files, you can use the
**filelist** feature. Just put a file into your download directory that
has the name . This file should contain all the files that are needed to
play that specific map.

## Rcon

The remote console is a possibility to set some settings from a
connected client, restart maps or change gametypes.

You have to set the cvar on the serverside - you can add the following
to the dedicated.cfg:

    set rcon_password <password>

. On the client side you have to set this cvar too while connected.
After that you are able to execute rcon [commands](commands "wikilink")
via:

    rcon <command> <parameter>

## Links

- [Multiplayer cvars](Multiplayer_cvars "wikilink")

[Category:General](Category:General "wikilink")
[Category:Multiplayer](Category:Multiplayer "wikilink")
[Category:Manual](Category:Manual "wikilink")