### Engine

- Merged a lot of the DarkRadiant features and cleanups
- Implemented skin rendering for the models not only in the
  modelbrowser, but also in the camera view - use the skin value from
  the entity to set the shader for the renderer
- Gettext support
- Position and size tracking for windows

### Sidebars

- Inconsistent marks in surfaceinspector/entityinspector (for selecting
  objects with different states)
- Reworked the entity inspector
- Reworked the surface inspector
- Add prefab/template menu.

### Improvements/features

- Modelbrowser - something like the texture browser - just rendering the
  models below
- Render trans33/trans66 brushes transparent in radiant
- Move brushes and entities level upwards/downwards and also modify the
  levelflags
- Integrate sound support into radiant to play misc_sounds
- Filters can be defined via xml
- UI settings are stored in xml files
- Bounding box rendering for misc_models
- Extended select features
- Added material and ump editors
- Group [RMA](Mapping/Random_map_assembly "wikilink") tiles
- Integrated ufo2map check option into the editor to directly jump to
  errors
- Implemented selection sets
- Add tooltip with information about entity/entity key from entities.ufo
- Added a new texture overview dialog
- Added overlay feature to render a picture in the background
- Added "skip-common" feature for replacing textures
- Added cut option
- New, better method for CSG subtract tool
- Added parsing of our LICENSES file to show whether the license of the
  used file is compatible

<File:Xywnd.png%7CFloating> XY Window <File:Texturetool.png%7CTexTool>
<File:Texturebrowser.png%7CUpdated> texture browser
<File:Shortcuteditor.png%7CShortcut> Editor
<File:Selectionsets.png%7CSelection> sets can be saved
<File:Filtereditor.png%7CFilter> Editor
<File:Entityinspector.png%7CUpdated> EntityInspector
<File:Routinginfo.png%7CShow> routing info
<File:Searchandreplace.png%7CSearch> and replace
<File:Soundview.png%7CSound> viewer
<File:Surfaceinspector.png%7CSurfaceInspector>

[Category:Changelog](Category:Changelog "wikilink")
[Category:Contribute](Category:Contribute "wikilink")
[Category:Development](Category:Development "wikilink")
[Category:Mapping](Category:Mapping "wikilink")