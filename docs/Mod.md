## General

UFO:AI supports mod development. The main mod is the mod. To create a
new mod, just create a new directory in the UFO:AI directory. E.g. name
it . Start UFO:AI with

`./ufo +set fs_gamedir mymod`

Every file that is "overwritten" in your mod takes the precedence over
the files in the directory. Of course you can also add new files with
this. New maps, new scripts, new textures and so on.

It's also possible to switch the mod from within the game. In this case
only some subsystems are restarted (in order to load the right files
with the right priority). Use to switch it, or to list them. If there is
no parameter given, it will list all the available mods, if there is a
parameter given, it will activate the mod given by this parameter.

## Server logic (Battlescape)

Modding the battlescape is possible by providing your own game lib. The
code for our main game is in .

## Client logic

Modding the client logic is possible, too. We already have
[gametypes](ClientGame "wikilink") implemented for multiplayer, skirmish
and campaign. The code for our main games is in

[Category:Contribute](Category:Contribute "wikilink")
[Category:Modding](Category:Modding "wikilink")