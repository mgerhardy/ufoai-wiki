## Introduction

Artwork is used all over the game and you should look into contributing
where your skills or interest take you. Here are a few places where
artwork is needed:

- The [GUI](GUI "wikilink") can always use more polished background
  images, buttons, and more. Check out the [proposed
  UI](Proposals/UI_(2008) "wikilink") as well as GUI discussions in the
  forums for more details.
- We use artwork for all of the research articles. See the
  [TODO/General](TODO/General "wikilink").
- We always need more faces for our soldiers and skins for their
  uniforms. See
  [TODO/General#Skins.2FTextures](TODO/General#Skins.2FTextures "wikilink")
- Our [mappers](Mapping "wikilink") need more textures to create unique
  environments. Textures are more likely to be used if done in
  collaboration with a mapper, since there is a close tie between the
  geometry and the texture. Easier areas to contribute textures are
  animated billboards and signs, and screens in the UFOs.
- Our [modellers](Modelling "wikilink") needs skins for their models,
  everything from cars to aliens to soldiers.

Please make sure that you also submit the sourcefiles of your images
(like Photoshop's or xcf source files).

## Technical Details

### Normalmaps

<img src="Normalmap.png" title="Normalmap.png" width="200"
alt="Normalmap.png" />
<img src="Normalmap_settings.png" title="Normalmap_settings.png"
width="300" alt="Normalmap_settings.png" /> Settings for the [normalmap
plugin](http://nifelheim.dyndns.org/~cocidius/normalmap/) in Gimp. They
must have the same name as your texture but a **_nm** attached.

As you can see in the screenshot the darker the areas of the heightmap,
the more it will stick out (with relief or parallax mapping). So areas
you want to go in should be very bright, areas that should come out
should be darker.

- [xNormal](http://www.xnormal.net/Downloads.aspx)
- [Normal maps](http://wiki.polycount.net/Normal_Map)
- [Normalmap
  Tutorial](http://www.katsbits.com/htm/tutorials/creating_bumpmaps_from_images.htm#template)
- [Blender Normalmap
  Tutorial](http://katsbits.com/htm/tutorials/blender-baking-normal-maps-from-models.htm)
- [3DSMax Normalmap
  Tutorial](http://forums.mapcore.net/viewtopic.php?f=58&t=6806)
- [Normalmap
  Tutorial](http://cgtextures.com/content.php?action=tutorial&name=normalmap)
- [Normal Map Creation in The
  Gimp](http://developer.valvesoftware.com/wiki/Normal_Map_Creation_in_The_GIMP)
- [Relief map tutorial for
  Gimp](http://www.torquepowered.com/community/resources/view/10156/1)

Our normalmaps have the height encoded in their alphachannel. This is
needed for parallax mapping to work with UFO:AI.

- RGB = XYZ (surface normal perturbation for dot3 bump)
- A = height for parallax (offset) mapping.

Note that this type of normalmap describes surface normal vectors in
tangent space, not object space. What this means is that the vectors in
the normalmap are vectors relative to the surface-normal of the model.
To transform a "color" from the normalmap into a vector, we first scale
to the range 0.0 to 1.0 (by dividing by 255 for most standard image
formats). Then, we subtract 0.5 and multiply the result by two. This
gives a value in the range -1.0 to 1.0, which is interpreted as the
value of the normal vector for the appropriate axis. The Red channel
maps to the X axis, the Green channel maps to the Y axis, and the Blue
channel maps to the Z axis.

Thus, if your normalmap has a color of (127, 127, 255), it will be
interpreted as the vector (0.0, 0.0, 1.0). Since this is relative to the
object surface normal, the visual output will not be changed, since the
object-space surface normal will not be altered.

The reason all of this is important is that the surface normals
associated with a model will affect how your normalmap looks in-game.
The major issue to be aware of is normal-smoothing. By default, most
models will be "smoothed," which means that the surface normals will
vary smoothly across the surface, producing the visual impression of
smooth curves. If normals are not smoothed, surfaces will appear planar
because all the surface normals for a given polygon will point in the
same direction. How much smoothing is done can be controlled by the
"smoothness" parameter which is passed to \`ufomodel\`; currently, some
reasonable defaults have been built into the \`make models\` command.
The other issue is the issue of texture wrapping; any discontinuities in
the texture-coordinate mapping will not be smoothed. Therefore, if you
want smooth edges, you either need to ensure that the texture-mapping is
continuous at the edge in question, or modify the normalmap texture to
compensate for the discontinuity.

If the "bumpmapping" graphics options is disabled, the effects of
normalmap textures will not be visible in game.

### Glow maps

Glowmaps are supported for mesh model skins and for normal brushes. They
can be controlled via parameters in the material system. They must have
the same name as your texture but a **_gm** attached. Glowmaps should
be RGB color images; no alpha channel is required. An all-black glowmap
is equivalent to not having a glow-map at all. Colors from the glow-map
will be rendered as emissive sources and have a glow/bloom style
postprocessing effect applied to them. If the "postprocessing" graphics
option is disabled, they will not be visible in game.

### Specularity maps

Specularity maps allow you to specify how much light an object reflects,
and what color it should be. They must have the same name as your
texture, but with a **_sm** at the end. Assuming that GLSL rendering is
enabled, the specularity map will be used for specular light reflection
in the same way that a standard texture is used for diffuse light
reflection. The alpha channel of a specularity map specifies how tightly
focused the reflection is, and the RGB channels specify the color (and,
implicitly, intensity) of the reflection. A white or gray color will
result in a reflection the color of the incoming light, which is the way
that most physical objects behave. Some objects, such as metals, have
specular reflections that are colored by the object; for these objects,
you will want to have an appropriate color.

- Note: since textures get wrapped around an entire model, if the whole
  model should have the same specular properties, a 1 pixel texture will
  do the job just as well as a high-res texture. Use the smallest
  textures that will work to save memory.

### Roughness maps

By default, all specularity is calculated using the Phong reflection
model. If a roughness map exists, the GLSL renderer will use the
Cook-Torrence reflection model instead. The Cook-Torrence model allows
for a wider range of visual effects than the Phong model, but it
requires a texture that describes the properties of the surface in order
to do so. This is a roughness map. Roughness maps should have the same
name as your texture, but with a **_rm** at the end.

<File:Roughness1.jpg>\| <File:Roughness2.jpg>\| <File:Roughness3.jpg>\|
<File:Roughness4.jpg>\|

There are three parameters that are described by a roughness map. Given
an RGB image, the R channel describes how rough the surface is at a
microscopic level. The G channel describes the index of refraction of
the material. The B channel describes how much light is reflected if the
viewer and the light source are both aligned with the surface normal.
The equations which are applied to these values are fairly complex, and
are described in the link below. In general, roughness controls how
tight the reflected spot is, and the index of refraction controls what
angles light gets reflected at.

Cook-Torrance shading is more computationally expensive than Phong
shading, so it should not be used everywhere, but only where it will
have a visual impact. Phong shading is very good for rendering plastics,
and similar smooth reflective surfaces. For objects which have little or
no specular reflection, the choice of shading model will make little
difference. Where Cook-Torrance shading is really useful is for
depicting things which are glossy but not completely smooth. For
example, Cook-Torrance shading allows realistic rendering of wet cloth
or skin, semi-gloss paints, short fur (eg. cows, horses), and metals (in
particular, metals with non-smooth finishes, such as brushed aluminum).
Some examples of a few possible settings are shown at right on the
Firebird Dropship. Note that the dropship model does not have a
normalmap; the use of a normalmap in conjunction with Cook-Torrance
specularity allows for even more fine-grained control of reflective
properties.

Roughness maps can be used in conjunction with Specularity maps for
complete control of how specular reflections will appear. If both a
Roughness map and a Specularity map are present, the alpha channel of
the Specularity map will be ignored in favor of the more detailed
specification of reflectivity in the roughness map.

- Note: since textures get wrapped around an entire model, if the whole
  model should have the same specular properties, a 1 pixel texture will
  do the job just as well as a high-res texture. Use the smallest
  textures that will work to save memory.

For more details of Cook-Torrance shading, along with example images
that show what different parameter values look like, see:

- [The Cook-Torrance Shading
  Model](http://wiki.gamedev.net/index.php/D3DBook:%28Lighting%29_Cook-Torrance)

### Texture naming

Beware of long texture names - texture relative path from , excluding
the extension, can't exceed 32 characters. Do not name your textures
with filenames longer than that, they can't be used.

For example :

is bad. is 33 characters.

Such a texture should be renamed to something like

where is 32 characters.

### File formats

UFO:AI supports several image formats for textures, skins and menu
images:

- jpg
- png
- tga

They should be saved in RGB resp. RGBA.

Alphachannels should only be included if they are needed in that
particular texture (and they should always be included in the normalmaps
and specularity maps - see above)

### Dimensions

Power of two dimensions are the best for textures as every other
none-pot dimension might have to be rescaled for graphic cards that
don't support none-pot textures. And the rescaling will result in
quality loss of course.

## Videos (Cutscenes)

We have animation support in form of roq and ogm (ogm would be the
prefered file format) files in UFO:AI. You can play them with the
command. You can also show videos in the ufopedia - the
[menu](UFO-Scripts/menu_*.ufo "wikilink") node is MN_CINEMATIC:

    cinematic {
        video "filename"
    }

The filename is relative to

There are tools to create roq files:

-

- ffmpeg (svn version)

<!-- -->

    ./ffmpeg -threads 2 -i moon12.xvid.avi -s 1024x512 -minrate 3000000 -maxrate 6000000 -g 1000 -ar 22050 out.roq

- [Official ID roq
  encoder](ftp://ftp.idsoftware.com/idstuff/quake3/tools/roq.zip)

-

- (Open-Source, from sourceforge, supports rendering RoQ files)

We also have a [Cinema4D](Modelling/Cinema4D "wikilink") sequence in .
Please also note, that the Switchblade or ffmpeg encoder produces way
better looking videos with higher quality.

According to Riot's page, where switchblade can be downloaded, versions
of ffmpeg that encode RoQ videos are based primarily off of a port of
version 3 of switchblade. At present there is now a version 4 of
switchblade that fixes bugs present in version 3 and also encodes videos
of higher quality.

*Please be aware* that because of limitations of the game engine and
encoding of RoQ files that there are restrictions not only on output
format (frame rate, dimensions, audio frequency, etc.) but also on the
input format that the video has to be in *before* it is processed into a
RoQ video. More details about this can be found in the [Guide for making
ROQ videos with Switchblade v4.](SBTut "wikilink")

## Tutorials

- [Seamless textures with
  Gimp](http://www.coniserver.net/wiki/index.php/Seamless_Texture_Tutorial)
- [Hard Surface Texture
  Painting](http://forums.cgsociety.org/showthread.php?t=373024)

## Gimp Plugins

- [Low Frequency Even](http://registry.gimp.org/node/24636)


This plugin removes low frequency brightness and color differences from
image.

## Links

- -

-

- Free high quality texture generator

-

-

-

-

-

-

- \- Public domain images for textures

-

- generate normal / ambient occlusion / displacement maps

- over 2000 tutorials

- Tutorials and more

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

[Category:Contribute](Category:Contribute "wikilink")
[Category:Artwork](Category:Artwork "wikilink")