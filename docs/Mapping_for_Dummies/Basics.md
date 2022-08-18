## Basic Definitions

You can find a list of commands for UFORadiant
[here](Mapping/Mouse_and_Keyboard "wikilink"), however, there are a few
things you need to know first for that list to make sense.

- A "Brush" is an object on screen. It is not what you draw the object
  with, it **IS** the object. You usually click and drag a box on the
  screen (left mouse button), and what you get is called a brush. This
  object is the core of the entire map building process.
- A "View" is the big grid in the middle when you open up Radiant. It
  primarily starts off in the 4 view split view, where you will see a 3D
  camera view, a top-down view, and then two views from the side.
- An "[Entity](Mapping/Entities "wikilink")" is a special kind of object
  that is different from brushes. For the most part, your map will
  consist of brushes and entities. Brushes provide the static geometry
  of the map (all of the architecture). Entities are used to handle
  special cases: they allow you to add lights and locations where enemy
  will spawn.
- Vertex is the corner of an object. If a square has four corners, we
  call these vertices.

## Controlling the View

![](Radiant_views.png "Radiant_views.png")

To change what you're looking at, hold down on the mouse in whichever
view you prefer and drag yourself around. You will see your view change.
In the grid views, you will see the grid slide around as you move. You
can zoom in and out by using your mouse's scrollwheel.

In the 3D view, you don't need to hold down . Clicking it once will
"capture" your mouse and wherever you move the mouse will change the
direction of the camera. This is called mouselock mode. While you're in
mouselock mode, you can hold to move the camera's position. By doing
this, you can fly around the map to see what you're working with. When
you're done adjusting the camera, hit again to exit mouselock mode.

will re-center the camera view. The arrow keys will take the view
forward/back and slide left/right. Note that if or is on then the camera
view will behave differently. You will usually want to use 3D view with
them both turned off. While in mouselock mode you can also move the view
by using the scrollwheel.

### Showing and Hiding Items

To better manage your view, you'll want to be able to hide things you're
not working on. There are a few ways to do this:

- **Levels:** Just like in the game, you can view a map that's been
  split into levels by clicking the icons numbered 1-8 on the top bar of
  UFORadiant. This will show only those items that should appear on each
  level.
- **Filters:** UFORadiant has loads of filters to help you easily hide
  things. You can find them by going to Filters at the top (same row as
  File/Edit). Any option with a check next to it is being filtered. If
  it's running a bit slow, filtering out entities is a great way to
  speed up UFORadiant.
- **Show/Hide:** There's also an option to hide items you have selected.
  Go to View at the top, then Hide/Show to hide selected items and show
  hidden ones. Don't worry, we're just about to get to how to select
  brushes

## Selection

First, because it happened to me: If you've already tried to make a
brush and now you can't deselect it, hit the button to deselect
anything. I think I spent the first 15 minutes in the editor figuring
out how to do this because I started fiddling before reading all the
instructions.

To select a brush, hold while clicking on the object. Note that this
will select the top-most brush in the stack. If you are using the
top-down view, it will select the brush with the face on top of other
brushes. If it's the front view, it will select brushes in the front.
And so on.

To select a single face of a brush you can hold down and and click to
select the face under the cursor.

If you're having trouble with other brushes getting away, don't forget
the Show/Hide options from the previous section. You can also use to
hide them and to show all hidden items.

To expand your selection, hold and click on multiple brushes. You can
also hold and hold , then drag the mouse to select everything that falls
within a range. Holding and clicking will also remove items from the
selection.

In the camera view window, you can also use the below described
'Mapinfo' sidebar panel to select objects and work with them without
having to try to dig your way through numerous levels of layered
brushes. This is most helpful for entities, though, because the brushes
are not well identified in the 'Mapinfo' panel.

## Creating and Modifying Brushes

![](Radiant_resize.png "Radiant_resize.png")

We can create or modify brushes in any view other than the 3D view.

To create or modify a brush, we need to make sure we're in the Resize
mode. Make sure the icon shown in the image to the right is selected (or
click ) to select it.

When in Resize mode, simply click and drag with the . You'll always
start with a cube. In order to make complex shapes, you'll need to carve
up the cube and piece several different brushes together. But don't
worry about that just yet.

To modify the brush when it is selected, click and hold down the
*outside of the brush*. You should not be clicking on the brush but
somewhere outside of it.. Then, while holding the drag the mouse and you
will see the shape change.

To move any object (brushes or entities) in Resize mode, click *inside*
the brush and drag around. Pretty straightforward.

If you modify the vertices of a brush () you should always grid align
the vertices. This is also true for cutting brushes () or CSG carving.

## Sidebar

On the right of UFORadiant you'll see a panel with several tabs. Each of
these sidebars will give you different features.

### Entities

This is where you will set properties for
[entities](Mapping/Entities "wikilink"). It also gives you a tree view
of every item in your map. All the entities are listed and you can find
all the brushes under the worldspawn entity. It's more useful for
finding entities, because brushes are not identified at all.

### Surface

The [surface panel](Mapping/Surface_inspector "wikilink") allows you to
set all the properties for brushes and those properties which can be
applied to single faces of a brush. Align textures, choose which levels
a brush should appear on, and pretty much everything else. This panel
will become a close friend.

### Prefabs

This panel will let you browse and insert
[prefabs](Mapping/Prefabs "wikilink") into your map.

### Textures

Access all of the textures available in the game. You can apply them to
a brush or face by selecting the brush or face and double clicking on
the texture in the texture panel.

### Particles

This is not yet fully implemented, but will eventually allow you to view
particle effects to include in your map.

### Map Info

Counts the different ([entities](Mapping/Entities "wikilink")) on the
map.

### Job Info

I have no idea!

## Grid layout

You may have noticed when creating a brush that you are locked onto the
grid system. Everything you do must correspond to the grid. But you can
change the spacing of the grid to be smaller or larger.

You can change the size of the grid by using the number keys above the
keyboard (1 is smaller than 0). You can also choose the Grid option at
the very top of UFORadiant and select a different grid size.

The grid is incredibly important, as the later tutorial on
[dimensions](Mapping/Dimensions "wikilink") will explain. Because
soldiers walk around on a grid in the battlescape, everything you build
in the map must be laid out accordingly. That's why it's always a good
idea to keep in mind what grid you're on when building in UFORadiant.

If you're coming to UFORadiant from more extensive 3D modeling software,
like 3DSM, you may not be used to working on-grid. It will probably be
one of the more difficult adjustments to make and one of the unique
aspects of building for a grid-based tactical game.

## Texturing brushes

You need to add textures to a brush to make them pretty. To do so,
select the brush (or just the face of the the brush ) and then open the
texture browser in the sidepanel. Find the texture you want and double
click on it.

## General useful information

To get your map to build into a file correctly (what the game uses to
play the map), you'll need at least three brushes on the map with their
level settings correct. It must also be a minimum of 20 64x64 visible
squares (Figure 320 x 256). I haven't tested if this can be shrunk when
you go up multiple levels, but a 'single level' map is hit with this
constriction. However, you will **NOT** need to place any alien or human
start points yet.

*(I'm not sure if the following is still correct.)* The map will also
have a 22 meg memory usage hard limit in the game. This includes
equipment models, actor models, etc. So, even if your compiled .bsp file
is smaller then this restriction, you may run into it. If you are
crashing to desktop with a .bsp file that's larger then around 14-15
megs, it's quite possible nothing is wrong but memory dumps. Be aware if
your map is VERY complex.

## Further steps

Play around with the controls here to get used to what they're going to
do, and then come back and we'll walk you through setting up a map
without people, and then adding some folks to it.

When you're done making a very broken toy while playing with the tools,
go to [Lesson 1](Mapping_For_Dummies/Lesson1 "wikilink").

[Category:Mapping](Category:Mapping "wikilink")
[Category:Contribute](Category:Contribute "wikilink")