## General

With equipment definitions you can define various weapon and item pools,
that can be used for each campaign or mission.

## Example

    equipment replaceme
    {
        assault         2
        assault_ammo    4
        smg         2
        smg_ammo    4
    }

This will define an equipment pool with 2
[weapons](Equipment "wikilink") and the appropriate ammo. **replaceme**
will be the id you need to know if you want to access this definition in
e.g. a [campaign definition](campaign.ufo "wikilink").

## Skirmish/MP Menus

In the skirmish (and someday the MP menu as well), players can select
their equipment set. For this reason, you can also add a name parameter
to your equipment definition. The example above could be:

    equipment replaceme
    {
        name "_Assault Rifle and SMG"
        assault         2
        assault_ammo    4
        smg         2
        smg_ammo    4
    }

## Links

- [UFO-Scripts](UFO-Scripts "wikilink")
- [campaign.ufo](campaign.ufo "wikilink")
- [Adding mission](Adding_mission "wikilink")
- [Create campaign](Create_campaign "wikilink")

[Category:UFO-Scripts](Category:UFO-Scripts "wikilink")
[Category:Contribute](Category:Contribute "wikilink")