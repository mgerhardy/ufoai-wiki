## General

- **font**
  [V_TRANSLATION_MANUAL_STRING](V_TRANSLATION_MANUAL_STRING "wikilink"):


the font path relative to

this var is translateable to allow [translators](Translating "wikilink")
to use their own fonts - just translate this value in your po file and
you use a self defined font

- **size** [V_INT](V_INT "wikilink"):


the font size

- **style** [V_STRING](V_STRING "wikilink"):
  - **TTF_STYLE_NORMAL**
  - **TTF_STYLE_BOLD**
  - **TTF_STYLE_ITALIC**
  - **TTF_STYLE_UNDERLINE**

## Example

    font f_menu
    {
        font    "_media/FreeSans.ttf"
        size    22
    }

    font f_menubig
    {
        font    "_media/FreeSans.ttf"
        size    28
        style   TTF_STYLE_BOLD
    }

## Links

- [UFO-Scripts](UFO-Scripts "wikilink")

[Category:UFO-Scripts](Category:UFO-Scripts "wikilink")
[Category:Contribute](Category:Contribute "wikilink")