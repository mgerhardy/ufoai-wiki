## General

You key bindings are stored in a file names . This file can be modified
in your home directory. (See the [FAQ](FAQ "wikilink") where you have to
look for the file)

## Show current bindings

Go to the [console](console "wikilink").

`]bindlist`

This gives you a list of the current keymap.

`]cmdlist`

This will give you a list of [commands](commands "wikilink") you can
bind to your keys.

## Example

This example swaps the and , so you can turn with the .

`]unbind MOUSE2`
`]unbind MOUSE3`
`]bind MOUSE2 "+turn"`
`]bind MOUSE3 "+action"`

To not have to do this for each change every time you play the game you
can create your own config file that you execute when in the game to
enable all your changes. Copy/paste the below into a normal textfile and
change to your preferences.

## Keynames

- TAB
- ENTER
- ESCAPE
- SPACE
- BACKSPACE
- UPARROW
- DOWNARROW
- LEFTARROW
- RIGHTARROW
- ALT
- CTRL
- SHIFT
- F1
- F2
- F3
- F4
- F5
- F6
- F7
- F8
- F9
- F10
- F11
- F12
- INS
- DEL
- PGDN
- PGUP
- HOME
- END
- MOUSE1
- MOUSE2
- MOUSE3
- MOUSE4
- MOUSE5
- AUX1
- AUX2
- AUX3
- AUX4
- AUX5
- AUX6
- AUX7
- AUX8
- AUX9
- AUX10
- AUX11
- AUX12
- AUX13
- AUX14
- AUX15
- AUX16
- APPS
- KP_HOME
- KP_UPARROW
- KP_PGUP
- KP_LEFTARROW
- KP_5
- KP_RIGHTARROW
- KP_END
- KP_DOWNARROW
- KP_PGDN
- KP_ENTER
- KP_INS
- KP_DEL
- KP_SLASH
- KP_MINUS
- KP_PLUS
- MWHEELUP
- MWHEELDOWN
- JOY1
- JOY2
- JOY3
- JOY4
- JOY5
- JOY6
- JOY7
- JOY8
- JOY9
- JOY10
- JOY11
- JOY12
- JOY13
- JOY14
- JOY15
- JOY16
- JOY17
- JOY18
- JOY19
- JOY20
- JOY21
- JOY22
- JOY23
- JOY24
- JOY25
- JOY26
- JOY27
- JOY28
- JOY29
- JOY30
- JOY31
- JOY32
- PAUSE
- SEMICOLON
- SUPER
- COMPOSE
- MODE
- HELP
- PRINT
- SYSREQ
- SCROLLOCK
- BREAK
- MENU
- POWER
- EURO
- UNDO

Every other key is available by it's character