Draft for exporting from Blender 2.63:

Be sure to grab the updated exporters (2.63+), I've pushed them to the
repository:

- -

  -

Drop them to

Go to: File -\> User Preferences -\> Addons tab -\> Import/Export
Category, and enable the Quake2 MD2 and UFO:AI TAG exporters.

Open your model, assign it at least one texture, **Important:** The
texture *name* will be the models skin name, UFO:AI uses as convention:
".texname" note the leading dot and the absence of file extension.

Select one and only one mesh, go to File -\> Export -\> Quake MD2, if
you are exporting a static model uncheck the 'Export animation'
checkbox, select filename and path, Save! (Note about animations: the
exporter will export all frames from the current Start frame to the
current End frame, set them appropriately or you may end with
extra/missing frames)

If your model has tags, select all the tags you need to export (tags
must be 'Empty' objects) go to File -\> Export -\> UFO:AI TAG, select
filename and path and save, the tag file needs to have the same name as
the md2 (Note: as above the exporter will export all frames from the
current Start frame to the current End frame, they need to be the same
number of frames than the md2 or the game will error out)