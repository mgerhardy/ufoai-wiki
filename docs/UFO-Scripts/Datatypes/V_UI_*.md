## V_UI_EXCLUDERECT

- Todo

## V_UI_CVAR

- Todo

## V_UI_DATAID

- Todo

## V_CVAR_OR_FLOAT

- Todo

## V_CVAR_OR_STRING

- Todo

## V_UI_NODEMETHOD

- Todo

## V_UI_SPRITEREF

Structure identify a set of sprites. Properties use this type can be set
with the name of the sprite set.

The sprite set name is usually a prefix of images relative to the path
`base/pics/`. But there is way to define sprite description with `.ufo`
scripts.

For example the name `buttons/big_blue` will identify the set:

- `base/pics/buttons/big_blue.png`
- `base/pics/buttons/big_blue_disabled.png` (if it exists)
- `base/pics/buttons/big_blue_hovered.png` (if it exists)
- `base/pics/buttons/big_blue_clicked.png` (if it exists)

And widget will use it accrding to the status it is need.

## V_UI_ICONREF

Do not exists anymore.

See [\#V_UI_SPRITEREF](#V_UI_SPRITEREF "wikilink").

## V_UI_ACTION

- Todo

## V_UI_OPTIONNODE

- Todo

## V_UI_ALIGN

![](Text_position.png "Text_position.png")

ALIGN_UL: up-left
ALIGN_UC: up-center
ALIGN_UR: up-right
ALIGN_CL: center-left
ALIGN_CC: center-center
ALIGN_CR: center-right
ALIGN_LL: low-left
ALIGN_LC: low-center
ALIGN_LR: low-right

[Category:GUIs](Category:GUIs "wikilink")
[Category:UFO-Scripts](Category:UFO-Scripts "wikilink")