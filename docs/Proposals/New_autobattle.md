This page describes yet another proposal for auto-resolving missions.

## General idea

the system will be based on player's previous statistics, so it will
follow his style. The initial statistics should be gathered before the
"autobattle" button become available. The statistics must be saved with
the game, so it probably will break savefile compatibility. The
autobattle results will be slightly worse than average stats, and it
will also contribute to the statistics, so if player will stop playing
missions manually, his results will gradually become worse.

Plot missions do not contribute to the stats.

## Gathering statistics from the mission

All numbers gathered from battle should be normalized, so that we could
scale it easily to the conditions of needed mission.

The normalized number of turns it took to end the battle.

    NormNumbOfTurns = NumbOfTurns * NumbOfPHALANXSoldiers / NumbOfAliens / SizeOfMap

The normalized number of shots (for every weapon type DISCUSS)

    NormNumbOfShots = NumbOfShots / NumbOfTurns / NumbOfPHALANXSoldiersWithThisWeaponType

And the normalized amount of damage dealt by these shots

    NormAmountOfDamage = AmountOfDamage / NumbOfShots

The normalized number of wounds (PHALANXS soldiers being shot by aliens.
one hit - one wound) (for every primary weapon type DISCUSS)

    NormNumbOfWounds = NumbOfWounds / NumbOfTurns / NumbOfPHALANXSoldiersWithThisWeaponType

The stats are saved from, well let's say 10 last missions. After the
initial stats are gathered, every new mission will replace the oldest.
This will represent the change in player's preferences while he gains
access to the new equipment. (Or we can just make a weighted average:
the most recent mission goes with the weight, let's say, 0.6, while the
previous average with 0.4. This way the contribution of every battle
will gradually decrease with time.)

## Calculating autoresolve

The main thing: NO DICE ROLLS PLEASE! The result of the mission is an
important thing to just use the random.

From now on we operate with averages, calculated as arithmetic mean of
the gathered stats. As I mentioned before, the averages are slightly
lowered (well, technically speaking, they are raised, as lengthier
battles, more ammo spent and more damage sustained are worse) by a fixed
fraction in order to give a player a stimulus to play missions manually.

First, we calculate the length of the battle

    NumbOfTurns = AverNumbOfTurns / NumbOfPHALANXSoldiers * NumbOfAliens * SizeOfMap

So the battle will be longer if we have less soldiers, more enemies and
bigger map

Next, we iterate through the soldiers, calculating how many shots he
made, and how many wounds he got. We use the averages from the
statistics that corresponds to the primary weapon type used by this
soldier.

    NumbOfShots = round(AverNumbOfShots * NumbOfTurns)
    NumbOfWounds = round(AverNumbOfWounds * NumbOfTurns)

If the calculated number of shots is more than the amount of ammo
carried by this soldier, he is considered dead. Equip your soldiers
better! The NumbOfShots is then lowered to the amount of ammo for later
calculation of AmountOfDamage (even dead soldiers can have their killing
score, so that we can give him his medal posthumous).

Now we calculate the amount of damage dealt by this soldier

    AmountOfDamage = AverAmountOfDamage * NumbOfShots

This value will later be used to distribute killing scores:

    NumOfKills = round_up((AmountOfDamage / TotalAmountOfDamage) * NumbOfAliens)

We round things up to make sure that we do not have any orphaned bodies
in the end, but we also need to check that the TotalNumOfKills doesn't
exceed NumbOfAliens. This also means that some unlucky soldiers won't
have as much kills as they deserve. Well, that's life.

Then we calculate the amount of damage he sustained. I think the simple
rotation through enemies will suffice. Aliens are considered to damage
soldiers in turn with their primary weapon. If the amount of damage is
more than soldier's HP, well, you know the answer.

The number of killed civilians is in direct connection with the length
of the mission

    KilledCivs = NumbOfTurns * SomeMagicCoefficient

Aliens also fire their guns, but here we need this only to reduce the
amount of recovered equipment, so the formula may be less elaborate

    FiredShots = NumbOfTurns * SomeOtherMagicCoefficient

If every soldier is dead, the mission is not successful, and player
needs to replay mission manually. Otherwise - it's win.

All the results are fairly generated by now: the soldiers fired some
ammo, got kills (also exp), sustained some damage (probably died), saved
(or not) some civilians, and recovered items. The lowered averages go
into the statistics the usual way.

There is still an issue for an empty stats for some weapon type. Or
\[near\]zero stats. With this system the soldier with zero stats won't
suffer any damage, and also won't fire any ammo, which automatically
means that he'll survive. That alone is not a bad thing, but victory
condition shouldn't consider such a soldier - he's just a bystander. So
this special case must be covered:

    if (TotalAmountOfDamageDealtBySurvivors == 0) you lose

But even with this condition the system is exploitable for cheaters:
they can staff their ground team with f.i. just rocket launchers, with
very low (but not zero) AverNumbOfShots, decent AverAmountOfDamage and
zero AverNumbOfWounds. That can be covered in second special case check:
we see if the amount of dealt damage is even close to the total HP of
the alien team

    if (TotalAmountOfDamage < TotalHPOfAliens * SomeThirdMagicCoefficient) you lose

Third magic coefficient should be about 0.5 I think. It's not that
important anyway, as it's just a protection from cheaters.

## Things still not covered

- As you can see, I still use two important magic coefficients.
  Probably, they should be replaced with something more real.
- Taking aliens alive. I do not know the mechanics of knocking aliens
  out. Is it non-lethal damage? Then it's easy: if the soldier scores a
  kill because of AmountOfDamage which is dealt from the non-lethal
  weapon - it's a capture. But I'd rather think that soldiers will have
  non-lethal weapons as secondary, which brings me to the last one:
- Firing secondary weapons. Pistols and such. Of course the amount of
  damage dealt from it is negligible (or you are a really bad player),
  but you still need to fire some ammo.