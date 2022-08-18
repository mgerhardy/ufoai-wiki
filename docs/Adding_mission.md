## General

Adding a new mission to an existing campaign is very easy. All you have
to do is to create a new mission tag and add this to a stage set
mission. Some of the keys are described in
[campaign.ufo](campaign.ufo#Missions "wikilink").

You can also set the [cvar](cvars "wikilink") **cl_showcoords** to **1**
to get the coordinates printed to console when you click somewhere on
geoscape.

## Example

### Mission

    mission farm
    {
        text        "_Location: Revelstoke\nType: Landed Alien Ship\nObjective: Secure Alien Ship before Liftoff"
        map     farm08
        music       mission
        pos     "116 52"
        aliens      7
        alienteam   alien
        alienequip  campaign_alien
        civilians   3
        civteam     european
        recruits    3
        $win        6000
        $alien      100
        $civilian   500
    }

### Stage and Stageset

To let this mission appear on geoscape during the game you have to add
it to a stage set mission tag:

    stage ufos_are_coming
    {
        set first
        {
            seq ufos_are_coming
            commands    "addufo"
        }
        set crashed_and_landed
        {
            delay       "0 0 1"
            frame       "0 10 0"
            expire      "0 3 0"
            missions    "transport mine construction farm office or_asyut"
            quota       4
            nextstage   invasion
        }
        set stop
        {
            needed      crashed_and_landed
            delay       "0 110 0"
            endstage    ufos_are_coming
        }
    }

As you can see here the mission **farm** was added to the stage set
**crashed_and_landed**. Now the mission is included in gameplay.

## Links

- [campaign.ufo](campaign.ufo "wikilink")
- [UFO-Scripts/equipment.ufo](UFO-Scripts/equipment.ufo "wikilink")
- [UFO-Scripts](UFO-Scripts "wikilink")
- [Create campaign](Create_campaign "wikilink")

[Category:UFO-Scripts](Category:UFO-Scripts "wikilink")
[Category:Contribute](Category:Contribute "wikilink")