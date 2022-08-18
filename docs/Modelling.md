## Introduction

3D models are used for many things in UFOAI: the soldiers, aliens and
their weapons and equipment; some items on maps (trees, cars, furniture,
small UFOs); and some of the icons on the geoscape.

This document will introduce you to modelling for UFOAI, but the docs
are still sparse on how to get your content into the game. Feel free to
share your work in the forums and ask for help getting it evaluated and
implemented.

We use the MD2 format, but there are [many different
programs](Modelling#Programs "wikilink") you can use to create these.

You can see a list of models that are still needed in the
[TODO/General#Models](TODO/General#Models "wikilink"). We can also use
appropriate additions to the available soldier models. In particular, we
need lots of new heads for our soldiers, and these can be an easy way to
get into modelling for UFOAI.

## Style

In this game we're doing fairly hard sci-fi that has to obey at least
some of the laws of physics. We want to see much more 2001: A Space
Odyssey and Space: Above & Beyond style than Star Trek or Star Wars.

### Dimensions

- a player is 56 units tall
- 8 units equals 1 foot
- therefore, player is 7 feet tall

## Creating new models

### Programs

There are many programs you can use to make models. Blender seems to be
used by some in the forums, so if you've never modeled you're likely to
be able to get help with that program in our forums. It has the added
benefit of being free.

- [AC3D](Modelling/AC3D "wikilink")
- [Blender](Modelling/Blender "wikilink")
- [3DSMax](Modelling/3DSMax "wikilink") /
  [Gmax](Modelling/Gmax "wikilink")
- [Maya](Modelling/Maya "wikilink")
- [Cinema4D](Modelling/Cinema4D "wikilink")
- [LightWave](Modelling/LightWave "wikilink")
- [CharacterFX](Modelling/CharacterFX "wikilink")
- [Wings3D](Modelling/Wings3D "wikilink")
- [XSI](Modelling/XSI "wikilink")
- [DeleD3DEditor](Modelling/DeleD3DEditor "wikilink")
- [MilkShape 3D](Modelling/MilkShape3D "wikilink")

### Needed models

See the **Models/Maps section** in the
[TODO/General](TODO/General "wikilink") page or any of the other
[TODO](TODO "wikilink") pages for upcoming versions for a list of needed
models.

## Modelformat

We use the normal Quake2 [md2](md2 "wikilink") format for our models.
See the [md2](md2 "wikilink") entry for a longer description of the
format and tools that you might find useful. We even support the
[obj](obj "wikilink") and [md3](md3 "wikilink") basic features.

For those who are familiar with the [md3](md3 "wikilink") format and the
tags used to identify geometry - we even support
[tags](Modelling/3DSMax#Export_tag_file "wikilink") for
[md2](md2 "wikilink").

The following numbers are rough guidelines for the various upper limits.
They are already a bit dated now and by no means fixed rules. You can
always ask a team member if your stuff will be ok.

### Level of Details

We have support for LOD models for [md2](md2 "wikilink") and
[md3](md3 "wikilink"). [md3](md3 "wikilink") has built in support for
several meshes and for [md2](md2 "wikilink") we support loading LOD
models from different files from the same directory. The
[md2](md2 "wikilink") filenames must be like this: Normal
[md2](md2 "wikilink") file name: model.md2 =\> resulting LOD model name
is model-lod01.md2, model-\>lod02.md2, model-lod03.md2. Thus we support
up to four different level of details. It's also possible to only
provide model-lod01.md2 and skip the others. For [md3](md3 "wikilink")
we are doing the same but with the built in meshes.

The LOD models are using the same textures that are already uploaded and
used from the main model. You also have to ensure that the frame count
matches between all provided LOD models.

In [3DSMax](Modelling/3DSMax "wikilink") you can use the **MultiRes**
modifier to generate different LOD stages for your model.

### Texture sizes

- [Weapons](Equipment/Weapons "wikilink")/cars/big trees 512x512px
- small plants/ammo: 256x256px
- creating higher resolution textures would be the best. The preferred
  size for all textures is 1024x1024. If we then need them smaller, we
  can scale them down, but still have the high resolution version for
  changes and stuff like that.

### Polygons

- cars: \~700tris
- big [weapons](Equipment/Weapons "wikilink"): 200-500tris
- ammo: \~100tris
- characters: \~1000tris for body and \~300tris for head
- it would also be cool if you could provide different level of details
  for a model (different files for each lod - filenames encoded like
  this: (high res), (lower res), ....)

### Sizes

- read about the [levelflags](Mapping/Levelflags "wikilink") UFO:AI
  uses, we should be able to hide some parts of a model if it is higher
  than one level in UFO:AI. This is why we have split some of the
  existing models into several smaller ones. This way we are able to set
  different [levelflags](Mapping/Levelflags "wikilink") for each
  modelpart in order to hide or display them as needed. For example
  streetlamps should be split into two parts. As an example see .

### Skins

- see [Modelling//Skins](Modelling/Skins "wikilink") article for more
  information

## Testing in game

After the model is exported, you can edit the file (see
[pk3](pk3 "wikilink")) and change the included examples to load your
model. Once you changed it you can open the game
[console](console "wikilink") and type .

## Characters

See [Character Animation](Modelling/Character_Animation "wikilink").

## Links

-

-

-

-

-

-

-

-

-

-

-

-

-

-

## Other programs

-

- that paint depths on to polygon models in real-time

-

- \~440 model formats are supported

- Mesh redrucer for 3ds files

- Open Source plant modeling package

-

## Patterns & Blueprints

-

-

-

[Category:Modelling](Category:Modelling "wikilink")
[Category:Contribute](Category:Contribute "wikilink")