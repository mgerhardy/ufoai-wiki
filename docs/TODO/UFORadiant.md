## TODO list for UFORadiant

### Engine

- Replace depracted gtk function calls

- Use realpath() (MinGW has this afaik, too) to get the path of the
  binary. This will allow us to run uforadiant from anywhere - even
  without specifying the working directory. Useful for e.g. assigning
  the action to open a \*.map file in UFORadiant by double clicking it.

- Replace image plugin with GtkImage

  - A first step was to replace the jpeg and tga implementations with
    those from GDK (jpeg, tga and png support is included now) - the
    next step would be to remove the plugin completely and use the
    GtkImage

- Remove picomodel and use libg3d for the model plugin

- (Windows) fix integration with ufo2map for error checking

  - gtk package issue - there is a helper executable which seams to be
    missing from the gtk package we provided earlier - it's maybe fixed
    in current trunk with recent gtk package
    --[Mattn](User:Mattn "wikilink") 21:10, 16 January 2009 (UTC)
  - output on pastebin is gone. I think it also could be related to exec
    behavior which is different for windows - we have to figure a way to
    interact with the started processes. -
    [RudolfoWood](User:RudolfoWood "wikilink") 14:42, 6 February 2009
    (UTC)

- use data dir from configure for better packaging options

### Sidebars

- entity inspector - typesafety (see ):

  - parser for entities.ufo (remove entities.def)

  - new value: only show valid keys


perhaps some kind of combobox inside the keys column? -
[RudolfoWood](User:RudolfoWood "wikilink") 14:08, 22 February 2009 (UTC)

implemented a combobox, still some issues to fix with multi-selection
(related to inconsistency below) -
[RudolfoWood](User:RudolfoWood "wikilink") 08:12, 26 March 2009 (UTC)

- - fill with reasonable default value (from parsed definitions)

  - after choosing the new value, default value should be selected and
    editable, and this field should receive focus.

  - typecheck after edit of value

### improvements/features

- Terrain/footstep improvements:

  - Add SoundPreview widget to the surface inspector if only faces are
    selected the the GlobalUFOScript() terrain functions found a sound
    for the selected texture.

  - render sound icon for footstep marked surfaces

- generate ump files or add map tiles to existing ump files

  - UMPFile class for reading and writing ump files

  - Add tile to ump feature

  - UMPEditor

- map load preview: Basic code is there, see MapFileChooserPreview class

- render sun angles in the 2d viewports as a circle and a line in the
  upper right corner of each viewport.

- add a misc_sound renderer that is showing the area where the sound is
  hearable. We have a renderer for this already for the light entity.

- particle editor [thumb](image:Radiant-particleditor.png "wikilink")

  - a particle browser is now in the sidebar

    - improve the data structures and the parsing functions to be able
      to get all the data that is needed to play the animations

    - render particle animations

- texture browser should highlight those textures that have a material
  in the map material file

- integrate materials into render engine

  - some blending is already implemented

- render particle images (3d) and/or models (2d + 3d) in the views

- make 3D freelook also work with num/capslock on

- make brush cutting preserve contentflags

- Radiant should not save incorrect maps - for example, scientific
  notation texture offset does not make game happy (report at Bug)

- Radiant uses absolute paths for models, should save relative ones (to
  directory)

  - Not a problem on Linux - seams to be windows only - maybe mixed
    directory separators --[Mattn](User:Mattn "wikilink") 13:11, 17
    January 2009 (UTC)
  - mixed directory separators caused problems in
    path_get_filename_start, perhaps other occurences. -
    [RudolfoWood](User:RudolfoWood "wikilink") 16:35, 5 February 2009
    (UTC)
    - Still a problem? --[Mattn](User:Mattn "wikilink") 19:33, 27 August
      2009 (UTC)

- TextureCache is not freed before destroy (load big maps like
  corrupter_crash and close Radiant) -\>textures.cpp:Textures_Destroy
  must be changed

  - there is still a todo for particles - there was a problem with
    releasing textures - [RudolfoWood](User:RudolfoWood "wikilink")
    14:25, 8 February 2009 (UTC)

- integrate features into uforadiant

  - we've ufomodel now - not all md2.pl feature are included yet, but we
    should use ufomodel as backend, uforadiant only as frontend.

- Texture panel shouldn\`t steal keyboard focus when it\`s open. It\`s
  impossible to change for example grid when texture panel is open.

-- interactive search (enabled by default for treeviews) grabs focus, is
disabled in r27334 and can still be used with Ctrl-F (or another default
search shortcut) [RudolfoWood](User:RudolfoWood "wikilink") 18:50, 30
November 2009 (UTC)

- Remade ![](Filter-treeview.png "Filter-treeview.png") filter system,
  currently it has many useless for game entries, but misses some really
  needed things like misc_particle. It can be done via sidebar panel,
  with tree of possible filtered items, look to screenshot.

-- added some more filter options in r27337 as temporary solution

- - introduce filter settings from xml like darkradiant has

  - create filter tree view

- Make texture sidebar's "Hide Unused" state persistent. If I select
  "Hide Unused", then switch to a folder whose contents haven't been
  loaded, currently it loads all the textures and then I have to select
  "Hide Unused" again. If "Hide Unused" has been selected, I would like
  the sidebar to hide and NOT LOAD the unused textures as I browse
  through different folders (not loading will save time switching
  between folders).

-- darkradiant uses an improved TextureBrowser, perhaps it would be good
to use their version [RudolfoWood](User:RudolfoWood "wikilink") 19:12, 7
December 2009 (UTC)

- An option to apply texture to all selected surfaces except nodraws. I
  may be getting greedy here, but it would be nice to be able to select
  brushes and apply a texture to all selected surfaces EXCEPT any
  surfaces already textured with nodraws (maybe also the other
  tex_common textures. That way if I've already marked the nodraws but
  want to change textures, I don't have to individually select all but
  the bottom face of a brush. Not worth implementing unless it's fairly
  easy on the coding side, but thought I'd write it down. -- H-Hour

  - quite easy - class FaceSetShader

- It would be great if the feature (= using ufo2map -check out of
  radiant) would work. [ShipIt](User:ShipIt "wikilink")

  - radiant does not save (or load) the compiler binary path

[Category:TODO](Category:TODO "wikilink")
[Category:Contribute](Category:Contribute "wikilink")
[Category:Development](Category:Development "wikilink")
[Category:Mapping](Category:Mapping "wikilink")