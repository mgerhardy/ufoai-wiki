## General

This tutorial only describes one possible way to animate already
existing characters.

Please keep in mind that you not only have to animate the character mesh
itself, but also the [tags](Modelling/Tags "wikilink").

## 3DSMax

To animate your character in [3DSMax](Modelling/3DSMax "wikilink") you
have to create a biped system. After the system was created, open it's
properties. There you can load our file that holds the animations for
e.g. soldiers, civilians and so on.

Now select the bip object, go to the movement-\>biped tab and change to
figure mode to bring the bip object into it's initial form (you can even
load a fig file to do this from already existing shapes).

After you've done this, select the head mesh and apply the physique
modifier, click attach and select the head bip object.

## Animation

Character animations are read from **anm** files with the same basename
as the [md2](md2 "wikilink"). e.g.:

    modelname.md2
    modelname.anm

### .anm file format

The format of these **anm** files is as following. For each animation
sequence you have a line consisting of ...

- animation name
- start frame
- end frame
- fps

... that are separated by whitespaces.

#### Example

    death1              0       30      18
    dead1               30      30      18
    death2              31      61      18
    dead2               61      61      18
    death3              62      94      18
    dead3               94      94      18

    stand0              189     190     1
    walk0               191     206     22
    cstand0             209     210     1
    cwalk0              212     227     15

### List of needed animations for a character

Characters are soldiers and aliens (as opposed to civilians) that can
perform actions like shooting with different weapons.

- `stand0, stand1, stand2, stand3`
- `walk0, walk1, walk2, walk3`
- `cstand0, cstand1, cstand2, cstand3`
- `cwalk0, cwalk1, cwalk2, cwalk3`
- `death1, death2, death3`
- `dead1, dead2, dead3`
- `run0`
- `move_*, shoot_*, cmove_*, cshoot_*` (replace \* with the following
  list)
  **Attention**: "**`*move_*`**" is actually an "**`idle`**" animation
  and has nothing to do with moving around.
  - `rifle`
  - `biggun` - Fixme: What is the difference to "rifle"?
  - `melee`
  - `pistol`
  - `pistol_d` (akimbo)
  - `grenade`
  - `item`
  - `rpg`
- `stand_menu`
- `stand_still`
- `panic0`

#### Meaning of "c"

Every action starting with a "`c`" is for the same action but in
crouched state.

#### death and dead animations

- `death#` - dying animation
- `dead#` - The animation of the dead body (i.e. the body lying on the
  floor). In most cases the last frame of the matching "death" animation
  (effectively making it a non-animation ;))

You may have also noticed, that there are various animations for death.
We use three different death animations for each model. So keep in mind,
that all of your models will need this three death animations if you
build animated models for UFO:AI. The same counts for all other listed
animation names - they must be available in the file.

#### Meaning of the numbers

The number in the animation names (except for the '`death`' and '`dead`'
ones) is the one defined with `animationindex `<number> in the
[weapon_\*.ufo](UFO-Scripts/weapon_*.ufo "wikilink") files.

- **`0`** - items (mostly the 'unusable' ones like ammo), grenades
- **`1`** - rifles
- **`2`** - pistols, and 'active' items (e.g. medikit, irgoggles)
- **`3`** - rpg (shoulder mounted weapons)

You can also have a look at our files for the characters.

- . The head models don't need any files. They inherit the rotation from
  the tag file (e.g. ) (the tag-files must have the same base name as
  the body).

Also see the [list](Modelling/List_of_Animated_Models "wikilink") of
animated models.

#### Bip-Files

Bip files are for easy transforming animation and bones to your model.

## Links

- [Modelling](Modelling "wikilink")

-

[Category:Contribute](Category:Contribute "wikilink")
[Category:Modelling](Category:Modelling "wikilink")