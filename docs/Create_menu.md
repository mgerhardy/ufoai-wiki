## General

Our menus are scripts in . If you want to generate a new menu you have
to do several things:

- Create the images for this menu (in )
- Create the script files for this menu (in )
- Read [UFO-Scripts/ui/\*.ufo](UFO-Scripts/ui/*.ufo "wikilink") to get
  into the menu scripts. You can also find a lot examples at .

## Create the script files for a new menu

Please see our [menuscript
descriptions](UFO-Scripts/ui/*.ufo "wikilink") for more information
about the syntax and semantic of the several menu script entities

## Using the editor

We have a built-in editor that can be used to edit the menus. You have
to open the [game console](Console "wikilink") and type the
[command](commands "wikilink") . This opens a menu with some control
panels that allows you to select and modify the menu nodes. To save
these changes you have to click the "extract window" button in the
editor menu (this only works if you had something selected (see the
active window string in the editor menu). The files are saved in your
home directory (depends on your OS, see the [FAQ](FAQ "wikilink")) under
*window_NAME_extracted.ufo*. The changes are **not** directly written
back to the scripts as some information might be missing in those
generated scripts. The opportunity is that you can perfectly align all
nodes with the editor.

[Category:Contribute](Category:Contribute "wikilink")
[Category:UFO-Scripts](Category:UFO-Scripts "wikilink")
[Category:GUIs](Category:GUIs "wikilink")