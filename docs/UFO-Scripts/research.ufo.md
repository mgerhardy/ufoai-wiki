## General

Currently all research related stuff is in .

- **tech**: [V_STRING](V_STRING "wikilink")


The **unique** name of the research item. It is a convention to start
the name with **rs_**

- **type**: [V_STRING](V_STRING "wikilink")


Just says where to look for more information (this is internal
information and will not be displayed anywhere, but is needed to
check/find information)

1.  **tech**: [V_STRING](V_STRING "wikilink")
    - Items have all the information in here. Especially the name and
      the model/image.
2.  everything else (weapon, craft, building, alien, etc...)
    - See the correct [scriptfile](UFO-Scripts "wikilink") file.

- **name**:
  [V_TRANSLATION_MANUAL_STRING](V_TRANSLATION_MANUAL_STRING "wikilink")


self-explaining i hope :) Only needed when type=tech

- **up_chapter**: [V_STRING](V_STRING "wikilink")


Defines in which chapter of the ufopedia this item will show up. (The
chapters are defined in **up_chapters main**)

- **description**:
  [V_TRANSLATION_MANUAL_STRING](V_TRANSLATION_MANUAL_STRING "wikilink")


A short string that is used by gettext to be translateable (e.g
"_itemname_txt").

This needs to be a unique string in all desciptions. See the po files in
the source directory (src/po/\*.po)

- **pre_description**:
  [V_TRANSLATION_MANUAL_STRING](V_TRANSLATION_MANUAL_STRING "wikilink")


A short string that is used by gettext to be translateable (e.g
"_itemname_pre_txt").

This needs to be a unique string in all desciptions. See the po files in
the source directory (src/po/\*.po)

This string is displayed if you've collected some items but have not
researched them yet

- **require_AND**:


This is a list of required techs or collected items that all are
possible to get the current tech

- **require_OR**:


This is a list of required techs or collected items where at least one
has to be researched already to get the current tech

- **provides**: [V_STRING](V_STRING "wikilink")


The item (only one allowed) name in the correct ufo file or
data-structure (e.g inventory).

The given names are **not** "tech" items.

This items can be produced once the "tech" item has been finished.

- **time**: [V_INT](V_INT "wikilink")


Default: 0

time the research needs (the time that one scientist would need to
research the item i.e. the maximum time to complete the research with no
pauses). If time is 0 the item can be produced at the same time all the
"required" items are finished.

- **researched**: [V_BOOL](V_BOOL "wikilink")


Default: false

1.  false: You need to research this tech.
2.  true: You can **produce** it from the beginning.

- **needscollected**: [V_BOOL](V_BOOL "wikilink")


Default: false

1.  false: You only need to have the required technologies researched to
    research this item.
2.  true: To be able to research this item you need to have all required
    technologies researched and at least one item collected.

- **image_top / image_bottom**: [V_STRING](V_STRING "wikilink")


Path to the image that should be displayed on the top (big) or bottom
(small) in the ufopedia.

- **mdl_top / mdl_bottom**: [V_STRING](V_STRING "wikilink")


Same as the image but for 3d-models.

It overrides the image-definitions if it is provided.

- **producetime**: [V_INT](V_INT "wikilink")


How many days per item

## Files

Currently there are two files containing "tech" descriptions:

-

-

## Example

    tech rs_weapon_kerrblade
    {
        name    "_Alien Artifact - Kerrblade"
        type    weapon
        up_chapter  artifacts

        description {
            default "_kerrblade_txt"
        }
        pre_description {
            default "_kerrblade_pre_txt"
        }

        mail_pre
        {
            from    "_mail_from_paul_navarre"
            to      "_mail_to_base_commander"
            // subject  defined by "name"
            icon    icons/artifact
        }

        mail
        {
            from    "_mail_from_paul_navarre"
            to      "_mail_to_base_commander"
            // subject  defined by "name"
            icon    icons/artifact
        }

        require_AND
        {
            item kerrblade 1
            tech rs_skill_close
            tech rs_damage_normal
        }
        provides    kerrblade
        time    200
        producetime -1
    }

## Links

- [Research](Research "wikilink")

[Category:UFO-Scripts](Category:UFO-Scripts "wikilink")
[Category:Contribute](Category:Contribute "wikilink")