## General

Wings3d is a free, OpenSource modelling program. Wings3d can be picked
up very quickly compared to some modelling programs, and the user
interface makes it quick to use. It can also be a powerful tool for
modelling once mastered; having a diverse set of mesh manipulation
tools.

Wings3d also supports UV mapping and texture files.

Wings3d can be downloaded from [the Wings3d
website](http://www.wings3d.com/) or the [Sourceforge project
page](http://sourceforge.net/projects/wings/).

## Export MD2 from Wings3d

Wings3d does not actually support any kind of exporting in the format
.MD2 and I've found no plug-ins which allow it to do this. This means
that currently the best method is to use another program that does
support the exporting like [3DSMax](Modelling/3DSMax "wikilink"),
[Blender](Blender "wikilink") or any of the other ones that you have to
hand.

This means that after the mesh is created its best to export into the
new program and follow that program's specific .MD2 exporting
instructions from there.


There is a [md3](md3 "wikilink") exporter and importer plugin for
Wings3D: see [their
SVN](http://wings.svn.sourceforge.net/viewvc/wings/trunk/plugins_src/import_export/).

There is also a [md2](md2 "wikilink") plugin feature request on the fr
tracker at:
[sourceforge.net](http://sourceforge.net/tracker/index.php?func=detail&aid=1720622&group_id=33028&atid=406955)

### Transferring your Wings file

You can't always say which format will be best to export from wings
which can then be imported into your chosen modelling program. For
example [Blender](Blender "wikilink") supports .wings import which can
be very useful.

But, I would say that as a general rule exporting your wings file as a
.obj file will probably be the best course of action. The .obj format is
a very clean and easy to edit modelling file format and so should be
widely supported and import/export from most programs without too many
problems.

### Scale

Getting a [md2](md2 "wikilink") file into Wings could become as much
trouble as exporting your wings file so I would suggest that the scaling
of your model is done best in the program you are going to use directly
before export as [md2](md2 "wikilink"). The fewer times you
import/export a model, the better.

If you have a set of meshes that are all of a related scale and need to
be exported its probably best to play with the import scale settings of
your chosen program to use before export. If the import settings don't
support this then the export settings from wings should support it.

### Create Animations

Wings3d currently doesn't support any form of rigging or animation. This
is best done in another program.

## Links

- [Wings3d Homepage](http://www.wings3d.com/)
- [Wings3d official development
  forum](http://p212.ezboard.com/bnendowingsmirai)
- [Wings3d tutorial
  site](http://www.geocities.com/paulthepuzzles/aardvarks.html)
- [Tutorial links](http://www.3dvalley.com/phplinks/index.php?PID=4)
- [Character creation
  tutorial](http://www.muranon.com/axel/character/tutorial_1/index.html)
- [Wings3D + CharacterFX +
  MotionBuilder](http://www.goldenxp.com/tutorials/)
- [Building a Bi-ped in
  Wings3d](http://www.combat-bunny.com/tutorial.html)

[Category:Contribute](Category:Contribute "wikilink")
[Category:Modelling](Category:Modelling "wikilink")