**This TODO is outdated since we have LUA UI.**

This page is about the **user interface toolkit** (feel free to proposal
a better name), a kind of library used by UFO:AI to create graphic user
interface. This page is not about game user interface, but only about
features and code powered user interfaces, then nothing about gameplay.

This list includes tasks that may be done to clean up the user interface
toolkit. Its not a closed list, feel free to add thing or comment it.

## On the mind

- Script

  Do not manage anymore ourself GUI "action" script (everything inside
  confunc node, func node, and events), but use the know library for it.
  It need some works to select a library that do not contraint our way
  to work. It can be subsequently use in another part of the game.

  Here some candidates selected cause it is C-like and typed script
  languages:

  - (looks easy to bind, do not feature nested function)

  - (a very small documentation)

<!-- -->

- Sprite integration

  The current code use "sprite" objects, witch mean a piece of texture
  with a random size we can display according to a status (normal,
  disabled...) This exists to easily work with, but the idea is to merge
  all this little pieces of images before packaging the game (to reduce
  texture number, and size, and feature texture size with a power of 2).
  The code to it exists, but ATM we do not automatically integrate it to
  the release.

<!-- -->

- Android portage

  We can, with a relativly low cost feature the skirmish mode for mobile
  phone. We only need to redone few windows. It can be a way to improve
  the GUI features, especially with touchscreen inputs (code), with
  realtime screen orientation adaptation (code), and with
  multiresolution GUI (code/packaging).

## C++

Rework of the code with classes. It is mostely about widget, the core
code also can need classes here or there, but there is no problem for
conversion.

- convert behaviour to classes

- clean up classes, clean up code, clean up methods

- rework behaviour registration

- convert classes to real node classes (merge data inside)
  - need to think about a way to convert it
  - need to check inheritances and properties...

- clean up data

- \o/ retirement

## Request

Things need somewhere...

- Tooltip for options
  - display it
  - set it from client code

## Just do it

Easy tasks

- dichotomic search for properties
  - create a list of all properties per behaviour (a lot of dup pointer,
    but very fast)
- rename `invis` into `visible` (not so easy)
- convert background into panel
- fix the hack to prevent freed of data we want to register (mn_data)
- we should clean up code from loaded/new/clone
  - create uml schema and think about improvment... (function to clone
    function to alloc memory...)
- clean up the code
  - Delete UI_CheckCvar and UI_SetCvar (move the code to the client
    code, and use cvar listener)

  - cleanup `@todo`

  - add an example on the doxygen header of each nodes

  - check VID_NORM_\* use versus viddef.virtual\*

  - fix "mn_" prefix, some cvar from ui modele use "mn_sys_"

  - rename all "menu" occurrence into "ui" (a menu is a specific widget
    of a GUI)

  - create a more modulare code (reduce inter module dependencies, ie.
    ui_timer) to allow more unittest (and cleaner code)

  - rename behaviour into widget (more understandable)

  - rename cinematic package to video -\> conflict with cl_video (a
    little outofscope anyway)
- `image`
  - move properties

    - Need first to remove use of `texh` and `texl` in another nodes

  - we can add some new properties if need [:Image:Pics node
    proposal.png](:Image:Pics_node_proposal.png "wikilink")
- `model`
  - Clean up the code
  - Need a better review (auto scale...) I think mattn fix it.
- `window`
  - Merge the code used to drag the window with the window code
  - If need, create a new window node to split fullscreen windows and
    floating windows.
- `spinner`
  - Rework the sprite to use anyway an only one sprite (to reduce glitch
    when we use low res).
- `text`
  - Stop spliting text every frame.
    - In this case, we can create a new node for text only (no text
      list, no tabbed list) to have a cleaner code.
- `video`
  - Fix ogm/roq memory to allow real multi instance. Else using more
    than one video node should be buggy.

  - implement stop/start feature (more than a simple task, and not
    really need anyway)

## Big tasks

Need some planification before working. It need some days or some month
of work. Or there is dependencies with other tasks.

- \[must\] `container`
  - move the "base container list" into a new node
  - split object move
    1.  dnd start: remove the object from the source
    2.  dnd drop: add the object to the target (should we compute TU
        here?)
    3.  dnd finish without drop: add again the object to the source
- focus code
  - review the main keyboard handler code

  - fix focus navigation with "tab" key

  - fix focus execution of a node with "return" key

  - update textentry events, we should add a validate event (when we
    explicitelly type return key). At the moment we control can't loose
    the focus without calling cancel or change, and it make problems
    (IRC need and event to send the buffer).

  - check the focus code. provide a callbak for nodes (`onBlur`,
    `onFocus`).
- clean up node structure
  - find a better way for cvar properties, it currentelly use a very
    hard to understand code

  - clean up extradata from the node structure
- clean up the script
  - [TODO/User_interface_toolkit//Script](TODO/User_interface_toolkit/Script "wikilink")

  - merge `*foo disabled true` -\> `*node:foo@disabled = true`

    - Attention the first is relative to the window, the second before
      the window (the default first token is a window name). But `*foo`
      and `*node:root.foo` should be the same object.
    - ~~then remove `node:`, because its the default~~ reserve 'foo'
      without prefix for local var, or thing like that

  - optimisation: do not read every time const path/float/..., but cache
    the result (easy, at runtime, or into a postcomputing function)
    (attentions, extended windows)

  - allow to debug const path at runtime (it is not every time the case)

  - find a way to remove casts. It can be a hard job. We can think about
    caching RAW value at runtime, and add a type checking embedded with
    the RAW value. It can be a nice way to split parsing function into
    more simple functions. (very important, because, cast is only an
    help for the code, not for the script programmer)

  - open idea: instead of cvar:foo, using cvar(foo), the same for nodes
    (like an instanciation, is it more readable?)

  - open idea: should we use `;` between actions (C style, more easy to
    parse)

  - open idea: cvar and node without '`*`'
- confunc
  - remove confunc every it is possible (now we can use func with
    param). We should only use confunc for interface.
- `text node`.
  - slipt tabbed text into a table node
- integrate sequences into menu code
  - check sequence langage
    - what is about content description
    - what is about control
  - idea:
    - implement missing control
    - allow to call function with a "multitask" way (run in background)

## Open ideas

Only some idea without big reflexions. Is it need? doable?... easy or
not.

- memory optimisation
  - reduce the size of a node (at the moment 548 bytes per node)
    - is node name need a full buffer? Never we change the name? Is it a
      design to reduce clusering?

    - we can allow nodes with not the same memory size (only use
      extradata need)

- advanced nodes/node improvment/interactions
  - ~~create a composite spinner (*textentry*+*spinner*)~~
    - It should be the job of a component
  - ~~add a common `compositelist` (with a vertical scroll) to create a
    vertical table with composite nodes (for example: text + checkbox)~~
    - ~~More easy, we can create a cloner
      [TODO/User_interface_toolkit//Cloner
      proposal](TODO/User_interface_toolkit/Cloner_proposal "wikilink").~~
      - It should be the job of a component + dyn allocation

- \[must\] creating real components supporting encapsulation (creating
  self properties and function)

- \[think\] reworking function
  - move confunc outside nodes (confunc is a global access from client,
    remove )
  - allow to call function from client (instead of using confunc)
  - \[think\] spliting function and node (function will became something
    like a node property)

- \[wich\] support smooth move of nodes (translation feature)

- \[should be a must\] using a know script (LUA?) instead of self
  language
  - stoping self language developpement
  - need to evaluate speed changes

- icon and icon structure
  - \[must\] rework icons to use a more quake-frendly way (filename with
    suffix, remove icon mapping)

  - \[must\] remove all icon package (not easy to use, need a mapping)

    - Now there is tool to extract icons and to create icon package

  - \[wich\] if it is possible, allow hi-res icons (IMHO, this feature
    need again to use mapping)

  - \[experimental\] use SVG icons inside `./src/icons/` and create a
    make command to generate PNG inside `./base/...`

- redure complexity of scripts
  - ~~think about style for node ([support a subset of
    CSS](TODO/User_interface_toolkit/CSS_for_UFOAI "wikilink"), or reuse
    attributes between nodes)~~
    - components can do the job for the moment.

- Update mouse event mamnagment to translate some events to parent.
  `mouseEnter/mouseLeave` (every time), `mouseWheel` (when the node dont
  custom it), `mouseClick` (when the node dont custom it, but we should
  check XHTML/JavaScript specifications), `mouseMove`?

- `spinner`
  - spinner extension with a vertical slider

- create an horizontal slider

- `item`
  - Use 3D armour

- `string`
  - Improve the text layout

- `confunc`
  - find a way to display usage of confunc with param

- `option`
  - check if we can merge option with node (+/-)

- generalisation of the "icon" image loading for all the UI module. It
  can provide a common way to store image (abstract way without non
  power of 2 limitation), more flexible status, reduce number of
  textures.

## Bugs

- vertical missaligned text gliph
- wrong cut into text glyph
  [1](https://sourceforge.net/tracker/?func=detail&aid=2627571&group_id=157793&atid=805242)
  ; font size from font.ufo dont work?
- A warning is displayed when we start a skirmish.
  - tipoftheday push dont find menu_main; why menu_main init is executed
    here? why something push menu_main?
  - maybe something push menu_main and close it before init is executed
    (or before cmd into init command) ?

## Proposal

Feel free to add some things...

- [TODO/User_interface_toolkit//Popup](TODO/User_interface_toolkit/Popup "wikilink"),
  work around popups

[Category:GUIs](Category:GUIs "wikilink")
[Category:TODO](Category:TODO "wikilink")