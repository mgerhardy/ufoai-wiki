## General

This documentation is based on from quake2world.

Since version [2.3](Changelog/2.3 "wikilink") we have a material system.
You can easily and flexible enhance your maps with it. The map loader
searches them in  - they have to have the same basename as the map -
just not as extension, but . In case of random map assemblies, use the
same name as the (you cannot set material properties per tile, only per
whole map).

You can think about materials as a set of properties for individual
world textures. You can create animations, terrain blending, scrolling,
zooming and environment reflections with them. Each material is defined
on one texture (the *material texture*). All the textures on the map
will then have the properties of that material. The material can have
one or multiple properties. Sometimes a property references another
texture (the *property texture*). Note that all properties apply at the
same time, not in succession!

You do not need to compile the source again if you just want to change
the material file. To test your material configuration simply start the
corresponding map and see if your material definition works the way you
imagined it. If not, edit it, save it and restart the game to see your
changes.

Here are some properties with their explanations.

### Scrolling Texture

`# scrolling texture`
`{`
`   material tex_pics/tonight_honuda`
`   {`
`       texture tex_pics/tonight_honuda`
`       scroll.s 0.25`
`   }`
`}`

This one will scroll the texture horizontally - the **scroll.s**
parameter is the speed. Note that the texture displayed is the texture
in the property, not the texture the property is defined for! You can
use this to make the same texture scroll at different speeds on the same
map by using a placeholder texture. The orientation the texture scrolls
into depends on the texture rotation you set in radiant.

### Terrain with two stages

`# terrain with two stages`
`{`
`   material tex_nature/desert006`
`   {`
`       texture tex_nature/desert001`
`       terrain 0 64`
`       lightmap`
`   }`
`   {`
`       texture tex_nature/desert002`
`       terrain 128 192`
`       lightmap`
`   }`
`}`

This property makes a gradient with multiple textures. The **terrain**
parameter determines at which heights the texture given in the property
will be displayed. The texture will blend with the material texture. In
this example, the material texture makes a gradient with two property
textures.

The **lightmap** parameter indicates that the property textures should
use the map's lightmap. If this parameter is absent, the property
textures will no be blended against the brush's lightmap.

### Metal surface with reflections

`# a metal surface with reflections`
`{`
`   material tex_material/metal`
`   {`
`       envmap 0`
`   }`
`}`

This is a metal surface with reflections using the built-in envmap
(valid built-in envmaps are **envmap 0** and **envmap 1**) - you can
also define another texture as envmap.

- What's the difference between envmap 0 and 1?

### Pulsating surface

`# a pulsating surface`
`{`
`   material tex_misc/pulse`
`   {`
`       texture tex_misc/pulse_blend`
`       pulse 2`
`   }`
`}`

The **pulse** parameter makes the material texture alternate with the
property texture. If no property texture is specified, the material
texture alternates with itself. Again, the **lightmap** parameter
governs whether or not to light the property textures with the map's
lightmap.

### General surface parameter

`# A general surface parameter`
`{`
`   material tex_misc/pulse`
`   bump 1.5`
`   {`
`       texture tex_misc/pulse_blend`
`       pulse 2`
`   }`
`}`

This example shows that materials can also have general surface
parameters. These parameters are not defined in a property.

You can find more examples at .

## Reference

### General surface parameters

Many of the general surface parameters can also be controlled through
textures. For more information on setting up normalmaps, glowmaps,
specularity maps and roughness maps, see the
[Artwork](Artwork "wikilink") section.

bump b: Bump amplification is used to tune bump mapping effects. Higher values increase the "bumpiness" of surfaces. The b parameter is required, and must be a positive floating point value, or 0.0. The default value is 1.0.
parallax p: Parallax amplification is used to tune the depth of bump mapped surfaces. Using values higher than 1.0 requires high-quality normalmaps, with properly encoded height values. The p parameter is required, and must be a positive floating point value, or 0.0. The default value is 1.0.
hardness h: Hardness is a multiplier for the specular component of bump mapped surfaces, and can be used to amplify or mute a material's reflectiveness. Organic materials benefit from lower values, while polished metals and glass benefit from higher ones. The h parameter is required, and must be a positive floating point value, or 0.0. The default value is 1.0.
specular s: Specular amplification is used to tune the specularity of bump mapped surfaces. The s parameter is required, and must be a positive floating point value, or 0.0. The default value is 1.0.
glowscale g: Glowscale is used to modify the intensity of the glow-map (if present). The g parameter is required, and must be a floating point value greater than or equal to zero. The default value is 1.0. Glowmaps are associated with texture images; for an image named <name>.<ext>, if an image named <name>_gm.<ext> exists, it will be treated as a glow map. If post-processing is enabled in the graphics options menu, glow-maps will provide emissive lighting with real-time bloom effects. Glowscale may be specified for a material, for a specific stage, or both. When drawing a particular stage, the stage-specific glowscale and the material-wide glowscale will be multiplied together. Since both values default to 1.0, it is generally sufficient to specify one of them.
normalmap texture: You can override the default normalmap by specifying a texturename here
glowmap texture: You can override the default glowmap by specifying a texturename here

### Parameters for property textures

These parameters affect property textures only.

anim frames hz: Frame-based animations are used to animate surfaces like computer screens. The stage texture name should end in 0, e.g. , with subsequent frames following in sequence. The frames parameter specifies the number of textures which comprise the animation. The hz parameter specifies the frequency of the effect. Both are required, and must be a positive integer and positive floating point number respectively. The maximum number of frames is 16.
anima frames hz: The same as **anim** but alternates the frames. For instance, if you had frames \*0 to \*2, it would go \*0,\*1,\*2,\*1,\*0,1,\*2,\*1. The number of frames should be uneven for this to work properly. Otherwise the mid frame (resp. the last frame) will be shown twice.
animb frames hz: The same as **anim** but plays backwards.
animr frames hz: The same as **anim** but this time a random frame of the animation is chosen & displayed using the given speed. Attention: This will not create a completely fluid animation, as there is no check built in to prevent the same frame being chosen two or more times in a row. So this command is perfect for 'slow' animations where then some of the frames are simply shown longer & so this effect also 'randomizes' the length of the intervall between frame changes to some degree (makes random frames stay 2 or more times longer visible than other frames of the animation).
animf frames hz: The same as **anim** but this time a random frame of the animation is chosen & displayed using the given speed. A check is performed to prevent the display of the same frame twice in a row. This check will guarantee a fluid motion. Please make sure your animation has at least 3 frames to prevent unnecessary calculation loops.
blend src dest: The blend directive exposes OpenGL's GL_BLEND function. This is used for textures which lack an alpha channel, where additive blending is typically required. The src and dest parameters are GL constants, e.g. blend GL_ONE GL_SRC_ALPHA. The default blend function is GL_ONE GL_ONE_MINUS_SRC_ALPHA. See [Blendmodes](Mapping/Materialsystem/Materialsystem-Blendmodes "wikilink") for examples.
color r g b: The color directive is used to influence the stage's default color. This directive is often used in conjunction with other directives such as pulse or stretch. The parameters r g b are each required, and must each be floating point numbers between 0.0 and 1.0.
glowmaplink: By adding this command to your animation the frames of your animation will start to glow. This is especially useful for animation frames where the glowmap would be the same image like the frame itself.
pulse hz: Pulses are used to animate surfaces like jump pads or light fixtures. The stage texture will fade in and out over the base material. The hz parameter specifies the frequency of the effect. It is required and must be a positive floating point number (n.n) which specifies how many times the pulse will flash per second. The stage texture is interpolated over the base material using a sin function.
dutycycle hz: An additional parameter can be used to specify a delay between pulses. It can only appear in the line following a pulse parameter and must be a positive floating point number between 0.0 and 1.0. It defines a fraction of the pulse's frequency during which the animation is played.

![](dirtmap2.png "dirtmap2.png") ![](dirtmap_rma.png "dirtmap_rma.png")

rotate hz: Rotation directives are used for fan blades, Yin-Yangs, and other surfaces which should appear to rotate. The hz parameter specifies the speed of the rotation. It is required, and must be a positive floating point number.
scroll.s s, scroll.t t: The scroll directives are used to slide texture stages across the underlying base material. This is used for computer screen redraw lines, layered water surfaces, and trim lighting. S and T are the two texture coordinate axis. Each directive takes exactly one required parameter, which must be a floating point number.
stretch amp hz: Stretch directives are used to create continuous expanding and contracting effects. The amp parameter specifies the scale of the stretch, while hz specifies the frequency. Both are required, and must be positive floating point numbers.
terrain ceil floor: Terrain directives are used to achieve simple height-based terrain blending. The ceil and floor parameters specify the highest and lowest Z-axis coordinates where blending will occur. At Z coordinates less than floor, the base material texture will appear; at Z coordinates greater than ceil, the stage texture will appear. Linear interpolation is used to blend the two textures at Z coordinates between ceil and floor. Both parameters are required, and must be floating point numbers.
dirtmap factor: Defining this in a texture stage will result in blending in a dirtmap. To make this effect look good you have to keep some little things in mind. The alpha value for the dirtmap blending is calculated along the vertices. That means that touching brushes must have overlapping vertices to get the same alpha values (see the attached image). The parameter factor is a blending factor that globally influences the blending of the dirtmap for all vertices. Its default value is 1.0. Values lower than this will make the dirtmap less visible, values higher than this will make it more visible.

### Envmap parameters

Environment map stages are used to simulate reflections on metal, water,
glass, etc. For convenience, they may be declared with numeric values to
take advantage of several built-in effect textures, e.g. envmap 0.
Alternatively, a unique texture can also be provided, e.g. envmap
envmaps/my_envmap. Environment map stages do not currently support any
unique directives, but do support color scroll.s scroll.t, described
above.

`{`
`   material office/glass`
`   {`
`       envmap office/glass_envmap`
`       blend GL_SRC_ALPHA GL_ONE`
`       color 0.9 0.9 1.0`
`   }`
`}`

### Lightmap Stages

Lightmap stages are used to blend in statically computed lighting
information. This is typically applied as the last drawn stage. Lightmap
stages are declared by simply beginning the stage with the lightmap type
name. Lightmap stages do not support any unique directives.

`{`
`   material lunaran/computer0`
`   ...`
`   {`
`       anim 4 0.3`
`   }`
`   {`
`       lightmap`
`   }`
`}`

### Flare Stages

Flare stages are used to add flares (coronas) to surfaces such as light
fixtures. For convenience, flare stages may reference numeric values to
take advantage of several built-in effect textures, e.g. flare 1. At
present time you can use 10 different built-in flares (flare 0, ...,
flare 9). Alternatively, a unique texture can also be provided, e.g.
flare flares/my_flare.

Flare stages do not currently support any unique directives, but do
support color scale.s scale.t described above. If a color is not
provided to the stage definition, Quake2World automatically uses the
surface's average static lighting color to shade the flare. Either of
the scale.s or scale.t directives can be used to influence the size of
the flare produced by this stage.

`{`
`   material tech/small_light`
`   ...`
`   {`
`       flare tech/flare1`
`       scale.s 1.5`
`       color 0.5 1.0 1.0`
`   }`
`}`

### Tape Stages

The tape stage can blend textures in a defined area. The first parameter
is the center, the second the relative floor and the third the relative
ceiling.

Meaning that min is `center - floor` and max is `center + ceiling`.

`{`
`   material terrain/grass`
`   ...`
`   {`
`       texture terrain/whatever_blend`
`       tape 0.5 0.2 0.4`
`   }`
`}`

[Category:Mapping](Category:Mapping "wikilink")