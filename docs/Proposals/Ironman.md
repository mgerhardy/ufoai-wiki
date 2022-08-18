## Ironman mode

This article describes an ironman mode, which is intended to force a
player to play "fair", i.e. without loading an old savegame. It is an
extra challenging mode for those who prefer to play that way.

## How it works

At the start of any new campaign, the player is given the opportunity to
play the campaign in ironman mode. If the player does not choose to do
so the campaign works as normal. However if the player chooses ironman
mode, there are a few differences.

Firstly the player has to choose a save slot. This slot will be where
the player's game will be saved, and no other slots can be used to save
the game. Furthermore, the player can only manually save when exiting
the game. The save button on the menu should be disabled. The game is
automatically saved in the following circumstances:

- When the player exits the game. The player can not choose not to save
  the game.
- Periodically, in real time (but not on the battlescape).
- Whenever a mission starts. The game is saved as if the player had lost
  the mission; either a complete defeat or an unfavourable outcome of
  autoresolve. This goes for all missions, so in case of base defence
  missions the consequences of the destruction of the base should be
  pre-calculated at mission start.
- Whenever a mission ends. The outcome of the mission overrides the one
  saved in the pre-mission save, even if the player chose autoresolve.
- Ideally, on every big event on the geoscape that affect the player,
  such as an installation being bombed, a craft being shot down or
  completion of research.

## Security and risk

Because the player only has one save slot available, his savegame is
more vulnerable than normal. The saved file might get corrupted somehow,
or accidentally overwritten by another save from a normal campaign game.
There should be some mechanic to safeguard the data from such
occurrences.

To prevent savegame overwriting, one could disallow writing to a save
slot that contains an ironman save. The save should still be deletable
from within tha game, but with a confirmation message.

To prevent data corruption, the game could be saved in two locations at
the same time.

[Category:Proposals](Category:Proposals "wikilink")