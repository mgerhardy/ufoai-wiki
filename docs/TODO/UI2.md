**This TODO may be out of date as the UI code has changed but UI2 has
not necessarily been updated. An audit will need to occur to get UI2 in
working order first.**

Full TODO information appears at the top of each .ufo file in /mods/ui2.

Many (but not all) components appear in the _assets\* files.

# Base (bases.ufo)

Note: Base window also includes building construction and alien
containment functions within it.

- Clicking on an aircraft just takes the player to the aircraft window.
  It should also load the details of the aircraft that was clicked.

- Add injured soldiers to employee count icon row

- Alien containment requires several delete cvar calls on cvars that may
  not exist, which leads to errors printed in console.

- Construct building by clicking on the (+) icon next to its capacity
  bar

- Show building preview when clicking on capacity bar.

- Remove BUILD/VIEW STATS button and building construction list.

- Consider how to display building names now that there are so many.

- Several buildings need a small icon for Facilities tab

  - alien containment

  - hangar

  - power plant

  - command

  - intercept (small hangar)

  - radar

  - advanced radar

  - hospital

  - missile battery

  - laser battery

- It would be nice if the full list of all building capacities still
  listed the top 5 first. Order of buildings listed in
  basemanagement.ufo effects in-game order.

- Adjust the color of blocked tiles in the small base selector at the
  top of the base window.

- Maybe improve or create icon to kill aliens in containment?

**Improvements for later**

- Build facility: Make the add building button turn to a warning (red !
  button) if it is too high (if it is antimatter, it should show a
  warning when it is low)

- Build facility: Improve building preview display

- Don't show progress bar in alien containment if alien is already
  researched

- The small base selector at the top should have a drop-down panel for
  each base, when hovering the mouse over it, that shows the base name
  and region (and maybe a symbol for each of the following if they exist
  in that base: dropship, lab, workshop).

## Research (research.ufo)

![](ui_todo_research.jpg "ui_todo_research.jpg")

- \(1\) After clicking on a UFOpaedia link for an item, or
  assigning/unassigning a scientist to a research project, the base
  names for research at other bases disappear.

- \(2\) This should display (scientists hired / (scientists hired in
  this base + scientists unhired). Need new code in the callbacks to get
  hired/unhired scientists as well as hire/fire them with the buttons.

- \(3\) Currently, clicking on the back-to-geoscape button actually
  takes you back to the base. When I try to add an extra ui_pop to it,
  it bumps me all the way to campaign options window (load, save, etc).

- Make research lists scrollable and find a way to test it (ie - I don't
  have a save with enough research options).

- Clicking on a base name in the external research area should take the
  player to that base's research window.

  - Perhaps I should add a little arrow to indicate clicking will take
    the player away from the current window.

## Market

![](ui2_market_window.jpg "ui2_market_window.jpg") Geever is creating a
shopping basket function for the market. Work is just beginning on this
window.

- Make Buy and Sell buttons work.

- Make autosell/stock freeze button work.

  - Autosell clicking seems to change things, but need to test properly
    that it is working.

  - Test that autosell button is hidden on those things it ought to be
    (aircraft)

- Add the price (forgot to add it)

- Make object info panel work.

  - Model not appearing

  - Weapon/firemode selection needs work

- Make ufopaedia icon work properly

- Complete transaction panel when it is available

**Improvements for later**

- Display item info better. This probably requires a rethinking of what
  info is displayed and how it is displayed for all the different item
  types we have. Would effect other windows too, probably.

## Production

Haven't figured out what I want to do with this yet. May keep market
similarities, may try to find a new layout scheme.

## Base Summary

No concept work done. Considering not using this window. I have put
building capacities under the facilities tab on main base window, and
will also add the baselayout panel for easy switching between bases.

- Window removed

## Transfers

No concept work done.

## Aircraft

No concept work done. Will depend on whether or not we can split
equipping to the new soldiers window.

## Soldiers

Entirely new soldiers window needed, since we're getting rid of
employees window. I would love to finally separate equipping from the
aircraft window and put it into the soldiers window, if that's possible.
But either way I expect this window will come at end of dev cycle.

## Hospital

No concept work done. Maybe sub-window in Soldiers?

# Miscellaneous

- Improve art for selectbox, checkbox, and other similar items.

- Improve icon for UFOpaedia

- Fix language font to display all languages.
  [Bayo](User:Bayo "wikilink") 13:29, 6 May 2012 (SAST)

- Single player options menu (singleplayer.ufo)

- Multiplayer options menu (multiplayeringame.ufo)

  - Create IRC icon

- Create new win/lose windows. May or may not use backgrounds and  -
  also see

## Main (main.ufo)

- Initial settings popup window not done (choose your language, name,
  sound settings).

## Campaign (campaign.ufo)

- ~~Add alert~~ if user tries to begin without selecting a load game

  - Button is disabled instead

- Several campaign windows not yet changed (end game, save game, etc.)

**Later improvements**

- Add info about a save when it becomes available (date, bases, top
  soldiers, things like that?)

- Display the data about a campaign in individual parameters and not
  just one chunk of text, using icons, etc.

## Skirmish (skirmish.ufo)

- Team selection broken. If I select a new team and then save before
  equipping, the team is not saved properly. Then, if I try to load it,
  nothing is loaded. Possible workaround: disable the save button until
  the team has been equipped? OR: in the NEW team option, put an equip
  button and don't update the selected team until it has been equipped?

- Make dropship/ufo selection the renders with a prev/next select option

- The map selection system needs to be fit into new style better. The
  border is not right, etc.

- Seem to be missing \*cvar:cl_equip and \*cvar:cl_equipname (player
  equipment). (Not sure what this is, but it was in my notes. Been a
  while since I did this window)

## Options (options.ufo)

- Joystick options and key configuration display not implemented yet

- Add new tab for mods

## UFOpaedia

No concept work done.

# Things to do when finished

- aliencont.ufo contains an empty window which was necessary to override
  the alien containment window in the original UI

- There are lots of items in hud_.ufo that are necessary for the
  default and alternative HUDs (causes errors if I remove them). Should
  locate and remove these items eventually.