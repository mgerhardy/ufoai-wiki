## Campaigns

- **name** [V_STRING](V_STRING "wikilink")

name of campaign

example: "_Standard Campaign"

- **text** [V_STRING](V_STRING "wikilink")

example: "_txt_standard_campaign"

campaign description

- **team** [V_STRING](V_STRING "wikilink")

example: human

which team?

- **soldiers** [V_INT](V_INT "wikilink")

how many soldiers in this campaign?

example: 12

- **difficulty** [V_INT](V_INT "wikilink")

what is the difficulty of this campaign? 0 is standard, the greater the
harder. This modifies the rate at which alien interest increases
throughout the campaign.

example: 0

- **minhappiness** V_FLOAT

if more than half the nations have a happiness below this value, game
will be lost.

example: 0.30

- **maxdebts** V_INT

the maximum money you can borrow before loosing game.

example: 20000

- **xvirate** V_INT

maximum average [XVI](XVI "wikilink") rate of nations before the game is
lost.

example: 70

- **researched** V_STRING

list of researched topic when the game starts.

example: rslist_human

- **ugvs** V_INT

number of UVGs you start the game with.

example: 2

- **equipment** [V_STRING](V_STRING "wikilink")

which [equipment](UFO-Scripts/equipment.ufo "wikilink") to use

example: campaign_player

- **market** [V_STRING](V_STRING "wikilink")

which market definition to use. This is an
[equipment](UFO-Scripts/equipment.ufo "wikilink") definition, too

example: campaign_market

- **credits** [V_INT](V_INT "wikilink")

how much credits at start

example: 500000

- **map** [V_STRING](V_STRING "wikilink")

which map to use for geoscape? The maps are in *base/pics/geoscape*.
There need to be different maps, for the 2D geoscape a version for day
and a version for night, for the 3D geoscape a map for each season in at
least the low resolution version; masks for culture, nations, population
and terrain are also needed. Have a look at the existing ones for more
information.

example: map_earth

- **visible** [V_BOOL](V_BOOL "wikilink")

is this campaign visible in campaign list

example: true

- **date** [V_DATE](V_DATE "wikilink")

starting date

example: "2000 0 7"

- **researchrate** V_FLOAT

The number of research hours a single scientist produces for each hour
of game time. Raising this number makes research go faster.

example: "0.8"

- **uforeductionrate** V_FLOAT

This number is used in the equation that determines how many UFOs are
spawned in a given cycle. Must be between 0.0 and 1.0. Higher numbers
will result in fewer UFOs spawning.

example: "0.75"

- **employeerate** V_FLOAT

An abstract number to increase or decrease the number of new employees a
player receives each month. The base number will be multiplied by
employeerate. If a nation was going to give 2 soldiers and employeerate
is set to 1.5, the player will receive 3 soldiers. *Note: nation
happiness influences this as well so there is more at play than the
nation employee value in nations.ufo.*

example: "1.0"

- **initialinterest** V_INT

The alien interest level at which the game starts. Alien interest
increases one per day and is used to determine at what stage of the game
UFOs appear, as well as some special events. Default is 20.

example: "20"

- **alienbaseinterest** V_INT

The alien interest level at which aliens begin building bases. See
**initialinterest** above.

example: "200"

### Salary definitions

You can define the salary values for each campaign. Valid identifiers
are:

- soldier_base [V_INT](V_INT "wikilink"):
- soldier_rankbonus [V_INT](V_INT "wikilink"):
- worker_base [V_INT](V_INT "wikilink"):
- worker_rankbonus [V_INT](V_INT "wikilink"):
- scientist_base [V_INT](V_INT "wikilink"):
- scientist_rankbonus [V_INT](V_INT "wikilink"):
- medic_base [V_INT](V_INT "wikilink"):
- medic_rankbonus [V_INT](V_INT "wikilink"):
- robot_base [V_INT](V_INT "wikilink"):
- robot_rankbonus [V_INT](V_INT "wikilink"):
- aircraft_factor [V_INT](V_INT "wikilink"):
- aircraft_divisor [V_INT](V_INT "wikilink"):
- base_upkeep [V_INT](V_INT "wikilink"):
- debt_interest [V_FLOAT](V_FLOAT "wikilink"):

#### Example

    salary {
        soldier_base 3200
    }

### Example

    campaign main
    {
        name        "_Standard Campaign"
        text        "_txt_standard_campaign"
        team        human
        soldiers    9
        scientists  6
        workers     14
        medics      2
        difficulty  0
        minhappiness    0.30
        maxdebts    200000
        xvirate     70
        salary {
            soldier_rankbonus 500;

        }
        researched rslist_human
        ugvs    2
        equipment   campaign_player
        market      campaign_market
        credits     1350000
        map         map_earth
        visible     true
        date        "2084 79 6"
    }

[Category:UFO-Scripts](Category:UFO-Scripts "wikilink")
[Category:Contribute](Category:Contribute "wikilink")