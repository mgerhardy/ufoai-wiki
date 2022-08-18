## Confirm actions

"Confirm action" mode for moving and aiming/shooting

Do not confuse this with default moving/shooting behaviour (i.e. one
click =\> action)

### Where the behaviour is used

- Battlescape -\> Own turn -\> Soldier-control
- "Confirm Actions" must be enabled in Options -\> Game -\> Confirm
  Actions

### Summary

**Moving** (default mode in battlescape):

When having a soldier selected one can move it around by hovering the
cursor over the destination "tile" with the mouse and click (<LMB>) to
enter "Pending mode" (the soldier does nothing at this point).

The game displays "Pending" mode by drawing a destination marker at that
location (additionally to the mouse cursor) and a line that follows a
calculated path trough all tiles toward the destination (if there is
one).

When the player is sure that the destination is the correct one he can
confirm the move (action) by either executing the "confirm action"
command (<Enter>) or by clicking on the destination tile again (<LMB>)

To exit "Pending mode" one can use the <RMB>. This will return you to
default mode (Moving).

Clicking on any other tiles than the already chosen destination tile
will alter the destination marker to be displayed there (and the path
and all other information being updated to that location).

TODO: A detailed description of the various info that is displayed next
to the cursor (and the dest-marker)

**Shooting**

Exactly the same behaviour as for moving with the following differences:

- Different cursor (duh) for mouse and destination-marker.
- A straight line (or ballistic line - depending on the weapon) is drawn
  instead of the "moving path".
- The action after successful confirmation will be controlled by the
  chosen action for the weapon/item. (duh again)
- Instead of moving TUs there will be information about the chosen
  weapon/item/firemode displayed here. Details: TODO

### Notes

- Default keys/user commands are represented in brackets like this:
  <KEY>
- The single 3d "cells" on the battlescape are refered to as "Tiles".