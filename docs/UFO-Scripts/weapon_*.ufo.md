## Item types

- Weapon

1.  `rifle`
2.  `pistol`
3.  `biggun`
4.  `rpg`
5.  `grenade`
6.  `melee`

- Ammo

1.  `ammo`

## Skills

There are several [skills](Skills "wikilink"), most of them having an
impact on weapon use, either accuracy or melee.

## Damage types

There are several [types of damage](Damage "wikilink"), some removing
health points, some inducing effects.

## Variables

name [V_TRANSLATION_STRING](V_TRANSLATION_STRING "wikilink")
this is the [translated](translating "wikilink") name of the weapon -
but in the script file it has to be in english.

the preceding underscore, as in "_Assault Rifle", indicates that the
text following it will be translateable via
[Gettext](Translating "wikilink").

model [V_STRING](V_STRING "wikilink")
model of the weapon relative to base/models (see [Directory
tree](Directory_tree "wikilink"))

weapon [V_BOOL](V_BOOL "wikilink")
it this a weapon or not? e.g. ammo is no weapon.

Among other effects, when an alien is assigned one primary weapon from
the equipment, this flag is used to tell weapon from ammo, even if it
has the same "buytype".

type [V_STRING](V_STRING "wikilink")
see item types above; they affect animation of using the weapon

animationindex [V_INT](V_INT "wikilink")
This is the animation index for the character with the weapon (see
[character animation](Modelling#Animation "wikilink")). This is useful
because a pistol will not be carried like a rpg. This affects walking
and standing with a weapon.

Don't confuse this with buytype (the category you can buy it in). See
below.

holdtwohanded [V_BOOL](V_BOOL "wikilink")
does this weapon always take to hands to hold? If true then the other
hand is unusuable while this weapon is equiped.

firetwohanded [V_BOOL](V_BOOL "wikilink")
does this weapon take two hands to fire? If true and something in the
other hand then firing is disabled.

shape [V_SHAPE_SMALL](V_SHAPE_SMALL "wikilink")
the shape in equipment menu, that is how much space do we need to place
this weapon (this value defines a rectangle given by the upper left
corner and dimensions). For non-rectangular shapes see [Non-rectangular
weapon
description](UFO-Scripts/weapon_*.ufo#Non-rectangular_weapons "wikilink").

center [V_VECTOR](V_VECTOR "wikilink")
move in three directions to display the item in menu. Middle coordinate
has something to do with the z axis, probably a rotation. The first is a
translation to the right, the third is a translation downwards. One unit
seems to be around 5 pixels on a 1024x768 screen. Horizontal parameter
moves to the left for positive values, and vertically positive values
move downwards.

scale [V_FLOAT](V_FLOAT "wikilink")
scale up or down for displaying in menu. Note that **shape** and
**scale** variables do not influence the size of the weapon in the
battlescape, so take care that small things do not have huge inventory
icons. On the other hand, it might a good idea to keep most primary
weapons the same inventory shape (even if, e.g., Rocket Launcher is very
long in the battlescape) and most secondary weapons the same (smaller)
inventory shape. This way they fit nicely in the backpack or holster.

It's not necessary to scale the object so that it completely fills all
the "shape" inventory box, just try to make it look nice.

thrown [V_BOOL](V_BOOL "wikilink")
is this weapon throwable? e.g. grenades

ammo [V_INT](V_INT "wikilink")
max ammo loaded for this weapon

reload [V_INT](V_INT "wikilink")
[TUs](TU "wikilink") for reloading

price [V_INT](V_INT "wikilink")
the price you have to pay when you buy it.

buytype [V_STRING](V_STRING "wikilink")
Defines in which category you will find this weapon:

- `buytype weap_pri` - All 'Primary' weapons and their ammo for
  soldiers.
- `buytype weap_sec` - All 'Secondary' weapons and their ammo for
  soldiers.
- `buytype misc` - Misc soldier equipment.
- `buytype armour` - Armour
- `buytype multi_ammo` - Only used for items (mostly ammo) that have to
  appear in the primary and the secondary list. (It's a workaround, but
  no problems have been spotted - yet.)

virtual [V_BOOL](V_BOOL "wikilink")
The item is virtual, which means it does not exist. It has a definition
for game mechanics only (like weapon/ammo stats, fire definitions).
Virtual items don't show up in user interfaces, are not collectible, but
can be available (as ammo to reload for example) if researched.

## Some variable types for ammo

damage [V_POS](V_POS "wikilink")
Example: `damage "xx y"`

The first number (xx) is the average damage, the second (y) is the
maximum random value than can be added/subtracted from the damage.

spldmg [V_POS](V_POS "wikilink")
Example: `spldmg "xx y"`

The first number (xx) is the average splash damage, the second (y) is
the maximum random value than can be added/subtracted from the damage.

<!-- -->

dmgtype [V_STRING](V_STRING "wikilink") <font color="red">**FIXME**</font> *Is this still all up to date?*
Takes a value such as

- `normal`
- `blast`
- `fire`
- `plasma`
- `laser`
- `particlebeam`
- `stun`

This is important as different types of armour are better against
certain types of insult. Also some damage types such as `stun` have
special meaning (i.e. they effect more than just armour&health points)

<!-- -->

weapon_mod [V_STRING](V_STRING "wikilink")
Example: `weapon_mod xxxxx`

List that contains all firemodes that are displayed/used when the ammo
loaded in weapon xxxxx (equals an item definition of xxxxx).

It also tells the game that this item can be used in weapon xxxxx

The weapon entry must come **before the ammo entry** in the ufo file.

## Some variable types for firedef

Firedefs are enclosed in a **weapon_mod** definition (see above).

Several of these variables are used in the hit calculation. The
attempted line of fire is modified using pseudo random numbers. For
direct fire modes the pitch (up/down) and yaw (left/right) angle has a
gaussian distributed variable added while thrown fire modes have a
random distribution.

**`accuracy = (1 - (accuracy ability / MAX_SKILL + weapon skill / MAX_SKILL) / 2) × wound penalty`**
**`direct angle = gauss × (spread × ((WEAPON_BALANCE + SKILL_BALANCE * accuracy) * injurymultiplier) × crouch`**
**`throw angle = random × 2.0 × (spread × (WEAPON_BALANCE + SKILL_BALANCE × accuracy)) × crouch`**
*`(`**`Note:`**` MAX_SKILL = 100, wound penalty = `<TODO>`, WEAPON_BALANCE = 0.5, SKILL_BALANCE = 1.0`*
*`if HP is less than 50% then injurymultiplier = 1.0 + INJURY_BALANCE * ((1.0 / (HP / maxHP + INJURY_THRESHOLD)) - 1) * MAX_SKILL / mind ability, otherwise injurymultiplier = 1.0; INJURY_BALANCE = 0.2, INJURY_THRESHOLD = 0.5)`*

spread [V_POS](V_POS "wikilink")
Example: `spread "pp yy"`

width of gaussian applied to attempted line of fire, in degrees (TODO:
check it really is degrees). First element affects pitch, second element
affects yaw. Lower values mean greater precision.

crouch [V_FLOAT](V_FLOAT "wikilink")
multiplicative modifier for firing when crouching. Lower values mean
greater precision. Crouching does not tend to help much with pistols,
but improves sniping prospects quite a bit.

dmgweight [V_STRING](V_STRING "wikilink")
The type and weight of damage this firedef uses. This is used with unit
resistance and armour protection values to modify final damage. A
firedef of type fire_medium will cause extra damage on a unit that is
more vulnerable to this type. See
[armour.ufo](UFO-Scripts/armour.ufo "wikilink")

time [V_INT](V_INT "wikilink")
The time units (TU) it takes to use this firemode.

shots [V_INT](V_INT "wikilink")
The number of shots fired. The particle cannon takes 1 unit of ammo for
5 shots when the "rapid shots" firemode is used.

ammo [V_INT](V_INT "wikilink")
The ammo used. The particle cannon takes 4 units of ammo for a single
shot charged blast.

delaybetweenshots [V_INT](V_INT "wikilink")
The delay that the weapon needs to play sounds and particles

The higher the value, the less the delay (1000/delay)

throughwall [V_INT](V_INT "wikilink")
This parameter defines the ability to shoot through a wall with this
firedefinition. The amount of throughwall will be the walls the firedef
will be able to penetrate. The damage will be decreased with every wall
of course.

name [V_TRANSLATION_STRING](V_TRANSLATION_STRING "wikilink")
shotorg [V_POS](V_POS "wikilink")
This can shift a muzzle vertically (first value) and horizontally
(second value) for the trace that is done on the server side.

projtl [V_STRING](V_STRING "wikilink")
impact [V_STRING](V_STRING "wikilink")
hitbody [V_STRING](V_STRING "wikilink")
firesnd [V_STRING](V_STRING "wikilink")
impsnd [V_STRING](V_STRING "wikilink")
bodysnd [V_STRING](V_STRING "wikilink")
bncsnd [V_STRING](V_STRING "wikilink")
impactattenuation [V_FLOAT](V_FLOAT "wikilink")
fireattenuation [V_FLOAT](V_FLOAT "wikilink")
You can define a *impactattenuation* and a *fireattenuation* value
([V_FLOAT](V_FLOAT "wikilink") between 0.0 and 3.0 (0.0 means that there
the sound is played at the given volume all over the level, 3.0 means
that is the sound is only hearable when the camera is very close to the
sound source.

sndonce [V_BOOL](V_BOOL "wikilink")
gravity [V_BOOL](V_BOOL "wikilink")
launched [V_BOOL](V_BOOL "wikilink")
rolled [V_BOOL](V_BOOL "wikilink")
reaction [V_BOOL](V_BOOL "wikilink")
delay [V_INT](V_INT "wikilink")
bounce [V_INT](V_INT "wikilink")
bncfac [V_FLOAT](V_FLOAT "wikilink")
speed [V_FLOAT](V_FLOAT "wikilink")
damage [V_POS](V_POS "wikilink")
spldmg [V_POS](V_POS "wikilink")
irgoggles [V_BOOL](V_BOOL "wikilink")
Is this an irgoogle?

rounds [V_INT](V_INT "wikilink")
How many rounds should this effect last. Used to keep incendiary
grenades and smoke grenades around. Each side turn is one round, so 2
rounds would make it last when the player fired it and the aliens' turn
only. Minimum is 2.

## Non-rectangular weapons

Sometimes weapon might have an empty space in the rectangular shape
where it would be nice to allow placement of other items. This can be
done only on tile level, so the usefulness only appears for larger
multiline weapons like rocket launcher or machine gun.

Shape keyword defines a shape of a rectangle, so on it's own no
non-rectanghular shapes are possible. On the other hand, you can specify
multiple shapes, thus forming slightly more complex shapes.

For example, if a shape is defined as "0 0 5 2", you would get a
rectangle, positioned at relative coordinates 0 0, 5 tiles horizontally
and 2 tiles vertically large. Let's say we have empty space at the upper
left and lower right tile, so to make those tiles usable for other
weapons we would do:

`shape "1 0 4 1"`
`shape "0 1 4 1"`

Notice how we have stacked two rectangles. First is shifted one tile to
the right (first "1"), and is only 4 units long and 1 unit high. Second
is placed one row lower ("1" in the coordinate y position), and also is
4 units long and 1 unit high, thus leaving one tile at the end usable.

Make sure to test such configurations, simple mistakes can lead to weird
behaviour in the inventory screens.

## Example

    item sniper
    {
        name        "_Sniper Rifle"
        model       weapons/sniper/sniper
        weapon      true
        type        rifle
        animationindex  1
        holdtwohanded   false
        firetwohanded   true
        shape       "0 0 5 2"
        center      "9 0 3"
        scale       1.05
        ammo        5
        reload      10
        price       5920
        size        30
        buytype weap_pri
    }

    item sniper_ammo
    {
        name        "_Sniper Rifle Magazine"
        model       weapons/sniper/sniper_clip
        type        ammo
        animationindex  0
        shape       "0 0 1 2"
        center      "0 0 0"
        scale       1.15
        price       190
        size        5
        buytype weap_pri
        dmgtype normal

        weapon_mod sniper
        {
            firedef
            {
                name    "_Snap Shot"
                skill   sniper
                projtl  bullet
                impact  bulletImpact
                hitbody null
                firesnd weapons/sniperrifle
                speed   0
                spread  "1.5 1.5"
                crouch  0.3
                range   250
                shots   1
                ammo    1
                time    12
                damage  "105 0"
                dmgweight normal_heavy
                reaction    true
            }
            firedef
            {
                name    "_Aimed Shot"
                skill   sniper
                projtl  bullet
                impact  bulletImpact
                hitbody null
                firesnd weapons/sniperrifle
                speed   0
                spread  "0.9 0.9"
                crouch  0.3
                range   250
                shots   1
                ammo    1
                time    18
                damage  "105 0"
                dmgweight normal_heavy
            }
            firedef
            {
                name    "_Headshot"
                skill   sniper
                projtl  bullet
                impact  bulletImpact
                hitbody null
                firesnd weapons/sniperrifle
                speed   0
                spread  "0.9 0.9"
                crouch  0.3
                range   250
                shots   1
                ammo    1
                time    24
                damage  "150 0"
                dmgweight normal_heavy
            }
        }
    }

## Links

- [Weapon_tables](Weapon_tables "wikilink")
- [Equipment](Equipment "wikilink")
- [Skills](Skills "wikilink")
- [Damage types](Damage "wikilink")
- [tweak weapons](Equipment/Tweak_weapons "wikilink")

[Category:Equipment](Category:Equipment "wikilink")
[Category:Weapons](Category:Weapons "wikilink")
[Category:UFO-Scripts](Category:UFO-Scripts "wikilink")
[Category:Skills](Category:Skills "wikilink")