A sequence is a cinematic using the game engine to render 3D models,
image, text, sounds, and music. It can be displayed in fullscreen, or as
a part or the GUI.

With this type of UFO-script we can make your own sequences. Have a look
at the **base/ufos/seq_\*.ufo** for more examples.

## `precache [model|pics]`

- .. for `models` as parameter: pathnames relative from -folder
- .. for `pics` as parameter: pathnames relative from -folder
- .. (string) filenames for

### Example

    precache models
    {
        "models/civilians/male/body01"
        "models/civilians/male/head01"
    }
    precache pics
    {
        ufoai
    }

## `camera NAME`

- **omega**: [V_VECTOR](V_VECTOR "wikilink")


moving

- **zoom**: [V_FLOAT](V_FLOAT "wikilink")


value for zooming

- **dist**: [V_INT](V_INT "wikilink")



- **origin**: [V_VECTOR](V_VECTOR "wikilink")


where does it start?

- **angles**: [V_VECTOR](V_VECTOR "wikilink")


rotation

### Example

    camera cam1
    {
        zoom    1.0
        angles  "30 225 0"
        dist    100
    }

## `obj2d NAME`

- **text**:
  [V_TRANSLATION_MANUAL_STRING](V_TRANSLATION_MANUAL_STRING "wikilink")


the translateable text

- **pos**: [V_POS](V_POS "wikilink")


x, y (normalized to 1024x768 resolution)

- **align**: [V_ALIGN](V_ALIGN "wikilink")


ur, ul, uc, ...

- **color**: [V_COLOR](V_COLOR "wikilink")


The RGBA value for the obj2d

- **fade**: [V_COLOR](V_COLOR "wikilink")


RGBA

- **speed**: [V_POS](V_POS "wikilink")


speed in two directions (x,y)

- **relative**: [V_BOOL](V_BOOL "wikilink")


will be placed relative to previous element - useful if you use
translateable text and don't know for sure how many lines the translated
text uses

- **enlarge**: [V_POS](V_POS "wikilink")


value used for scaling the obj2d

- **bgcolor**: [V_COLOR](V_COLOR "wikilink")


the RGBA value for the background color

- **font**: [V_STRING](V_STRING "wikilink")


the font that should be used to display the text (see [font
definitions](UFO-Scripts/fonts.ufo "wikilink"))

- **image**: [V_STRING](V_STRING "wikilink")


the image path - relative to

- **name**: [V_STRING](V_STRING "wikilink")



- **inbackground**: [V_BOOL](V_BOOL "wikilink")


If true, the engine render the object before the 3D models. Default
value is false.

### Example

    obj2d herby_text
    {
        text    "Code, Visual Effects"
        pos "974 50"
        align   ur
        color   "0 1 0 0"
        fade    "0 0 0 1"
    }

## `model NAME`

- **tag**: [V_STRING](V_STRING "wikilink")



- **anim**: [V_STRING](V_STRING "wikilink")


see anm-file for model

- **skin**: [V_INT](V_INT "wikilink")


skinnumber

- **parent**: [V_STRING](V_STRING "wikilink")


parent model (e.g. head and body) (at head: name of the body-model)

- **speed**: [V_VECTOR](V_VECTOR "wikilink")


speed in all three directions (x,y,z)

- **omega**: [V_VECTOR](V_VECTOR "wikilink")


moving

- **origin**: [V_VECTOR](V_VECTOR "wikilink")


where does it start?

- **angles**: [V_VECTOR](V_VECTOR "wikilink")


rotation

### Example

    model herby_body
    {
        model   models/civilians/male/body01.md2
        skin    2
        anim    walk0
        origin  "-277.5 0 0"
        speed   "60 0 0"
    }
    model herby_head
    {
        model   models/civilians/male/head01.md2
        parent  herby_body
        tag tag_head
    }

## General commands

- **wait**: [V_FLOAT](V_FLOAT "wikilink")


value of seconds to wait

- **cmd**: [V_STRING](V_STRING "wikilink")


command to execute

- **rem**: see `delete`
- **delete**: [V_STRING](V_STRING "wikilink")


remove a ressource - string is the NAME of the ressource to remove

- **animspeed**: [V_INT](V_INT "wikilink")


set the speed used for animation of models. The default value is 1000
milliseconds. A smaller value will set a slower animation.

- **click**


Will halt the sequence execution until the user clicked a mouse button

- **sound** NAME


NAME is a soundfile relative to the directory.

- **music** NAME


NAME is a musicfile relative to the directory.

### Example

    wait 0.2
    delete herby_body
    delete herby_head
    delete herby_text

## Example

    sequence intro
    {
        music mission
        animspeed 100

        obj2d i_sentence1
        {
            text    "_intro_sentence1"
            pos     "512 485"       align   uc
            color   "0 1 0 1"
            speed   "0 -30"
            relative    true
        }
        obj2d i_sentence2
        {
            text    "_intro_sentence2"
            pos     "512 510"       align   uc
            color   "0 1 0 1"
            speed   "0 -30"
            relative    true
        }
        obj2d i_sentence3
        {
            text    "_intro_sentence3"
            pos     "512 535"       align   uc
            color   "0 1 0 1"
            speed   "0 -30"
            relative    true
        }
        obj2d i_sentence4
        {
            text    "_intro_sentence4"
            pos     "512 560"       align   uc
            color   "0 1 0 1"
            speed   "0 -30"
            relative    true
        }
        obj2d i_sentence5
        {
            text    "_intro_sentence5"
            pos     "512 585"       align   uc
            color   "0 1 0 1"
            speed   "0 -30"
            relative    true
        }
        wait 200.0

        delete i_sentence1
        delete i_sentence2
        delete i_sentence3
        delete i_sentence4
        delete i_sentence5
    }

## Tool

The command `seq_start` allow to display a random sequence in
fullscreen.

Open the console and type:

    seq_start NAME_OF_THE_SEQUENCE

[Category:Contribute](Category:Contribute "wikilink")
[Category:UFO-Scripts](Category:UFO-Scripts "wikilink")