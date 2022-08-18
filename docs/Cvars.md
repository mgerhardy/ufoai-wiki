## General

Cvars are available for dynamic configuration of the engine. You can
always get a list of *cvars* by typing

    cvarlist

to the [console](console "wikilink"). See
[commands](commands "wikilink") for more information.

We also have tab completion for the [console](console "wikilink"). Just
type the first letter(s) and hit .

## List

See also [Cvars/Multiplayer](Cvars/Multiplayer "wikilink").

Values in square brackets ('\[' and '\]') contain the possible possible
values for each cvar. Do not leave them in.

\[1\|0\]


Install or uninstall the mousegrab.

\[1\|0\]


Fullscreen- or windowed-mode.

\[glx\|sdl\|gl\]


OpenGL refresh - `glx` and `sdl` are \*nix only - `gl` is Windows only

\[1\|0\]


Start the sound engine or not.

\[1\|0\]


Activates or deactivates the developer mode.

\[2\|1\|0\]


Activates or deactivates the console log (written to ).
The value 1 will start a new log every time to game starts up, value 2
will append to current logfile

\[language\]


Will change/set the language (see for valid languages; see also
[Manual/Language](Manual/Language "wikilink")).

\[1\|0\]


Used to create or place new [missions](adding_mission "wikilink") on
geoscape - will show the clicked coordinates.

\[1\|0\]


Use the cvar r_showbox to draw the bounding box of a model.

\[1\|0\]


Displays the *Frames per second* on the screen when enabled.

\[3\|2\|1\|0\]


Enable/disable graphic glsl shaders (default is 1). You need to set this
to 0 if game crashes on start with video errors (like on Intel G965
cards). 0 - disabled, 1 - low, 2 - medium, 3- high.

\[4.20\|4.10\|4.00\|3.30\|1.50\|1.40\|1.30\|1.20\|1.10\]


Change GLSL specification to compile shaders to. On changing this cvar
the shaders will recompile; you will see the compile log printed in the
console (including any warnings+errors). Default is 1.10, and is the
only specification currently supported by UFO:AI. Higher versioned
specifications may not compile. If the shaders had any compile errors
they will be disabled.

## Links

- [Console commands](commands "wikilink")

[Category:UFO-Scripts](Category:UFO-Scripts "wikilink")