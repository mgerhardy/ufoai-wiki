Cookbook, and tips. Feel free to add new help.

## How to link a text node with a scrollbar?

        text mailclient
        {
            ...

            /* called every time the view into the node change (scroll position or number of line change)
             */
            onViewChange {
                *node:parent.mailclient_scroll@fullsize = <fullsize>
                *node:parent.mailclient_scroll@fullsize = <viewsize>
                *node:parent.mailclient_scroll@current = <viewpos>
            }
        }

        vscrollbar mailclient_scroll {
            ...

            /* called when the user play with the scroll */
            onChange {
                *node:parent.mailclient@viewpos = <current>
            }
        }

The `onViewChange` event is called when the content of the control
"move". The content itself do not change, but we display more or less
lines, or we scroll it.

## How to group nodes together?

You can use a `panel` to group nodes. That means if you move/hide the
panel, you move/hide every other node inside this panel, too.

The syntax for setting properties to the panel is almost the same as for
a window.

        panel soldier_info {
            {
                visiblewhen "mn_show_employee == 1"
                pos "700 380"
                size "300 400"
            }

            string pwr_lbl { pos "10 3"  string "_Strength:" }
            string pwr_val { pos "285 3"  string "*cvar:mn_tpwr" align ALIGN_UR }
            pic pwr_brd { pos "14 18"  image "ui/bar_border" }
            tbar pwr_bar
            {
                pos "17 18"  current "*cvar:mn_vpwr" gap_width 3 texl "3 0" image "ui/bar_attribute"
                size "250 16"   max 100
            }
        }

This example comes from `hire.ufo`.

## How to display a part of an image file?

You can use a `pic` node and `texh` and `texl` properties.

Assume you are using a picture with the dimensions 128x32 that includes
2 buttons - each of a size 64x32. One of them is used for highlighting
the other one (remember the [node
events](UFO-Scripts/ui/*.ufo "wikilink")). The first button (the left
one) uses the **texl** coordinates `texl "0 0"` and the **texh**
coordinates `texh "64 32"` because it starts at pixel 0 for x and y and
go 64 pixels in x direction and 32 pixels in y direction. The hover part
of the current button was placed right beside the current item at x 64,
y 0 - this leads to a **texl** of `texl "64 0"` and **texh** of
`texh "128 32"`

## How to set an excluderect?

THis example come from `hud.ufo`. It show a part of the background GUI,
where we exclude two rectangle to allow to click on the battlescape
(instead of in the `pic` node). Excluderect position are relative to the
node `pos "0 0"` mean the top-left rectangle start at the top-left of
node. Number of excluderect per node don't have limit.

        pic bar_team
        {
            image   "hud/bar_teammember"
            pos "512 0" size "256 56"   texh "256 56"
            blend   true
            excluderect { pos   "168 18"    size    "44 47" }
            excluderect { pos   "168 29"    size    "89 36" }
        }

## How to use params into condition?

ATM there is 2 way to use params. The first way is to use `<...>` with a
number. `<1>` mean we use the first param of a function (`func`,
`confunc`). It is deprecated, but it is the only way ATM to concatenate
text with param (for example `"Welcome to my <1>"`).

The second way is to use reserved word `param1`... Then with an example:

    if (param1 != 0) { ... }

## String or number comparison?

We dont use the same operator for string and number (because it is more
easy to compile it like that :-). Patch to remove that is anyway
welcome.

If we want to compare the param with a string we must use `eq` or `ne`.

    if (param1 eq "foo") { ... }

If we want to compare the param with a number we must use `==`, `!=`,
`<=`, `<`...

    if (param1 == 0) { ... }

## How to create a composite model

A "composite" model is a model with many submodels. For example, actors
are splited into body and head, and we can also add weapons.

To script the GUI, we need a main model (the model where to link
submodels) This model define tag (named anchor) used to set position and
orientation of submodels. It need position and size like any other
nodes; but submodels dont need it.

A submodel dont need a lot of properties. Here we can see a scale, the
default value is already 1, but we can custom it to have a bigger head
or weapon.

        model body
        {
            {
                visiblewhen "*cvar:mn_show_employee >= 1"
                model       "*cvar:mn_body"
                skin        "*cvar:mn_skin"
                anim        "stand2"
                angles      "0 70 90"
                scale       "6.7 6.7 6.7"
                pos     "469 382"
                size        "200 355"
                origin      "0 -40 0"
            }

            model head
            {
                model       "*cvar:mn_head"
                skin        "*cvar:mn_skin"
                tag     "tag_head"
                scale       "1.0 1.0 1.0"
            }

        }

## How to associate a key with an action into a window?

If it is a personal key (only u will use it) open your own
"`base/keys.cfg`" (near the directory where save game are). Else open
the game "`base/keys.cfg`" (where the "ufo" binary is).

Then, add/remove/edit `bindui` command lines. You should look at
"`base/ufos/ui`" to use right node path.

    bindui KEY "NODEPATH"

[Category:GUIs](Category:GUIs "wikilink")
[Category:UFO-Scripts](Category:UFO-Scripts "wikilink")