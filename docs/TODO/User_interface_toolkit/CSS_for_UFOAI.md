## Subset of CSS

A simple subset of CSS to allow to create random dictionary of
properties per classname without any type checking (only string of
char).

We can parse an only one CSS file and save data for access to the
properties. When we read GUI scripts, when we read a `class`, we can
find CSS properties and apply it to the node as it is a property
(providing a tuple `name,value`). The node check itself the property
name, and the property value).

It request to create a simple CSS parsing (look very similar to the UFO
script) and a data access (random access to a classname; iterator of
properties per classname); and a very little update of the node parser.

### Syntaxe

    STYLESHEET = RULE*
    RULE = '.' IDENT '{' PROPERTYSET* '}'
    PROPERTYSET = IDENT ':' (VALUE|QUOTEDVALUE) ';'
    QUOTEDVALUE = '"' (ESCAPE|VALUE|SPACE|';')* '"'

    IDENT = [a-zA-Z][a-zA-Z0-9_-']*
    VALUE = [^;"]*
    ESCAPE = '\' [a-z"'\\]
    SPACE = [\t\s]

### Sample

    .classname1 {
        property1: value;
        property2: "foo bar";
        property3: 1 1 0.75 1;
    }

    .classname2 {
        property1: value2;
    }

## Sample for menu_main.ufo

### CSS

    .mainButton {
        size: 256 64;
        image: "menu/button_big";
        font: "f_menubig";
        color: 0 0.5 0 1;
        selectcolor: 1 1 1 1;
    }

### UFO script

        custombutton button_singleplayer
        {
            pos "640 170"
            click   { cmd "mn_push singleplayer" }
            string  "_Single-player"
            class   mainButton
        }

        custombutton button_multiplayer
        {
            pos "640 240"
            click   { cmd "mn_push multiplayer;" }
            string  "_Multiplayer"
            class   mainButton
        }

        custombutton button_options
        {
            pos "640 310"
            click   { cmd "mn_push options;" }
            string  "_Options"
            class   mainButton
        }

        custombutton button_tut
        {
            pos "640 380"
            click   { cmd "mn_push tutorials;" }
            string  "_Tutorials"
            class   mainButton
        }

        custombutton button_credits
        {
            pos "640 450"
            click   { cmd "seq_start credits;" }
            string  "_Credits"
            class   mainButton
        }

        custombutton button_exit
        {
            pos "640 520"
            click   { cmd quit }
            string  "_Exit"
            class   mainButton
        }