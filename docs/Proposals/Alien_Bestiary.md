## Alien Bestiary

Originally ported from a forum post by BTAxis:

- First we need to determine what kind of enemies we want to have in the
  game, in terms of what the role of the enemies is in tactical
  engagements, what sort of hazard they represent to the player (and by
  extension, what sort of tactics they entice from the player), how they
  behave and how they complement the other enemy types.

<!-- -->

- Second, we have to fill in the details for the enemies. Once we know
  what an enemy is supposed to do in the game, we can talk about what it
  should look like, what sort of innate abilities it should have, etc.

## What we have

This section lists the aliens that are either already ingame or are in
an advanced stage of planning. What you read here should be considered
set in stone.

Taman

- Role: Physically weak enemy with somewhat sub-average combat
  abilities, but with lots of mental capacity. Serves as a weak enemy
  for the early game, and a dangerous psionic foe for the later game.
- Implementation: Done.

Ortnok

- Role: Tough and strong, this enemy is a foot soldier fighting at the
  front. It should be used by the AI as a shock troop, preferring a
  direct assault over careful tactics.
- Implementation: Done.

Shevaar

- Role: The Shevaar is the aliens' secondary infantry combatant. It is
  meant to be fast, with a lot of TUs available for moving and firing.
  It should also have different inherent armour than the Ortnok, so
  different weaponry works well on it.
- Implementation: Done.

Bloodspider

- Role: The Bloodspider is more or less to UFO:AI what brainsuckers were
  to X-COM Apocalypse: small, fast and highly dangerous if you let them
  get too close. They don't have ranged weaponry, but are dangerous in
  melee. Their primary role is to harvest organic material though, so
  they aren't meant for combat.
- Implementation: Done.

Combat Bloodspider

- Role: An upgrade of sorts for the Bloodspider. The Bloodspider is a
  harvesting tool with offensive abilities, but this version is a
  straight up combat droid. It should be faster, tougher and deadlier
  than the regular bloodspider, and it should appear somewhere in the
  mid game.
- Implementation: Done.
  - *Note:* Current implementation has it at same speed as original
    bloodspider and it only appears on XVI/Harvesting missions.
- Campaign usage: Mid-game unit. Appears frequently.
- AI Concept: Should try to catch the soldiers in alleyways, inside
  buildings, etc. When near, it should rush at the soldiers.

Hovernet

- Role: Hovernets are flying, mechanical units. They have limited
  firepower compared to ground based units, and they serve mainly as
  scouts and air support for other aliens.
- Implementation: Done.

Combat Hovernet

- Role: Another aerial unit for the aliens but this one is built for
  combat.
- Implementation: Done.
  - *Note:* Current implentation is just a stronger Hovernet, but we may
    some day want an entirely different alien.
- Campaign usage: Mid- to late-game unit. Very common in all missions
  except harvesting and XVI.
- AI Concept: Prefers outdoors. Default attack/defense.

Alien wormhole device

- Role: It's not an alien as such, but it behaves like one in base
  missions. The wormhole device channels the psionic abilities of the
  hive mind on the other side of the wormhole, so while it can't move or
  attack normally, it can use psionic attacks in tactical combat.
- Implementation: Artwork done and in alien base, but no psionic
  effects.

## What is planned

This is my personal idea of how the bestiary could be extended. The goal
is to provide a number of enemies that require different approaches to
beat, without going overboard and making too many similar types.

Breeder

- Role: Breeders are half-organic, half-mechanical vehicles meant to
  infuse victims with XVI. In battle their primary role is to find
  civilians and turn them into alien drones, but when attacked they can
  retaliate with strong psionic attacks as well.
- Implementation: Rough sketch. Open to improvement or complete
  redesign. Note: 2x2 unit!

Alien tank

- Role: The purpose of this unit would be to be very tough and heavily
  armed. It's an enemy to attack from cover, because a direct engagement
  would result in almost certain death. It should be a 2x2 unit, so it
  can't enter confined spaces. It should also be mechanical. Mode of
  movement could be tracked, wheeled or legged, whatever works. Think
  ground-based, alien UGV.
- Implementation: None.
- Campaign usage: Mid- to late-game unit. Base attacks, terror attacks.
- AI Concept: Prefers outdoors. Should be very dangerous to attack
  directly. Perhaps it has limited peripheral vision or turning requires
  a lot more movement points than it would for a typical unit. Default
  attack/defense.

Psi-amplifier

- Role: A unit which amplifies the psionic powers of other units but is
  very weak itself. One idea is to have a floating, gaseous creature
  which might have a brain but little ability to hurt anyone.
- Implementation: None.
- Campaign usage: Late-game unit. Common at terror attacks and in bases.
- AI Concept: Should run from enemies and try to stay away if possible.
  Player must "corner" them.

[Category:Proposals](Category:Proposals "wikilink")