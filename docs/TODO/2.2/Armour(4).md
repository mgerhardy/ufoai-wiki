## Implementation

- armour applying effect should be done in G_Damage()/g_combat.c;
  because we pass used fireDef_t as param\[in\] into G_Damage() I would
  suggest to put both dmgtype and dmgweight into fire definition (few
  additional lines in script - dmgtype per firedef, not per ammodef, but
  greately reduces needed code work)

  - correction of myself: not needed, the object, which uses given
    firedefinition (the ammo) can be easily taken off using int obj_idx
    member of fireDef_s struct, which states exactly the thing we are
    searching for; so dmgtype in ammo definition is perfectly correct
    and easy to use--[Zenerka](User:Zenerka "wikilink") 22:17, 7 August
    2007 (CEST)

- objDef_s struct - new member, dmgweight (dmgtype is already there),
  also change/update/remove armour-related protection/hardness

- script parser update for both fire definitions (needed to parse
  dmgweight too) and armours

- new script definitions for armours

- include dmgweight and verify dmgtype for all fire definitions

- because armour does not have "health", do not show "armour points" for
  soldiers anywhere

## Concept

This article describes the functionality for armour in UFO:AI.

Armour is modelled as a reduction in damage from various attacks. When
an attack hits an armoured actor, that actor takes damage equal to the
damage value of that attack minus the defensive modifier of the armour.
A minimum amount of inflicted damage may be imposed.

### Example 1

An alien fires with a plasma pistol on a PHALANX soldier who is wearing
a medium armour. The plasma pistol does 30 damage and the armour has a
damage reduction against plasma pistols of 18. The alien hits the
soldier, so the soldier takes 30 - 18 = 12 damage.

### Example 2

A PHALANX soldier uses a grenade launcher on a group of three aliens.
However, the grenade bounces, and lands roughly in between an alien and
a civilian. When the grenade explodes, first splash damage calculation
takes place. The alien takes 35 damage from the blast, the civilian
takes 25. At this point armour calculation happens. The alien, whose
armour has a damage reduction of 20 against that grenade, takes 35 - 20
= 15 damage. The civilian doesn't wear any armour, and so takes the full
25 damage.

## Damage reduction values and scripts

The amount of damage a piece of armour reduces is defined by a superset
of the damage types. The reasoning behind this is that because even
though a bullet from a sniper rifle does the same kind of damage as the
bullet from a handgun, the calibre and firing power differ greatly
between the two. An armor that defends well against the handgun bullet
may be ineffective against the sniper bullet, but that doesn't mean ALL
armors are equally relatively ineffective against the sniper bullet. By
defining the damage reduction by more categories than there are damage
types, we can model this. Each damage type is associated with a number
of categories (one or more). Every ammunition must have a definition
that determines what category it belongs to, and it must have one such
definition for every weapon it can be used in. Care should be taken that
a piece of armour is generally equally effective against all categories
that belong to a damage type, as compared to categories that belong to
another damage type. For example, an armour that is especially good
against particle beam weapons should, in general, have high damage
reduction values for all particle beam categories. While the values can
vary, they should all be appreciably high, without exception.

Note that this implementation effectively renders the definition of
individual damage types obsolete as the effectiveness against damage
types is made implicit.

Here is an example of the definitions involved:

    item laserrifle_ammo
    {
     dmgtype laser
     weapon_mod laserpistol {
      dmgweight laser_light
     }
     weapon_mod laserrifle {
      dmgweight laser_medium
     }
    }

    item assault_ammo
    {
     dmgtype normal
     weapon_mod assaultrifle {
      dmgweight normal_medium
     }
    }

    item smg_ammo
    {
     dmgtype normal
     weapon_mod smg {
      dmgweight normal_light
     }
    }

    item light
    {
        ...
        protection
        {
            normal_light 10 //(normal damage weapons - light)
            normal_medium 8 //(normal damage weapons - medium)
            normal_heavy 5 //(normal damage weapons - heavy)
            laser_light 12 //(laser damage weapons - light)
            ...
        }
        rating_normal 30 //(overall judged effectiveness when dmgtype normal)
        rating_plasma 10 //(overall judged effectiveness when dmgtype plasma)
        rating_laser 25 //(overall judged effectiveness when dmgtype laser)
        ...
    }

## Representation in-game

Because armour is no longer effective against a whole family of
ammunitions at a time but rather against the individual categories, we
can not give hard numbers in the UFOpaedia or in the equipment screen,
as that would result in information overload. Instead, the script files
define ratings for general effectiveness against the damage types, for
example rated on a scale of 1 to 100. These ratings have no impact on
the actual armour performance, but they are displayed graphically by
means of a set of bars that are filled up depending on the manually
defined rating. A player can then use these bars to compare armour
effectiveness. Clearly, the ratings must represent the actual
performance of the armour.

## Armour damage and failure

The game abstracts from armour damage or outright armour failure. It is
meaningless to model these aspects because of the following reasons:

- Easily damaged armour will be used by neither the aliens nor PHALANX.
  It will take several shots by any weapon to render a suit of armour
  less effective, and after several shots the soldier wearing the armour
  is unlikely to still be standing.
- Armour can not be worn or removed during combat. As such, armour from
  a dead or wounded soldier is irrelevant for the rest of that mission.
- Item repair outside of a mission is tantamount to micromanagement, and
  therefore best abstracted from.

[Category:Contribute](Category:Contribute "wikilink")
[Category:TODO](Category:TODO "wikilink")
[Category:Development](Category:Development "wikilink")