Main window is where most of the time is spent during mapping.
Understanding what each component in there does can help in the process.

## Main window components

This is how main window looks right after starting up UFORadiant. As a
lot of things can be customized, look may differ depending on e.g. used
screen/resolution.

<figure>
<img src="01_radiant_main.png" title="01_radiant_main.png" width="800"
alt="01_radiant_main.png" />
<figcaption aria-hidden="true">01_radiant_main.png</figcaption>
</figure>

If you open a map, many areas are populated with map data. Here's how
Radiant looks with map opened (main areas annotated):
<img src="31_radiant_main_opened.png" title="31_radiant_main_opened.png"
width="800" alt="31_radiant_main_opened.png" />

### Context menu

on a 2D view will open Context menu.

### Toolbar icons

| Icon                                                                                   | Tooltip text | Action                                                 |
|----------------------------------------------------------------------------------------|--------------|--------------------------------------------------------|
| ![Image:02_open.png](02_open.png "Image:02_open.png")                                  |              | Opens file selection dialog to choose map file         |
| ![Image:03_save.png](03_save.png "Image:03_save.png")                                  |              | Saves current map                                      |
| ![Image:04_undo.png](04_undo.png "Image:04_undo.png")                                  |              | Undoes actions                                         |
| ![Image:05_redo.png](05_redo.png "Image:05_redo.png")                                  |              | Redoes actions                                         |
| ![Image:06_x-flip.png](06_x-flip.png "Image:06_x-flip.png")                            |              | Flips selected object on x axis                        |
| ![Image:07_x-rotate.png](07_x-rotate.png "Image:07_x-rotate.png")                      |              | Rotates selected object on x axis                      |
| ![Image:08_y-flip.png](08_y-flip.png "Image:08_y-flip.png")                            |              | Flips selected object on y axis                        |
| ![Image:09_y-rotate.png](09_y-rotate.png "Image:09_y-rotate.png")                      |              | Rotates selected object on y axis                      |
| ![Image:10_z-flip.png](10_z-flip.png "Image:10_z-flip.png")                            |              | Flips selected object on z axis                        |
| ![Image:11_z-rotate.png](11_z-rotate.png "Image:11_z-rotate.png")                      |              | Rotates selected object on z axis                      |
| ![Image:12_select_touching.png](12_select_touching.png "Image:12_select_touching.png") |              | Selects brushes that are touching the selected brush   |
| ![Image:13_select_inside.png](13_select_inside.png "Image:13_select_inside.png")       |              | Selects brushes that are inside the selected brush (?) |
| ![Image:14_csg_subtract.png](14_csg_subtract.png "Image:14_csg_subtract.png")          |              | Subtracts selected brushes from all other brushes      |
| ![Image:15_csg_merge.png](15_csg_merge.png "Image:15_csg_merge.png")                   |              | Merges the selected brushes, if possible               |
| ![Image:16_hollow.png](16_hollow.png "Image:16_hollow.png")                            |              | Redoes actions                                         |
| ![Image:17_select_vertices.png](17_select_vertices.png "Image:17_select_vertices.png") |              | Enters vertice selection mode                          |
| ![Image:18_select_edges.png](18_select_edges.png "Image:18_select_edges.png")          |              | Enters edge selection mode                             |
| ![Image:19_select_faces.png](19_select_faces.png "Image:19_select_faces.png")          |              | Enters face selection mode                             |
| ![Image:20_cubic_clip.png](20_cubic_clip.png "Image:20_cubic_clip.png")                |              | Toggles cubic clip                                     |
| ![Image:21_translate.png](21_translate.png "Image:21_translate.png")                   |              | Selects translate tool                                 |
| ![Image:22_rotate.png](22_rotate.png "Image:22_rotate.png")                            |              | Selects rotate tool                                    |
| ![Image:23_scale.png](23_scale.png "Image:23_scale.png")                               |              | Selects scale tool                                     |
| ![Image:24_resize.png](24_resize.png "Image:24_resize.png")                            |              | Selects QE/resize tool                                 |
| ![Image:25_clipper.png](25_clipper.png "Image:25_clipper.png")                         |              | Selects clipper tool                                   |
| ![Image:26_texture_lock.png](26_texture_lock.png "Image:26_texture_lock.png")          |              | Enables/disables texture lock                          |
| ![Image:27_entities.png](27_entities.png "Image:27_entities.png")                      |              | Opens entity list                                      |
| ![Image:28_console.png](28_console.png "Image:28_console.png")                         |              | Opens Radiant console                                  |
| ![Image:29_texture_browser.png](29_texture_browser.png "Image:29_texture_browser.png") |              | Opens Radiant texture browser                          |
| ![Image:30_refresh_models.png](30_refresh_models.png "Image:30_refresh_models.png")    |              |                                                        |
|                                                                                        |              |                                                        |

Main toolbar

<table>
<caption>UFO:AI toolbar</caption>
<thead>
<tr class="header">
<th><p>Icon</p></th>
<th><p>Tooltip text</p></th>
<th><p>Action</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><img src="01_level1.png" title="Image:01_level1.png"
alt="Image:01_level1.png" /> <img src="02_level2.png"
title="Image:02_level2.png" alt="Image:02_level2.png" /> <img
src="03_level3.png" title="Image:03_level3.png"
alt="Image:03_level3.png" /> <img src="04_level4.png"
title="Image:04_level4.png" alt="Image:04_level4.png" /><br />
<img src="05_level5.png" title="Image:05_level5.png"
alt="Image:05_level5.png" /> <img src="06_level6.png"
title="Image:06_level6.png" alt="Image:06_level6.png" /> <img
src="07_level7.png" title="Image:07_level7.png"
alt="Image:07_level7.png" /> <img src="08_level8.png"
title="Image:08_level8.png" alt="Image:08_level8.png" /></p></td>
<td></td>
<td><p>Selects brushes marked to appear in a particular level</p></td>
</tr>
<tr class="even">
<td><figure>
<img src="10_actorclip.png‎" title="Image:10_actorclip.png‎"
alt="Image:10_actorclip.png‎" />
<figcaption aria-hidden="true">Image:10_actorclip.png‎</figcaption>
</figure></td>
<td></td>
<td><p>Toggles actorclip brush displaying</p></td>
</tr>
<tr class="odd">
<td><figure>
<img src="11_weaponclip.png" title="Image:11_weaponclip.png"
alt="Image:11_weaponclip.png" />
<figcaption aria-hidden="true">Image:11_weaponclip.png</figcaption>
</figure></td>
<td></td>
<td><p>Toggles weaponclip brush displaying</p></td>
</tr>
<tr class="even">
<td><figure>
<img src="12_nodraw.png" title="Image:12_nodraw.png"
alt="Image:12_nodraw.png" />
<figcaption aria-hidden="true">Image:12_nodraw.png</figcaption>
</figure></td>
<td></td>
<td><p>Toggles nodraw brush displaying</p></td>
</tr>
<tr class="odd">
<td></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

UFO:AI toolbar

### Statusbar contents

| Area                                                                                                           | Description                                                                       |
|----------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------|
| ![Image:32_statusbar_tool.png](32_statusbar_tool.png "Image:32_statusbar_tool.png")                            | Shows selected tool name                                                          |
| ![Image:33_statusbar_position.png](33_statusbar_position.png "Image:33_statusbar_position.png")                | Shows position of mouse cursor                                                    |
| ![Image:34_statusbar_bru-ent_stats.png](34_statusbar_bru-ent_stats.png "Image:34_statusbar_bru-ent_stats.png") | Shows brush and entity count in the current map                                   |
| ![Image:35_statusbar_copied-tex.png](35_statusbar_copied-tex.png "Image:35_statusbar_copied-tex.png")          | Shows copied texture name. Currently not too useful in resolutions up to 1024x768 |
| ![Image:36_statusbar_something.png](36_statusbar_something.png "Image:36_statusbar_something.png")             |                                                                                   |
|                                                                                                                |                                                                                   |

Statusbar contents

[Category:Mapping](Category:Mapping "wikilink")
[Category:UFORadiant](Category:UFORadiant "wikilink")
[Category:Mapping](Category:Mapping "wikilink")
[Category:UFORadiant](Category:UFORadiant "wikilink")