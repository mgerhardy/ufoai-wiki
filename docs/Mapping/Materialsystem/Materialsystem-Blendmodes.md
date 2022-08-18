## Rendering

UFO:AI uses the OpenGL API to render graphics to the screen. Each frame
is stored in what is called a frame buffer. Each polygon in view is
rendered to the frame buffer one at a time, stage by stage, pixel by
pixel.

## Layers

OpenGL blend modes explain to the renderer how two graphic layers, a
source and destination layer, are to be mixed together.

The source layer is usually the RGB color data in a texture image file.
This texture is gathered from the material shader applied to the current
polygon. The actual image used in the source layer is generally defined
through use of the map keyword.

The destination layer is the color data currently existing in the frame
buffer.

## The Blend Function

Each layer is essentially broken down into pixels and each pixel in the
source layer is combined with the corresponding pixel in the destination
layer using a mathmatical formula. This formula is the blend function.

The formula reads as follows:

`[source * (srcBlend)] + [destination * (dstBlend)]`

The blend keyword defines both the source blend and destination blend
through the use of aliases however you are not limited to using aliases.

Both the source blend and destination blend can be defined separately
like so...

`blend [srcBlend] [dstBlend]`

## Source Blend

The following values are valid for the source blend part of the
equation.

| blend mode             | value            | description                                                                                                                                                                                                                                                    |
|------------------------|------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| GL_ONE                 | 1                | This is the value 1. When multiplied by the source, the value stays the same. The value of the color information does not change.                                                                                                                              |
| GL_ZERO                | 0                | This is the value 0. When multiplied by the source, all RGB data in the source becomes zero (essentially black).                                                                                                                                               |
| GL_DST_COLOR           | destination      | This is the value of color data currently in the destination (frame buffer). The value of that information depends on the information supplied by previous stages.                                                                                             |
| GL_ONE_MINUS_DST_COLOR | 1 - destination  | This is nearly the same as GL_DST_COLOR except that the value for each component color is inverted by subtracting it from one. (i.e. R = 1.0 - DST.R, G = 1.0 - DST.G, B = 1.0 - DST.B, etc.)                                                                  |
| GL_SRC_ALPHA           | source alpha     | The TGA file being used for the source data must have an alpha channel in addition to its RGB channels (for a total of four channels). The alpha channel is an 8-bit black and white only channel. An entirely white alpha channel will not darken the source. |
| GL_ONE_MINUS_SRC_ALPHA | 1 - source alpha | This is the same as GL_SRC_ALPHA except that the value in the alpha channel is inverted by subtracting it from one. (i.e. A=1.0 - SRC.A)                                                                                                                       |

## Destination Blend

The following values are valid for the destination blend part of the
equation.

| blend mode             | value            | description                                                                                                                                                                                                                                                     |
|------------------------|------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| GL_ONE                 | 1                | This is the value 1. When multiplied by the destination, the value stays the same the value of the color information does not change.                                                                                                                           |
| GL_ZERO                | 0                | This is the value 0. When multiplied by the destination, all RGB data in the destination becomes zero (essentially black).                                                                                                                                      |
| GL_SRC_COLOR           | destination      | This is the value of color data currently in the source (which is the texture being manipulated here).                                                                                                                                                          |
| GL_ONE_MINUS_SRC_COLOR | 1 - destination  | This is the value of color data currently in source, but subtracted from one (i.e. inverted).                                                                                                                                                                   |
| GL_SRC_ALPHA           | source alpha     | The TGA file being used for the source data must have an alpha channel in addition to its RGB channels (four a total of four channels). The alpha channel is an 8-bit black and white only channel. An entirely white alpha channel will not darken the source. |
| GL_ONE_MINUS_SRC_ALPHA | 1 - source alpha | This is the same as GL_SRC_ALPHA except that the value in the alpha channel is inverted by subtracting it from one. (i.e. A=1.0 - SRC.A).                                                                                                                       |

## Computing a Result

Rather than think of the entire texture as a whole and how the blend
function computes a result, it maybe easier to think of the red, green,
blue, and alpha values that correspond to a single pixel in the source
and destination layers, because that is essentially what the computer is
processing... one pixel of each layer at a time.

So, let's say the blend mode is add. That's ...

`blend GL_ONE GL_ONE`

And these blends are plugged into the blend function like so...

`[source * (GL_ONE)] + [destination * (GL_ONE)]`

Because GL_ONE equals 1 the formula can be simplified like so...

`[source * 1] + [destination * 1]`

Now, let's say that two coorisponding pixels from the source and
destination layers are being plugged into the function where the source
pixel is white and the destination pixel is black.

Each pixel contains a red, green, blue, and alpha channel. Each channel
is computed as a separate value.

`[1, 1, 1, 0 * 1)] + [0, 0, 0, 0, * 1]`

This then becomes...

`[1, 1, 1, 0] + [0, 0, 0, 0]`

Which then equates to ...

`[1, 1, 1, 0]`

And that means the result is a white pixel.

## Supported Blendmodes

- GL_ONE
- GL_ZERO
- GL_SRC_ALPHA
- GL_ONE_MINUS_SRC_ALPHA
- GL_SRC_COLOR
- GL_DST_COLOR
- GL_ONE_MINUS_SRC_COLOR
- GL_ONE_MINUS_DEST_COLOR

## Examples

`{`
`  material tex_nature/grass001`
`  {`
`    texture tex_nature/dirt001`
`    blend GL_DST_COLOR GL_ZERO`
`    lightmap`
`  }`
`}`

This example would render a mask (dirt001) onto the source texture
(grass001)

[Category:Contribute](Category:Contribute "wikilink")
[Category:Mapping](Category:Mapping "wikilink")