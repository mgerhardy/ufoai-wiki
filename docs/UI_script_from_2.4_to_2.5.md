## Component syntax

- Component syntax was unclear. Now it use the same syntax as `window`
  with `extends` keywork. Be carefull the order of the terme change.
  - `component my-component extends another-component` instead of
    `component another-component my-component`

## Extension of sprites to merge code

Sprite support now tiled image we use for button and window. For a first
small step, the file `base/ufos/sprites_tiled.ufo` contains all
descriptions of tiled sprites
[1](https://github.com/ufoai/ufoai/blob/master/base/ufos/sprites_tiled.ufo).
But idea is to move later this properties next to image, and syntax will
change.

On a side note, we can now use tiled or untiled sprites for most of the
nodes, and we can easilly add more tile templates if it is need
(bigger/smaller borders...)

- `image` is deprecated for most of nodes
  `window`/`button`/`panel`/`optionlist/checkbox`/`optiontree`... Others
  will come later. We must use `background` property which is a sprite.
  - `base/ufos/sprites_tiled.ufo` curently override old image name with
    new sprite name. Then for nodes which support background, it should
    only need to rename the `image` propery to `background` property.
    [2](https://github.com/ufoai/ufoai/commit/3ad7136085d7a522f73a8e47939f0d47ea50a5cb)
- `custombutton` is then useless and deprecated.
  - A simple rename to `button` should work.
    [3](https://github.com/ufoai/ufoai/commit/7cdd243b27fd942ab03b40458a3e88804c45594d)
- tiled images should be moved into `base/pics/tiled`
- Cause we use sprites, image for checkbox is not at the same location,
  and it do not use anymore `image`, but sprites.
  - Two components have been created: `checkbox_blue` and
    `checkbox_green`. You can check the code on the file `_menu.ufo`.
  - images are located inside `pics/banks/checkbox_*`, and next
    everything will be splited into `pics/icons/checkbox_*`
  - while images are not splited, script `ufos/sprites_tmp.ufo` contains
    name of the sprites used to the checkboxs (which will became later
    name of image inside `pics/icons`).

## Event callback

- click event are detected on the mouse up, and not the mouse down
- a click event can be disabled with another button down. Left button
  down, then right button down, then left button up, then right button
  up will not produce any click event.
- `onScroll`/`onScrollUp`/`onScrollDown` is now fired to parent nodes if
  the node do not catch it. An empty event will stop the propagation
  (`onScroll {}`)
  - click events will follow the same way

<!-- -->

- `panel` node is scrollable by default with mouse wheel/long left
  click/drag move.

[Category:GUIs](Category:GUIs "wikilink")