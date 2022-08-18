The **`skin`** script allow to describe skins the engine will use for
actor models (at the moment, only for human skins). It is not used for
the gameplay, but only for the look and feel.

Model file embed a list of skin name. The engine only use the first one
to find image file name. Others are not used, but can be, anyway, useful
for third party model viewers and editors. The engine

## Script

Each skin is describe with the keyword `actorskin`. It contain a string
id (used to find image file name), a name (displayed in the user
interface) which is translatable, and some properties.

singleplayer: [V_BOOL](V_BOOL "wikilink"): Describe if we can use this skin in single player mode.
multiplayer: [V_BOOL](V_BOOL "wikilink"): Describe if we can use this skin in multiplayer mode.

## Example

This example register a `foo` skin to the game. The game will search for
skins using `_foo` suffix. This skin is available in both multiplayer
and singleplayer game.

    actorskin foo {
        name        "_My foo skin"
        singleplayer    true
        multiplayer true
    }

## Resolution of image skin name

The engine use three things to found the file name used for a skin.

- The first image defined of the embedded skin defined inside model
  file. Most of the time it is the name of the model itself.
- The separator `_` (underscore) for readability.
- The actor skin id as suffix.

For example: It exists a model called `body.md2`. It embedded the skin
file name `body`. And it exists an actor skin name called `forest`. The
engine will check the image filename `body_forest`. If this image do not
exists, the engine will use the default skin name.

- `base/models/soldiers/foo`
  - `body.md2`
  - `body.jpg`
  - `body_forest.jpg`

## Script order

The engine use the first embedded skin from models. It is a special case
cause here - it doesn't use any suffix. To avoid loading error, the
engine must read this skin entry on first, and this skin must be called
`default`.

    actorskin default {
        name        "_Urban"
        singleplayer    true
        multiplayer true
    }

It is anyway an artificial order limitation. We should fix it with code.
**Patch is welcome.**

## Sharing actor skin

![](Swat4.png "Swat4.png") We can share an own actor skin with a
[pk3](pk3 "wikilink") file. You can check for an example of skin.

To use this file, we can move it on the game directory, or on the home
directory. It add a new "Elite" skin, for the multiplayer mode only.

Some notes:

- A [pk3](pk3 "wikilink") can contain more than one new actor skin.
- It should not overwrite official content.
- The script should be prefixed with `skins_`.
- Actor skin name and script should avoid conflict name.

## Multiplayer limitation

The game engine only share numerical skin id, and not named skin id. If
a player use a custom actor skin, we don't know if other people will see
the same model. Anyway the player himself will see the right model.
**Patch is welcome**.

If all players use the same [pk3](pk3 "wikilink") files, and the same
game content, all players will have the same right result.

[Category:UFO-Scripts](Category:UFO-Scripts "wikilink")