## General

The ufo script files can all be found in (see [Directory
tree](Directory_tree "wikilink")). These files include the [menu
definitions](UFO-Scripts/ui/*.ufo "wikilink"), [weapon
definitions](UFO-Scripts/weapon_*.ufo "wikilink") and a lot more. You
might first have to extract the [pk3](pk3 "wikilink") files in

Make sure, that you looked into the [coding
guidelines](Coding/Guidelines "wikilink") before submitting patches.

You can also use comments here:

    // this is a comment for one line
    /* this is
       a comment
       over
       several lines */

## Scriptfiles

- [LUA-AI](LUA-AI "wikilink")
- [UI lua scripting](UFO-Scripts/ui/LUA-scripts "wikilink")
- [ufox, a lua utility library for UI
  scripting](UFO-Scripts/ui/LUA-utility-functions "wikilink")
- [menu (UI) definitions](UFO-Scripts/ui/*.ufo "wikilink")
- [aircraft definition](UFO-Scripts/aircraftmanagement.ufo "wikilink")
- [armour definitions](UFO-Scripts/armour.ufo "wikilink")
- [base, buildings and
  autobuild](UFO-Scripts/basemangement.ufo "wikilink")
- [campaign definitions](UFO-Scripts/campaign.ufo "wikilink")
- [character template
  definitions](UFO-Scripts/team_templates.ufo "wikilink")
- [cities definitions](UFO-Scripts/cities.ufo "wikilink")
- [map entity definitions](UFO-Scripts/entities.ufo "wikilink")
- [equipment definitions](UFO-Scripts/equipment.ufo "wikilink")
- [font definitions](UFO-Scripts/fonts.ufo "wikilink")
- [inventory definitions](UFO-Scripts/inventory.ufo "wikilink")
- [maps definition](UFO-Scripts/maps.ufo "wikilink")
- [message options](UFO-Scripts/msgoptions.ufo "wikilink")
- [message categories](UFO-Scripts/msgcategories.ufo "wikilink")
- [music definitions](UFO-Scripts/music.ufo "wikilink")
- [nations definition](UFO-Scripts/nations.ufo "wikilink")
- [particle definitions](UFO-Scripts/ptl_*.ufo "wikilink")
- [research definitions](UFO-Scripts/research.ufo "wikilink")
- [sequence definitions](UFO-Scripts/seq_*.ufo "wikilink")
- [character skin definitions](UFO-Scripts/skins.ufo "wikilink")
- [static campaign](UFO-Scripts/staticcampaign.ufo "wikilink")
- [team definitions](UFO-Scripts/team_*.ufo "wikilink")
- [tip of the day](Tip_of_the_Day "wikilink")
- [weapon definitions](UFO-Scripts/weapon_*.ufo "wikilink")

## Available [commands](commands "wikilink")

You can get a command list by typing

    cmdlist

in the game [console](console "wikilink"). There are some commands that
are only available after starting a single player game.

## Available [cvars](cvars "wikilink")

You can get a cvar list by typing

    cvarlist

in the game [console](console "wikilink").

## Offline viewing

You can view a command list or cvar list outside of the game by using
the

    logfile 1

command prior to using the cmdlist or cvarlist command, if it's not
already in your console log file. This will have the list placed into
the log file which can then be viewed directly after you exit the game
and prior to running the game again. Keep in mind that you may have to
clean this output up. Replacing the date and time with an empty string
should do the trick quite well. You should be able to use a simple text
editor like notepad for this task. You can find the console log at
base/ufoconsole.log.

## Adding campaigns

- Add a [new campaign](Create_campaign "wikilink") to the game

## Links

- [Datatypes](UFO-Scripts/Datatypes "wikilink")

[Category:UFO-Scripts](Category:UFO-Scripts "wikilink")
[Category:Contribute](Category:Contribute "wikilink")