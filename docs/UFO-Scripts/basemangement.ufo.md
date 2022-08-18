## Bases

## Buildings

**name** ()
The name of the facility

**image** ()
The picture for this facility, as seen on the base screen, relative to

**fixcosts** ()
The construction cost for this facility

**depends** ()
Facilities need the things listed here to function.

**type** ()
The type this facility belongs to. Used for upgrades.
**hangar**, **lab**, **hospital**, **quarters**, **workshop**

**build_time** ()
The time (in days) this facility takes to construct

**varcosts** ()
The monthely maintenance cost for this facility

**map_name** ()
The name of the map tile for this facility (in )

**pedia** ()
The tech ID that has the UFOpaedia entry for this facility

**needs** ()
Additional sections of this facility. Used for facilities larger than 1
tile

**capacity** ()
The capacity of this facility. The meaning of the value depends on the
building type.

**onconstruct** ()
The name of the script to be run when this facility is built up. Don't
add a ; at the end.

**ondestroy** ()
The name of the script to be run when this facility is destroyed. Don't
add a ; at the end.

**visible** ()
Sets whether this facility is visible on the base screen. Set the first
part of a building to 1 all others to 0 otherwise all building-parts
will be on the list

**max_count** ()
No base may have more than this amount of this facility

**starting_employees** ()
The amount of employees that come with this building

**level** ()
building level

**mandatory** ()
Automatically construct this building when a base is set up.

### Example

    building building_hangar
    {
        name                "_Large Hangar"
        image               base/drop2
        fixcosts            68000
        depends             building_powerplant
        build_time          8
        varcosts            5500
        map_name            "drop"
        pedia               rs_building_large_hangar
        type                hangar
        needs               building_hangar2
        ondestroy           "building_ondestroy"
        starting_employees  8 //Number of soldiers in dropship when first base is built
        capacity            1
    }

    building building_hangar2
    {
        name        "_Large Hangar"
        image       base/drop1
        pedia       rs_building_large_hangar
        visible     false // no 'needs' field here!
    }

## Base Templates

basetemplate templateName

building_name ()
Pair: id of building - position in basescreen.

<!-- -->

    basetemplate balanced {
        building_entrance       "2 4"
        building_quarters       "4 3"
        building_quarters       "3 3"
        building_aliencontainment   "0 1"
        building_storage        "3 4"
        building_powerplant     "4 4"
        building_command        "4 2"
        building_hangar         "0 3"
        building_intercept      "1 3"
        building_workshop       "4 0"
        building_radar          "1 4"
        building_lab            "3 1"
        building_hospital       "3 2"
    }

## Links

- [UFO-Scripts](UFO-Scripts "wikilink")

[Category:UFO-Scripts](Category:UFO-Scripts "wikilink")