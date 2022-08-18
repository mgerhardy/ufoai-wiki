## Ufox extensions

Using the lua api to create a hierarchy of ui nodes leads to a lot of
typing. So there is an alternative. Using the ufox utility library. This
library contains a set of functions to create a ui tree from a set of
nested lua tables specifying the structure of the ui nodes and the
values of the properties. Currently ufox supports the following three
functions for creating ui node structures:

    ufox.build (data, parent)       create a tree of ui nodes from data and assign them as child to prent
    ufox.build_window (data)        create a window and associated child controls from data
    ufox.buidl_component (data)     create a component and associated child controls from data

Using these functions leads to code like this:

    local ui_data = {
        class = "panel",
        name = "pnlTest",

        pos = { 10, 250 },
        size = { 200, 200 },
        layout = ufo.LAYOUT_TOP_DOWN_FLOW,
        layoutmargin = 15,
        backgroundcolor = { 0.50, 0.00, 0.00, 1.00 },

        {
            class = "MainMenuBtn",
            name = "btnTest1",
            text = "_Test 1",

            on_click = function (sender)
                        ufo.print("Hello Ufo AI!\n")
            end
        },

        {
            class = "MainMenuBtn",
            name = "btnTest2",
            text = "_Test 2"
        },

        {
            class = "MainMenuBtn",
            name = "btnTest3",
            text = "_Test 3"
        }
    }

    local ui_node = ufox.build(ui_data, node_parent)

The above code creates a subtree of ui nodes based on the data foun in
ui_data and assigns the subtree to the parent node specified in
node_parent (usually the window).

Using the ufox build-functions requires you to adhere to the following
guidelines:

- if a table declaration is to be converted to a ui control, at least
  the fields 'class' and 'name' must be specified
- a property can only be specified in the table declaration if there is
  a corresponding set function, so 'text' requires a set_text(..)
  function, 'background' a set_background(..) and so on
- the build_window function requires the top-level table declaration to
  have a 'class' field with value 'window'

## Common mistakes

Although the use of the table hierarchy actually looks a lot like the
old UFO-script, it is not the same. The most notable difference is the
use of the 'comma' to separate field-value definitions. A common mistake
is to omit a comma. If you do, you'll get an error like the following.

    lua load error: [string "main.ufo"]:136: '}' expected (to close '{' at line 11) near 'version'

The above error simply states that somewhere in the file main.ufo (near
line 136) in the list of field-value definitions a comma is missing.

## Caveats

Note that while the ui engine relies on creation order for the layering
order of ui nodes, lua does **not** guarantee the order of elements
within a table, and so the build functions detailed above **cannot**
guarantee the creation order of the nodes specified in the given table —
using them in a ui tree with nodes that require a specific layering
order **will** lead to the resulting window/component/ui nodes
misbehaving. This can be worked around by making consecutive calls to
the needed functions to ensure the correct layering.

    local ui_tree = {
        name = "inv_stats_hud",
        class = "window",
        pos = {236, 60},
        size = {560, 418},
        backgroundcolor = {0, 0.15, 0.1, 0.7},
        bordercolor = {0.58, 0.81, 0.758, 0.7},
        bordersize = 2,
        -- Inventory area background image - needs to layer below the other inventory nodes.
        {
            name = "inv_bg",
            class = "image",
            pos = {10, 59},
            size = {351, 349},
            source = "/ui/inv_bg"
        },
        -- Other bottom layer or layer independent nodes here
    }
    local inv_stats_hud = ufox.build_window(ui_tree)

    -- This node needs to layer on top of the background image above
    -- hence we create it in a separate step to ensure proper creation (and thus layering) order.
    do
        local container = { name = "headgear", class = "container", pos = {88, 85} }
        ufox.build(container, inv_stats_hud)
    end
    -- Other nodes to layer on top of the above here.