## Introduction

In order to see a map in game it must be compiled. Compiling can be very
[time consuming](Mapping/Compile_time "wikilink"). If you don't want to
compile yourself, you can use the script to download the latest version
of the compiled maps. You need python 2.x to do so. Grab it from .
Windows users should right click the file and select 'Open with' and
choose the python binary (e.g. in ).

The rest of this page is designed for mappers who are compiling their
own maps, and for information on ufo2map's settings.

## Compiling your own map

To compile your own map it must be saved in the `/base/maps/` folder.
You should use `ufo2map.exe`, which is located in the folder where you
installed the game, alongside the game's executable (`ufo2map.exe`).
Running it is different for different platforms

### Windows

To run `ufo2map.exe`, go to the Start Menu. For Windows XP, click Run
and then type cmd. It should open a small black window with an old
dos-like prompt. Browse to your game's installation folder. If you game
is in `c:\Program Files\ufoai`, you would type
`cd "c:\Program Files\ufoai"` and hit enter.

Once you're in the directory, type `ufo2map maps/yourmap.map`.

Important:
To compile the map from inside the UFORadiant editor on windows, make
sure to have `gspawn-win32-helper.exe` and
`gspawn-win32-helper-console.exe` available on youre path, else you'll
get an error on the UFORadiant console telling you the command could not
be spawned. The best is to just have them alongside the `uforadiant.exe`
program.

Also, you might encounter the situation that `ufo2map.exe` and other
command line tools are running but not displaying any output. However
the output is send to files like `stdout.txt` and `stderr.txt`. This is
caused by a configuration issue in SDL. If this happens, running
`ufo2map.exe` from inside UFORadiant will not work properly. To resolve
this, add the following environment variable to you system:


    SDL_STDIO_REDIRECT=0

### Linux

Under Linux we use `ufo2map` - which is a binary including the bsping
and the radiosity part.

Just type `make maps` from . This will compile all maps in the first run
and subsequently all changed maps.

You can also compile just one specific map: Once you're in the master
directory, type `./ufo2map maps/yourmap.map`.

## Loading the map in game

To play the map in game, you will need to add the map to a .ufo file in
the `/base/ufos/` directory. You can either add the entry to your
existing `maps.ufo` file or make a new file for your map. If you're just
testing, making a new file can be easier to work with. The file should
look something like this for a test map, though you can look at other
maps in `maps.ufo` to see other options:

    mapdef yourmap
    {
        map         "yourmap"
        description "_Your map description"
        teams       2
        multiplayer false
        maxaliens   8
        aircraft
        {
        }

        ufos
        {
            //any
        }

        terrains
        {
            //any
        }

        cultures
        {
            //any
        }

        populations
        {
            //any
        }
    }

You can also get some more detailed information about the map definition
[here.](UFO-Scripts/maps.ufo "wikilink").
Once you have this file in the **/base/ufos/** folder, you can load your
map in Skirmish mode.

## Errors you may get

- **mixed face contents**


Example: Entity 0, Brush 12: mixed face contents

All brushsides should have the same content and surfaceflags set - but
there may be exceptions like nodraw faces

- **MAX_POINTS_ON_WINDING**


this happens if more than the allowed number of brushes touches one
brush - e.g. a long stair

- **MAX_MAP_LIGHTING**


this means that there are "too many lightmap pages". Concretely, this
may happen if there are too many surfaces in the map, or textures scaled
too small.

## Advanced Parameters for ufo2map

If you type **ufo2map --help**, you will get a long list of supported
parameters. Here are a few:

-extra:Extra light samples for better lighting
-quant NUMBER:The default is currently 4, but you can reduce this for much better lighting (cleaner lines). But this will dramatically increase compile times.
-nolighting:This will bypass the lighting stage if you just want a quick test. You can add **day** or **night** parameters behind it to bypass just that lighting stage.
-check:This will check the map file, but it will not make any changes. Instead, it will print out a list of found problems. It will report about mixed levelflags, z-fighting and more.
-fix:This will check the map file and try to fix a number of problems. So it fixes surfaces that ought to be nodraw and more.

Another article related to the advanced parameters of ufo2map can be
found in the [Mapping for Dummies: Lesson
3](Mapping_for_Dummies/Lesson3#Using_advanced_parameters_of_ufo2map "wikilink").

## Batch File

There is a batch file with some useful options, e.g. you can compile all
the maps in one directory (when dealing with a random map assembly).
Look for **contrib/scripts/compile_maps.bat** and run

    compile_maps.bat /help

for information.

## Statistics

- [Compile time](Mapping/Compile_time "wikilink")

[Category:Contribute](Category:Contribute "wikilink")
[Category:Mapping](Category:Mapping "wikilink")