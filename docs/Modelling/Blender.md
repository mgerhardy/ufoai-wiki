is a free open source 3D content creation suite, available for all major
operating systems under the GNU General Public License. You can download
it for free with no limitations.

## General

### MD2 Scripts

An import/export script for Blender 2.63+ is available at the
blender-tools in our [repository](Getting_the_source "wikilink"):

- -

Note: These seem to work fine on Blender 2.7x
(--[DarkRain](User:DarkRain "wikilink")
([talk](User_talk:DarkRain "wikilink")) 05:28, 12 December 2014 (CET))

### MD2-TAG Script

A Blender 2.63+ import/export script for
[tag](Modelling/Tags "wikilink") files as used by our
[MD2](MD2 "wikilink") models is available at the blender-tools in our
[repository](Getting_the_source "wikilink"):

- -

## Export MD2 from Blender

There are some things you need to consider when exporting a model to
[MD2](MD2 "wikilink") from blender:

In Blender to export the model you need to

- The model must be unwrapped.
  - Please also add at least one **image** texture (and create an
    (blender) image for it — even a dummy one with no actual image) to
    your model before exporting all md2 need at least one skin.
- If the center of your object (small violet circle) isn't located
  exactly in the absolute center (coord-grid center) you need to
  re-place it into the absolute center (unless you know what you are
  doing)
- Then you should be able to export it with the md2-export menu entry.

### Scaling

If you use one a scale where one blender unit equals one unit in the
battlescape you need to scale up the model x16 before export.

See the (1x1) and the (2x2) models for reference. They also include
blender-scaled reference boxes (1x1x2.45 blender units) that equals the
cursor in geoscape.

You should configure Blender to use a grid setting of 6.4 (or multiples
of this) - this will ensure, that the model will be aligned to the
[UFORadiant](Mapping "wikilink") grid settings.

### Create Animations

**TODO: WRITEME**

Rough basics: No matter how you animate the model. As long as you export
it as a [MD2](MD2 "wikilink") file you are limited by the specification
of the model-type. Mainly the so-called *key-framed* animations of the
[MD2](MD2 "wikilink") format are of interest to us. Basically the format
stores a list of vertices (with UV-data) and a list of animation frames.
Each frame can have other positions of the vertices.

If you create a bone-based (or shape-key) animation of your model,
export it to [MD2](MD2 "wikilink") and import that in
[Blender](Blender "wikilink") again you'll loose all original
information about bones and similar stuff .. they are transformed to
key-frames on export. There still are animations there, but they are not
as easily modified. This is also true for other modelling programs.

So **never ever loose your original file** if you don't want to
re-create a lot of animation-work.

Placement of weapons, floor, heads, etc. ... for [MD2](MD2 "wikilink")
files (which do not have this integrated into the format) is handled via
the [tag](tag "wikilink") files. Tags are implemented in Blender via
*Empty* objects which are animated along with the mesh, and are later
exported to tag files, the same limitations regarding MD2 animation are
applicable to tags, namely that they are also exported as *key-framed*
animations.

Note: Some already animated [MD2](MD2 "wikilink") files (nearly every
file created by [Herby](Herby "wikilink") of the original dev-team) do
**not** have existing source files ([max](max "wikilink") files) any
more ... it would be great if s/b would re-animate them in Blender so we
can modify them more easily.

## Create screenshots of models with UFOAI frame

To make creation of screenshots from 3d models with the green UFO:AI
background&frame easier (see the [Screenshots](Screenshots "wikilink")
section) a template for [Blender](Blender "wikilink") with this
background pre-set is available.

Just open up the file located in and import/load \[1\] the wanted file.
Make sure the model(s) is (are) nicely rotated and that the texture
shows up in blender \[2\], press to render and to save the file.


\[1\] Either *File*-\>*Import* an [MD2](MD2 "wikilink") or
*File*-\>*Append* from a file.

\[2\] There is a readme text inside the .blend file.

## Links

-

-

-

- \+

-

-

-

-

-

[Category:Contribute](Category:Contribute "wikilink")
[Category:Modelling](Category:Modelling "wikilink")