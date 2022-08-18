## Cameras

A camera allows the specified team to increase their view radius.
misc_camera is only available in single player mode.

To add a camera right click on any 2D view window to bring up the
Context menu. Choosing 'Create entity' and select misc_camera.

The spawnflags property is used to set levelflags for the model.

## Keys

- **origin**: the position of the model
- **spawnflags**: level flags, rotate
- **team**: the team this camera belongs to
  - 0 = civilian
  - 1 = phalanx
  - 7 = alien (will not effect AI behaviour at this time)
- **targetname**: the id of this entity
- **active**: 1 = active, 0 = inactive. You can define whether this
  camera is active (or whether it must be activated by e.g. a
  trigger_touch)
- **group**: This e.g. allows several cameras to be turned on/off by one
  trigger_touch.

## Links

- [Entitylist](Mapping/Entities "wikilink")

[Category:Contribute](Category:Contribute "wikilink")
[Category:Mapping](Category:Mapping "wikilink")
[Category:Entity](Category:Entity "wikilink")