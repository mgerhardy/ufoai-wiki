- slots for equipement per aircraft

:\* every aircraft definition in aircraftmanagement.ufo should have
defined amount (and maybe position in aircraft equip menu?) of slots for
additional equipement; moreover, the weapon slot should have additional
parameter called weight, with possible values: light, medium, heavy,
which will be used in aircraft weapons assigning; an example:

    aircraft craft_interceptor {
    ...
    shield    1
    weapon    1 light
    weapon    1 medium
    electronic 1
    ...
    }

- introduce parameters of an aircraft

:\* aircraft definition in aircraftmanagement.ufo should have parameters
with default values; those parameters are:

    //      range - the range of the aircraft, which tells how far aircraft can fly
    //      wrange - the range of the weapon, which tells the minimum distance
     of opening fire
    //      speed - the speed of the aircraft, which tells how fast the aircraft is
    //      shield - the parameter of aircraft armour, which tells aircraft's protection
    //      ecm - the parameter of electronic level at aircraft, the bigger, the
     lower possibility to hit by enemy
    //      damage - the parameter of weapon power, which tells how much damage
     such aircraft can do
    //      accuracy - the parameter of weapon accuracy, the bigger, the bigger
     possibility to hit an enemy

:\* an example of aircraft entry in aircraftmanagement.ufo:

    aircraft craft_interceptor {
    ...
    range   800
    wrange    0 /* no weapon by default */
    speed   120
    shield    0 /* no shield by default */
    ecm       0 /* no ecm by default */
    damage  100
    accuracy  0 /* no weapon by default */
    }

::\* Imo these values should be inherited from the aircraft item. The
values are all **0** by default (due to memset) and should only be
filled if e.g. the aircraft definition tell us to load a weapon by
default. It isn't a good idea to add all these 0 values to the script
files - very error prone imo. --[Mattn](User:Mattn "wikilink") 07:33, 27
May 2007 (CEST)

:::\* I agree - for these which depends on aircraft items; for example
speed value is defined per aircraft by default too (without aircraft
items)--[Zenerka](User:Zenerka "wikilink") 09:30, 28 May 2007 (CEST)

- new struct, a member of aircraft_t

<!-- -->

    typedef enum {
    CRAFT_RANGE,
    CRAFT_WRANGE,
    CRAFT_SPEED,
    CRAFT_SHIELD,
    CRAFT_ECM,
    CRAFT_DAMAGE,
    CRAFT_ACCURACY
    } craftparameters_t;

    typedef struct craftstats_s {
    craftparameters_t parameter;
    int value;
    } craftstats_t;

    typedef struct aircraft_s {
    ...
    craftstats_t craftstats;
    } aircraft_t;

- the code to adding or removing an equipement in aircraft equip menu -
  use craftitem type to put it to proper slot; use weapon weight to put
  it to proper weapon slot

- the code to calculate (craftstats_t) when adding or removing an
  equipement in aircraft equip menu

- in the long run, of course, use craftstats_t at airfights

[Category:Contribute](Category:Contribute "wikilink")
[Category:TODO](Category:TODO "wikilink")
[Category:Development](Category:Development "wikilink")