## General

Your tutorials will be available as
[sequences](UFO-Scripts/seq_*.ufo "wikilink"). You can always start them
by typing

    seq_start [sequenceID]

to the [console](console "wikilink").

To let them also appear in the tutorial menu you need to add a few more
lines:

    tutorial gameplay
    {
        name    "_Gameplay"
        sequence    tut_gameplay
    }

    sequence tut_gameplay
    {
        [..]
    }

This lets the tutorial with the id *tut_gameplay* appear in
[menu](UFO-Scripts/menu_*.ufo "wikilink") with the
[translatable](translating "wikilink") name *Gameplay*. As mentioned
above you can start this tutorial by typing

    seq_start tut_gameplay

to [console](console "wikilink").

## Keys for tutorial

- **name**: [V_TRANSLATION_STRING](V_TRANSLATION_STRING "wikilink")
- **sequence**: [V_STRING](V_STRING "wikilink")

## Links

- [Sequences](UFO-Scripts/seq_*.ufo "wikilink")

[Category:UFO-Scripts](Category:UFO-Scripts "wikilink")
[Category:Contribute](Category:Contribute "wikilink")