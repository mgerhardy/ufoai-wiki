## Intro

This page intends to be a summary and reference of "Surface Inspector"
use and effects for UFO:AI. Surface Inspector can be opened by using the
"Surfaces" tab in the Sidebar.

Mostly this is the effects of each flag when no other flag is set.
Combinations of flags can be tricky but mostly it seems that "going
through" effects override blocking effects. Ex: if you set 2 flags, one
allowing shots to go through the brush and the other one blocking the
shots, final effect will be to allow the shots going through.

Note: It is a common convention to use the appropriate texture for some
of the flags. So if you put the 'actorclip' flag on a brush, you also
have to assign the texture.

## Texture options

![](Surface_inspector.png "Surface_inspector.png")

| Field or button     | Purpose                                                                                                                                                                                                              |
|---------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Shader              | [Texture](Artwork "wikilink") path and name, starting from , without extension.                                                                                                                                      |
| Horiz./Vert. Shift  | horizontal/vertical shift of the applied texture                                                                                                                                                                     |
| Step                | For all fields - by how large value should scroll buttons change the field.                                                                                                                                          |
| Horiz./Vert. Scale  | vorizontal/vertical stretch of the applied texture. Note that it is applied to the whole texture, so shifted textures will have the stretch applied also to parts that do not fit on the face.                       |
| Rotate              | Rotation of the texture                                                                                                                                                                                              |
| Fit Texture (A) (B) | The numbers of (A) and (B) determine the scaling of the texture for the X-/Y-axis (equivalent X-/Z-axis or Y-/Z-axis, depending on the face that is selected). <Fit> will apply the setting to the selected face(s). |
| Flip Texture        | Flip the texture horizontally or vertically.                                                                                                                                                                         |
| Modify Texture      | 'Auto-Fit' the texture of the selected face. Often useful, but also gives weird results sometimes.                                                                                                                   |
| Default Scale       | Choose the scaling for the texture of new brushes.                                                                                                                                                                   |
| Texture Lock        | Same as in the Side Toolbar. Used when moving brushes around to avoid the texture shift. Especially useful when integrating prefabs into the map.                                                                    |
|                     |                                                                                                                                                                                                                      |

Texture related controls

## Surface and contentflags

Surface and contentflags affect almost everything regarding brush,
except the texture - visibility, transparency, additional effects, even
sounds. The following attempts to be a full list of these flags used in
UFO:AI.

Meaning of each attribute:

- visual effect : does the flag change the face's appearance?
- player : can a human player go through a "wall" with that flag set
- shots : can a shot go through a "wall" with that flag set
- visibility : is it possible to see through a "wall" with that flag set
- blast: does a blast go through a "wall" with that flag set (tested
  with rocket)

### Surface flags

#### **light**

- visual effect: produces light
- players:
- shots:
- visibility:
- blast:
- used for: lamps

#### **blend33**

- visual effect: 2/3 transparent
- players:
- shots:
- visibility: go through
- blast:
- used for: windows, water

#### **blend66**

- visual effect: 1/3 transparent
- players:
- shots:
- visibility: go through
- blast:
- used for: windows, water

#### **nodraw**

- *Note: The following requires levelflags to be set for the level of
  the brush and every level above! So if the brush is located in e.g.
  level 3, levelflags 3 - 8 have to be set. If not, the nodraw brush
  will block the 'Line of Sight' and also the 'Line of Fire', but he
  will not block actor movement and also he will not cast a shadow.*
  [ShipIt](User:ShipIt "wikilink") 13:33, 11 April 2012 (SAST)
- visual effect: invisible, but casts shadow
- players: blocked
- shots: blocked
- visibility: blocked
- blast: blocked
- used for: shadows, performance optimisations, models
- specific texture: tex_common/nodraw texture should be always used

#### **warp**

- visual effect: warps
- players:
- shots:
- visibility:
- blast:
- used for: water surface
- notes: Should be assigned to visible faces only

#### **fireaffected**

- visual effect: none until fired up
- players: blocked
- shots: blocked
- visibility: blocked
- blast: blocked
- used for: faces that should have an ability to light on fire, like
  straw
- notes: Will spawn a fire particle when shot with some flames inducing
  weapon, fo example, flamethrower

#### **footstep**

- visual effect: none
- players: blocked
- shots: blocked
- visibility: blocked
- blast: blocked
- used for: faces that should produce a sound when stepped on
- notes: See [footsteps](Mapping/Footsteps "wikilink")

#### **flow**

- visual effect: flows
- players: blocked
- shots: blocked
- visibility: blocked
- blast: blocked
- used for: river
- notes: To change the direction of moving rotate the texture with the
  surface inspector

#### **phong**

- visual effect: smoothes the texture
- players: blocked
- shots: blocked
- visibility: blocked
- blast: blocked
- used for: barrels, pipes, rocks, tree trunks
- notes: Should be assigned to visible faces only

### Content flags

#### **level1 to level8**

- see [Levelflags](Mapping/Levelflags "wikilink") or [Levelflags - step
  by step](Mapping/Tutorials/Levelflags "wikilink")

#### **actorclip**

- visual effect : invisible (no shadow)
- players : blocked
- shots : go through
- visibility : go through
- blast : blocked
- used for : limiting actor movement (whole cells and railing), creating
  "floor", stairs (see [Ladders](Mapping/Ladders "wikilink"))
- specific texture: tex_common/actorclip texture should be always used
- Note : If no levelflags set, the actorclip brush is not shown anymore
  in UFORadiant when using the levelselector.

#### **weaponclip**

- visual effect : invisible (no shadow)
- players : go through
- shots : blocked
- visibility : go through
- blast :
- used for : blocking shots on objects that wouldn't block them
  otherwise (for example, models)
- specific texture: tex_common/weaponclip texture should be always used
- Note : If no levelflags set, the weaponclip brush is not shown anymore
  in UFORadiant when using the levelselector.

#### **lightclip**

- visual effect : invisible (but casts shadow)
- players : unaffected
- shots : unaffected
- visibility : unaffected
- blast : unaffected
- used for : shadows
- specific texture: tex_common/lightclip texture should be always used
- Note : If no levelflags set, the lightclip brush is not shown anymore
  in UFORadiant when using the levelselector.

#### **solid**

- visual effect : none
- players : blocked
- shots : blocked
- visibility :
- used for : mostly by ufo2map during compilation phase to determine
  which brushes will have priority when splitting overlapping brushes
- Note : if trans33 or trans66 is checked, it overides solid flags (ie
  the brush is transparent and allows everything to go through it)

#### **water**

- visual effect : none (no shadow)
- players : go through
- shots : go through
- visibility : go through
- used for : water. Use **flow** flag for "flowing liquid" and **warp**
  for water bodies like lakes or seas, fences


plays sounds on entering the brush;

exports envmaps for that surface (material) (explanation by mattn)

#### **window**

- visual effect : doesn't draw inside of the brush
- players :
- shots : blocked
- visibility :
- used for : windows, of course.

#### **passable**

- visual effect : none, does not cast a shadow
- players : go through
- shots : blocked
- visibility : go through

#### **terrain**

- notes : *"It forces texture coordinate plane to be horizontal, even if
  face in question is at \>45 deg angle to horison. Intended to keep
  texture mapping continuous on steep slopes. Not to be used on exactly
  vertical faces, this could cause rendering anomalies. In other words,
  it forces texture to be mapped in xy plane, disabling xz and yz
  cases."*

#### **origin**

- visual effect : invisible
- players :
- shots :
- visibility :
- used for : [doors](Func_door "wikilink")

## Value

Used for surface lights (see surfaceflag **light** and [surface
lights](Mapping/Lights#Surface_lights "wikilink")).

[Category:Mapping](Category:Mapping "wikilink")
[Category:Contribute](Category:Contribute "wikilink")