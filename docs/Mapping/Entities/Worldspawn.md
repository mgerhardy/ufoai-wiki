## Setting worldspawn

You have to set several worldspawn flags to be able to use the map for
UFO:AI and you can override some default settings for the lighting in
the worldspawn, too.

To set these flags, open your map, go to the Entities sidepanel and
search for the worldspawn entity. Select it and look in the bottom panel
of the sidepanel. Click on an existing key's value to edit the value, or
click on the **New** button to add a new key.

See below for valid keys. You can override the map compiler default
values.

For [random maps](Mapping/Random_map_assembly "wikilink") you can put
the worldspawn flags into the ump file.

## Keys

Any values with _day and _night refer to their respective time of day,
and both should be used.

- **color_day**, **color_night**


Color for the sunlight or moonlight in [RGB](RGB "wikilink"). This value
must be set or the light is ignored.

Example (day):

- **light_day**, **light_night**


Intensity of the light: a value between 1 and 255

Example (day):

- **angles_day**, **angles_night**


Angle of the sunlight or moonlight. The first value is the pitch
(up/down), the second is the yaw (x-y direction in 360 degrees)

Example:

- **ambient_day**, **ambient_night**


Color for the ambient light in [RGB](RGB "wikilink") (ie - how dark it
should be where no light reaches). A small amount of ambient light is
recommended for all maps.

Example (day):

- **maxlevel**


The highest selectable level (int). Range is 1-8.

- **maxteams**


The max. teams for multiplayer. Range is 1-4.

- **nextmap**


The map that should be started after this one was finished

- **norandomspawn**


Do not use random spawn positions for actors to spawn them. If this flag
is specified, actors of all teams are spawned in the order the
spawnpoints were originally created.

- **subdivide**


Controls maximum surface size for the bsp stage of the compile.
Generally, the default value 1024 is recommended. Lower values may
reduce artifacts, while higher values may reduce r_speeds.

- **brightness**


Controls light intensity. This is used to uniformly brighten or darken
your level. 1.0 is default, all positive floating point values are
valid.

- **saturation**


Controls light saturation, or color influence. This can be used to make
a level look more colorful, or more pale. The default value is 1.0.
Values from 0.5 to 3.0 are most useful.

- **contrast**


Controls light contrast. This can be used to create darker dark areas
and lighter light areas. The default value is 1.0. Values significantly
higher than 1.0 are not recommended.

- **quant**


Controls lightmap resolution, which is relative to texture size. Default
is 4 (1 \<\< 4). A value of 3 will produce sharper lightmaps, but will
dramatically lengthen your radiosity compile times. In fact, setting
this to 5 during development is a nice trick for speeding up your level
design process.

## Links

- [Mapping](Mapping "wikilink")
- [Entities](Mapping/Entities "wikilink")

[Category:Contribute](Category:Contribute "wikilink")
[Category:Mapping](Category:Mapping "wikilink")
[Category:Entity](Category:Entity "wikilink")