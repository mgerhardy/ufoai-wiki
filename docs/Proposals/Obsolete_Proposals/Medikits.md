## Wounds and Medikits

This article describes the system of soldier wounds, bleeding and the
use of medikits as per official design. The purpose is to create a
realistic yet simple system that allows players to tend to the wounded
on the battlefield without unbalancing the game.

It is assumed soldiers will almost always be wounded before they are
killed; weapon and armour balancing will have to ensure that this is the
case. In general weapon damage should be lowered; the reduction in
killing power is compensated by bleeding.

## Wounds

A soldier, when taking damage, will also be wounded. As it is currently
not possible to determine where the soldier was hit, the location of the
wound will have to be randomized, with each body part having a set
chance of getting the wound. This chance may be subject to factors such
as armour and implants. The possible locations are head, torso, arms and
legs. There is no distinction between the right and left limbs.

Each wound inflicts a penalty on the soldier, depending on which body
part is wounded.

- Wounds on the arms reduce accuracy with all weapons, and increase TUs
  needed to shoot.
- Wounds on the legs increase the amount of TUs needed to move.
- Wounds on the torso increase the amount of TUs needed for reaction
  fire.
- Wounds on the head decrease
  [visibility](Gameplay_Proposals/Visibility "wikilink") and accuracy
  with all weapons.

Each wound also bleeds, steadily taking health from the soldier until
the battle is over, the wounds are healed or the soldier dies. Bleeding
takes health directly from the health bar; there is no "second" health
bar of any kind.

Wounds treated with a medikit do not disappear. Instead they are
considered "treated". A treated wound does not bleed and only incurs
half of its normal penalty. However, treated wounds can only be fully
healed by spending time in a PHALANX base hospital. A soldier with
wounds that is sent out on a new mission will start that mission with
the penalties associated with those wounds.

When the player wins a mission, all untreated wounds will be
automatically treated.

Aliens are subject to wounding just like humans, but the specific race
of aliens may affect the chance of taking wounds, the penalties and the
rate of bleeding.

## Functions of the medikit

The medikit has three uses: treatment of wounds, recovery of morale and
revival of stunned actors. All three functions draw from the same
ammunition pool, for simplicity. Each of these functions is a separate
firemode on the medikit. Note that the medikit may not be used on
robotic targets for any purpose.

### Treatment of wounds

Each use of this firemode treats a single wound on the target actor.
Wounds are treated in the order they were inflicted. When the wound is
treated it ceases to bleed and its penalties are halved. In addition,
the actor being treated recovers a small amount of health. This firemode
can not be used on actors that have no untreated wounds.

### Recovery of morale

Each use of this firemode will raise the target's morale by a fixed
amount. Useful to prevent soldiers from panicking.

### Revival of stunned actors

When used on a friendly target, each use of this firemode will remove a
fixed amount of stun damage. Once stun damage falls below health, the
actor is revived. When used on a stunned alien target, this firemode
will actually increase stun damage, keeping the target sedated. However,
this function may not be used until [Live
Alien](Research/Live_Alien "wikilink") has been researched.
Civilians count as friendly targets.
This firemode may not be used on conscious enemy targets.