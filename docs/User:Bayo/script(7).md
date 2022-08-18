UFO:AI scripts, inside `.ufo` files, are used to define most of the
content of the game.

Yet, there is no global parser for this kind of files. Each node type
use is own code to read one by one token and use them like it want. Then
here some construction rules, scripts should respect to unify our
scripts. It was not created from scratch, but from script legacy, with
patch here and there to allow unifying and avoid most of ambiguous
constructions.

This grammar is already used by our Eclipse plugin, to parse and
validate scripts.

But all scripts are not yet conform to that.

## Grammar

    UFOSCRIPT := NODE*

    NODE := TYPE IDENTIFIER? BLOCK
          | TYPE IDENTIFIER? LIST
          | TYPE VALUE

    BLOCK := '{' NODE* '}'

    LIST := '(' VALUE* ')'

    VALUE := NUMBER | QUOTED_STRING | NAMED_CONST | REFERENCE

    TYPE       := NAME
    IDENTIFIER := NAME
    REFERENCE  := NAME

    ----

    NAME := [a-z][a-zA-Z0-9/\-_\.]*

    NUMBER := [0-9.]+

    QUOTED_STRING := '"' -> '"'

    NAMED_CONST := [A-Z][A-Z_]*

This grammar is simplified to stay readable. But some construction may
not be allowed.

## Values

| NUMBER        | A number, like `6`, or `56.2`                                                                                                                                                                                                                          |
|---------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| QUOTED_STRING | Any kind of content between to double quotes. It support common C escaping, like `\n`, `\"`. Many composite types are also quoted, for example `"2.5 4.0 2.5"` which is a 3D vector; or `"1 0 0 0.5"` which can be a red color with some transparency. |
| NAMED_CONST   | A named constant provided by the game. It must be in full upper case, for example `EMPL_PILOT`, and usualy there is only a set of available values. It should be always used when a value is hardcoded into the game (instead of a quoted string).     |
| IDENTIFIER    | An unique identifier of the script object.                                                                                                                                                                                                             |
| REFERENCE     | A reference to an unique identifier provided somewhere else in the script.                                                                                                                                                                             |

## Structure

### Block

A block contains sub nodes, which can contains another blocks. Usualy it
is used like a set of properties (key-value structure). But it can be
used like a sequence of definitions.

    item armour_light
    {
        name            "_Combat Armour"
        image           "armour/light"
        center          "0 0 -5"
        ...

        protection
        {
            normal_light    20
            normal_medium   18
            normal_heavy    12
            ...
        }

        rating
        {
            normal      30
            blast       30
            fire        20
            ...
        }
    }

Block can be identified by an id. Which is the case for most block from
the root, but not only.

Bellow, `intro` identify the `sequence` block, and `i_sentence1`
identify one `obj2d` block. We also can see the script refer to that
localy defined block.

    sequence intro
    {
        ...

        obj2d i_sentence1
        {
            text    "_intro_sentence1"
            pos     "512 100"
            align   "uc"
            color   "0.2 1 0.5 0"
            fade    "0 0 0 0.5"
            speed   "0 0"
            relative    false
        }

        ...

        rem i_sentence1
    }

### List

A list contains a set of values. It can not contain a block or a list.
But number, string, const or references.

Some script use it to define a "real" list of values

    mapdef africa_large
    {
        map     "+africa"

        ...

        gametypes   ( fight1on1 fight2on2 coop2 coop3 coop4 )

        ...

        aircraft    ( craft_drop_firebird craft_drop_herakles craft_drop_raptor )
        ufos        ( craft_ufo_harvester )
        terrains    ( "grass" "tropical" "desert" "mountain" )

        ...
    }

Others use it like a tuple to define a composite object. In this kind of
way it can be better to use a block. At least you should think about the
two ways. A block is more verbose but it is self descriptive and more
easy to custom.

    equipment multiplayer_initial
    {
        name "_Multiplayer"
        item (assault       10)
        item (assault_ammo  13)
        item (machinegun     1)
        ...
    }