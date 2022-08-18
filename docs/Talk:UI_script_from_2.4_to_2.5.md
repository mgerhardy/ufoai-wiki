## Sprite definition syntax

1\. So should all of my sprite definitions use background instead of
image? I am confused because your example sprite sheet uses image.

`sprite icons/earthlrg {`
`   image "icons/iconpack_gen2" // Switch this line to background?`
`   texl "102 150"`
`   size "102 102"`
`   single true`
`}`

No, sprite syntax do not change, or at least are compatible with the old
one. [But most of nodes must be
updated](https://github.com/ufoai/ufoai/commit/3ad7136085d7a522f73a8e47939f0d47ea50a5cb#diff-10).

- `image "ui/button_green_small"` means it use an image
- `background "ui/button_green_small"` means it use a sprite

Next i will clean up the code to only use sprites.
[Bayo](User:Bayo "wikilink") 18:12, 4 May 2012 (SAST)

Anyway, if a sprite is not defined from the script, [it autogen a
sprite](UFO-Scripts/icons.ufo/2.4-dev "wikilink") using an image with
the same name. [Bayo](User:Bayo "wikilink") 18:18, 4 May 2012 (SAST)