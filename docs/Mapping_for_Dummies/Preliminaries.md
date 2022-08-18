The complete newbie's guide is actually working within
[UFORadiant](Mapping "wikilink"), specifically in context with building
maps for UFO: AI. It is intended to get you started building your first
map, then modifying it. Like a 'Hello World' project, you won't
necessarily do much else with it other then learn.

You want to get your hands on a copy of
[UFORadiant](Mapping "wikilink"), available .

## Prepping the Software

When you load UFORadiant it will ask you for the engine path. This is
the path to the file which should be in the base folder where you
installed the game. If you've bypassed this without setting the path,
you can set it in the editor by going to and selecting the Paths option
under Settings.

## Understanding the File Structure

It's good to know how the files in UFOAI are stored and how you will be
working with them. Where you installed the game you will see a folder
called and inside that folder you will see a number of
[pk3](pk3 "wikilink") files. These are compressed files which contain
most of the content of the game: maps, textures, artwork, script
definitions, sounds, etc.

You should extract the file to the same directory (you can use if your
usual extracting program doesn't work). It should create subfolder and
in it you will find a number of files as well as several files.

For now, let's open . In one of the four panels you should see a a 3D
view. If you right-click in that window and move your mouse around, you
can move your view. While moving your mouse around hold the CTRL key.
This will allow you to fly around the map. Go ahead and give it a nice
look. When you're done, right-click again to "release" the camera and
return to using the program normally.

Close the map for now. Let's cover just a few more things you'll need to
know about the file structure. There are also the following
[pk3](pk3 "wikilink") files in your folder and extracting each one will
give you more folders in your folder. Here are a few of the more
important ones for mapping:

- (becomes )


This is where the textures are stored. In order to use existing textures
in your maps, you don't need to unpack this. UFORadiant will read them
in the [pk3](pk3 "wikilink") files. But if you want to create your own
textures, it can be useful to unpack this folder so that you can see the
file structure of how they're stored. See [Artwork](Artwork "wikilink")
to get more information about supported format, resolutions, normalmaps
and so on.

- (becomes )


This is where the [material files](Mapping/Materialsystem "wikilink")
will be stored for your map. The material files help you specify
bumpmapping, specularity and more. But we can deal with all that later.

- (becomes )


This is where you can add your own [map
definition](UFO-Scripts/maps.ufo "wikilink") in order to see your map in
the Skirmish or Multiplayer menus. We'll deal with that later as well.

- (becomes )


This is where the ambient sounds are stored. See
[misc_sound](Mapping/Entities/misc_sound "wikilink") for more
information on how to add ambient sounds to your map.

[Category:Mapping](Category:Mapping "wikilink")
[Category:Contribute](Category:Contribute "wikilink")