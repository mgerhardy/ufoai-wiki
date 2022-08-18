
The proposals on this page are mostly obsolete. The weapons were heavily
rebalanced for 2.5 and the heavy skill was removed. But there is no
reaction ability as detailed below and the actual damagetypes vs. aliens
matchup may not match the specification below.
--[H-hour](User:H-hour "wikilink") 14:14, 7 October 2012 (SAST)

## What's the goal?

There are three things I want to accomplish with these changes. First, I
want to encourage a match between skill-type and tactical-role. This
will encourage the player to take and train a diverse set of skills so
that they are prepared to face a diverse set of tactical problems in
battle. It should also increase the benefit of a player understanding
and employing several different strategies.

Second, I want to diversify the damagetypes/resistances so that more
weapons are relevant late in the game as well as in multiplayer. I also
want to simplify the damageweights system so that the player can easily
and clearly understand how a given weapon will impact a given
soldier/alien/armor (currently the damageweights information is hidden
from the player).

Third, I want to simplify reaction fire and isolate it as a trainable
ability. I hope this will make it more clear to the player his chances
in any reaction fire match-up. I want to do this by making a new
Reflexes ability which is separate from Speed. By doing this, there may
be future possibilities we can explore, such as aliens with high TU but
poor reaction fire (or the opposite), using a reflexes ability to effect
a soldier's chance at spotting an enemy when the visibility system is
implemented, implants that improve reaction/vision rather than general
speed, etc.

## The Changes

### Skills/Weapons

The following changes are designed to encourage a link between a Skill
and a particular tactical situation. In any given combat problem, a
particular skill ought to offer a more or less effective way of
resolving the problem. Here is a rough outline of the skill-situation
matchup:

*Close*: Indoors and other close-quarters situations where force must be powerful and quick, but not necessarily accurate.
*Explosive*: Combat matchups where indirect fire or splash damage are most effective (enemies behind walls or groups of enemies).
*Assault*: Mobile assault manuevering, competency at mid-range against a variety of enemies, and squad support where soldiers may need to fire and find cover.
*Sniper*: Long-range encounters.

To achieve this, I suggest the following changes:

1\. Remove the Heavy weapon skill (redistribution of these weapons
below).

2\. Make all aimed shot firedefs use the Sniper weapon skill. Make all
snapshot, burst or automatic firemodes use the Assault weapon skill.
This would have the effect of making a dedicated Sniper's "snap shot"
mode less effective, increasing his role as a slow, patient killer. It
would also narrow the Assault specialist to be more of a skirmisher
because it would be more important to reduce the distance between them
and an enemy. The downside would be an additional layer of complexity
for the player. They will no longer be able to think in terms of
weapon=skill, it will now be firemode=skill, which may seem
counter-intuitive at first.

3\. Reduce the distance of the flamethrower (3 tiles) and make it a
Close weapon skill to give close specialists a powerful early-game
weapon.

4\. Remove the burst firemode for the grenade launcher. It is
overpowered, particularly in the early-game. A cluster munition could be
introduced in the late-game with a new tech (plasma, perhaps) if
desired.

5\. Turn the Plasma Blaster into a shotgun-like Close skill weapon with
poor accuracy/range but high damage. Will require changes to the
research text, but the text already has some inaccuracies.

Given these changes, the weapon distribution by skill set would be:

*Close*: pistols, smg, shotguns, plasma blaster, blades, stunrod, flamethrower, stungrenade
*Explosive*: grenades (except stun), grenade launcher, RPGs
*Assault*: (snap shots for all rifles and sniper weapons), machineguns, heavy laser, plasma weapons
*Sniper*: (precision shots for rifles), sniper, coilgun, needler, bolter

### Damage Types

Two general ideas for changing how damage types work. The first is to to
implement particular characteristics for damagetypes, so that each
damagetype has its own strength and weaknesses. This can be done
entirely through the UFO scripts and requires no back-end changes.

The second change is to remove the dependence for normal_blast,
normal_heavy, normal_light etc. All soldiers, aliens and armor should
only have resistance values for the damage types
(normal,fire,laser,plasma,pbeam,etc) and resistance values for the
sub-types (light, medium, heavy, blast, spray). This will allow the
player to get an accurate view of the power/resistance of any
weapon/armor at a quick glance. But it requires a change in the backend.

The idea of the following setup is to ensure that each damagetype is
relevant throughout much of the game. It is based on the assumption that
we will have more aliens including dedicated mechanics and organics. See
the alien bestiary: [Proposals/Alien
Bestiary](Proposals/Alien_Bestiary "wikilink")

`Normal: medium damage vs. all enemies`
`Fire: strong vs. organics, weak vs. mechanics`
`Laser: medium vs. all, weapons have high accuracy/weak power`
`Plasma: medium vs. all, weapons have low accuracy/strong power`
`ParticleBeam: strong vs. mechanics, weak vs. organics and lightly armored mechanics`
`Shock: medium vs. all`
`Stun (electric): strong vs. mechanics, weak vs. organics`
`Stun (gas): strong vs. organics, weak vs. mechanics`

The sub-types of damage would work roughly like this:

`light: medium vs. organics, weak vs. mechanics and any armor`
`medium: strong vs. organics, medium vs. mechanics and light armors`
`heavy: strong vs. organics, strong vs. mechanics and light/medium armors`
`blast: strong vs. organics, strong vs. mechanics and all armors`
`spray: strong vs. organics, weak vs. mechanics and any armor`

### Abilities

A sketch of how the abilities currently work or how I think they ought
to work.

Strength (not implemented)


\- The weight a soldier can carry (not currently implemented)

\- Soldier gets a weight value up to a certain limit, at which point the
soldier is considered "encumbered". When encumbered, additional weight
reduces the soldier's maximum TUs.

\- The ability increases each time an encumbered soldier fires his
weapon or makes a psi-attack. TUs spent moving do not count because it
would be easy to abuse.

Accuracy (implemented)


\- Improves soldier accuracy for any weapon or firemode.

Mind (partially implemented)


\- Effects soldier morale and psionic attack strength (psionics not
implemented)

\- Battle experience increases mind strength. Early missions should
improve mind quickly, while latter missions improve it slowly. For
instance, a new recruit should have weak mind, but after a few missions
they should settle in and mind increases should come more slowly.

\- Special events could provide special bonuses for mind: being wounded,
surviving a mission in which many soldiers die, killing an enemy at
close range, etc.

\- Psionic-related mechanics to be decided later when the psionic system
is in place.

Reflexes (not implemented)


\- Higher values improve chance to use reaction fire. Could also effect
chance to spot an enemy.

\- Use of reaction fire increases reflexes. When visibility system
implemented, gaining first sight of an alien could also provide a small
boost.

\- Distance to target could effect reaction fire bonus. A reaction shot
taken from a long distance could be worth less than a reaction shot
taken closely. This could be a disincentive to abusing the system while
keeping soldiers at a safe distance.

## Implementation (Spring 2012, 2.5-dev)

The following will outline the changes made for players to track and
some of the concepts behind them.

### Sniper Weapons

Unit is less maneuverable, but more deadly when properly set up.
\- Damage and accuracy increased for all aimed shots (one shot - one
kill as much as possible).

\- TU cost of all firemodes and reloading increased.

\- Accuracy increase when crouched is more exaggerated than other
weapons.

\- Snap shot accuracy is very poor due to weapons being large and
unwieldy

**Sniper Rifle**: Squad marksman rifle. Minor accuracy trade-off for
less TUs spent firing/reloading.


\- TU for Aimed Shot increased to 20

\- Avg Damage increased to 130

\- Ammo capacity increased to 8

**Electromagnetic Rifle (Bolter)**: Quintessential sniper rifle. Very
accurate and deadly, but huge TU costs. As an early research item, it
should be a good step up against armor.


\- TU for Aimed shot increased to 28

\- TU for reload increased to 20

\- Avg Damage increased to 140, damagetype set to normal_heavy

\- Ammo capacity reduced to two

**Coilgun**: Powerful squad marksman rifle. Minor accuracy trade-off for
power, but more TUs will be sent firing/reloading than Sniper Rifle.


\- TU for Aimed Shot increased to 24

\- Avg Damage increased to 160, damagetype set to normal_heavy

\- Ammo capacity increased to 4