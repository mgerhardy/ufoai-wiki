## Basic processing

In ufo, scripts create (among other things), the user interface. These
scripts all have extension .ufo. When ufo encounters such a script it is
processed. Ufo now accepts two script languages to create the user
interface: a custom script language, called ufo script and a lua script.
Both script languages can be used side-by-side. Ufo determines the
script type by scanning the first line of the script file. If it starts
with:

    --!/usr/bin/lua

the script is considered to be a lua script and is processed by the
embedded lua interpreter, else the script is considered to be ufo script
and is processed by ufo script parser.

For a lua script, the entire script is first parsed by the lua
interpreter. If no errors are found, the lua script is then executed by
the lua interpreter. This is the moment youre script actually gets
executed for the first time. Scripts are loaded in the order as they
appear in the folder. This is why files containing generic stuff usually
start with an underscore.

## UI-scripting 'The lua way...'

Before you start, you should become familiair with the lua language
itself and most of all with the fact that lua is not an object oriented
language. Objects in lua are represented by a data structure called a
table, essentially being a container holding data and functions. This
mechanism is broadly used since every user interface node becomes a
table. However, since lua is not an OO-language, there is no mechanism
to add the "self" parameter in a method call. To solve this, lua
programmers since long have used the following trick:

    function fooTable.fooMethod(self, arg1)
        -- the code
    end

Since it was so broadly use, eventually Lua added a second function call
mechanism that does add implicitly a "self" parameter. It uses the ":",
like this:

    function fooTable:fooMethod(arg1)
        -- the code
    end

Be aware however that this calling mechanism applies only for functions
calls and not for data fields. So to access a data field on a table you
use the "." seperator, like this:

    local x = fooTable()
    x.fooData = 123

This distinction is important since everything in the UFO lua API is
exposed using functions with the exception of event handlers (note the
":" when accessing functions on a table and the "." when accessing the
field holding the on_click event handler. Here is some sample code:

    -- get the window node
    local x = node:root()
    -- attach an event handler to respond  to a mouseclick
    x.on_click = function (sender)
            -- do whatever you want to do when the user clicks
        end

## Accessing the API

All parts of ufo exposed to lua is accessible from within lua using the
"ufo" namespace. It contains the global functions, classes and
constants. For a complete list of the API see \[...\].

The API follows the naming of properties and methods in the ufo script
language with a few exceptions. In general this is the case when the
naming in the ufo script is either ambigious or confusing. For instance,
in ufo script the property "string" in general is being used to refer to
the text displayed by a control, so it was renamed to "text".

The lua API uses the following naming convention: - Getters are not
prefixed, so e.g. to get the name of the node you call "name()" -
Getters for flags however are prefixed by "is_", e.g. "is_virtual()" -
Setters are prefixed by "set_", e.g.
"set_background("icon/windowplusb")"

## Processing after loading

After a script is processed it is possible to run a onload event. To do
so, just put a call to register_onload somewhere in the script. A sample
is given below:

    function foo_onload ()
        -- do whatever you want to do after the script is processed
    end

    register_onload (foo_onload)

The difference by the way is subtle. The onload is executed just after
the lua script is processed so in theory it is possible to achieve the
same result by positioning foo_onload at the end of the script (it is
then executed last). However, in future, it might be that onload will be
executed after the loading/processing of all ufo lua scripts.

## Creating a user interface

To create a user interface, the second step in processing of the .ufo
file should yield a uiNode (single node or tree of nodes). To create
nodes, the api exposes node creation functions through the common ufo
namespace. Even though lua will allow it, you should never create a
uiNode directly. With the uiNode object (or any of its descendents) in
hand, you can start calling methods to alter the desired behaviour (e.g.
set the background).

    main = ufo.create_window ("main", nil)
    main::set_background("ui/main_bg")

The user interface makes a distinction between "controls", "windows" and
"components". Controls are user interface elements, e.g. buttons.
Controls are always located inside a container. A "window" is a
top-level user interface element. A "component" is a clonable group of
controls. A component typically is created around a container control
(e.g. a panel). Like controls, components can be created and added to
windows.

    local smallstring = ufo.create_component ("string", "smallstring", nil)
    smallstring:set_font("f_verysmall")
    smallstring:set_color(0.56, 0.81, 0.76, 1.0)

## Creating functions in lua

It is easy to write functions in lua. Functions can be shared through
the entire lua environment, just make sure that the function is known at
the moment it is used. It is also possible to attach a function to a
user interface node. If you declare a function on a lua node, it is
reusable anywhere else even in the old script language. For example, the
code below creates a panel component to be reused. It defines two
functions on the node. These functions do not exist in the C++ side of
ufo, only on the lua side. However they can now be used in the user
interface. Even if the old style script is used.

    local common_panel = ufo.create_component ("panel", "common_panel", nil)
    common_panel.enable = function (sender)
            common_panel:set_background("ui/enabled")
        end
    common_panel.disable = function (sender)
            common_panel:set_background("ui/disabled")
        end

## Creating and using confunc's

A confunc is a script defined node that can be called as a command
either from the console or from any other script. To define a confunc,
you must create a node of class "confunc". Then define an on_click event
with the signature of the command. Any parameters to the confunc are
accessible as additional parameters following "sender", the first
parameter of any function.

    local foo_func = ufo.create_confunc(parent_node, "pop_initready_aircraft", nil)
    foo_func.on_click = function (sender, arg1, arg2)
            sender:parent():child("craftname"):set_text(arg1)
            sender:parent():child("missionname"):set_text(arg2)
        end

Note that in the example above the arguments are named arg1 and arg2 but
they can have any name. In this case a more logical name would be
"craft" for arg1 and "mission" for arg2.

## Storing data on a node

Like functions, in lua it is easy to add data fields to a table.
However, using this mechanism is not advised since there is no guarantee
that the lua table will not be destroyed by the garbage collector. Ufo
has it's own mechanism to create persistent variables, either by
creating a "cvar" or by using a data node.

## Lua identifier scoping and the use of do..end

Identifiers have a scope (if you get lost here and don't know what
'scope' is, then I suggest you first start reading some books about
programming before continuing). Defining the same identifier twice in a
scope results in an error. Whenever you define a ui element, variables
are prefixed with the keyword 'local', indicating that the scope of the
variable is limited to this lua file only. If you forget the 'local'
keyword the identifier becomes visible in all lua files, possibly
resulting in a duplicate identifier error.

Another way of limiting the scope of identifiers is to use the 'do..end'
block.

    do
        local foo_panel = ufo.create_component ("panel", "common_panel", nil)
        ...
    end

In this case the identifier 'foo_panel' is visible only inside the
'do..end', thereby limiting the visibility to only a part of the file.
The use of 'do..end' is strongly advised since it prevents accidental
nameclash. Also it is a must in the asset files, wich define a number of
generic ui components.

## Utility libaries

One advantage of using lua is that it allows for libraries of support
functions that can greatly enhance the process of creating the user
interface. A most useful library is the ufox library. For more info, see
[UFO-Scripts/ui/LUA-utility-functions](UFO-Scripts/ui/LUA-utility-functions "wikilink")

[Category:Coding](Category:Coding "wikilink")
[Category:Contribute](Category:Contribute "wikilink")