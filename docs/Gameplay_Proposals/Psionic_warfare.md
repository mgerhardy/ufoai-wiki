This is a simplified outline of how psionics should work, inspired by a
longer proposal from Touchluck which can be read in the [talk
page](Talk:Gameplay_Proposals/Psionic_warfare "wikilink").

## Introduction

Psionic warfare will become available through research on live aliens
and [XVI](XVI "wikilink"). Players will be able to research a
psi-enhancing implant which allows their soldiers to access the alien
psionic network and carry out attacks. When connected to the psionic
network, soldiers are susceptible to psionic attack from aliens.

This document will outline research prerequesites, implant design, the
mechanisms governing psionic warfare in the battlefield and related UI
adjustments. For more detail on implant design and installation, see
[Proposals/Implants](Proposals/Implants "wikilink").

### Terms

- **psi-warrior**: psi-enabled Phalanx soldier
- **EMS**: Effective Mind Stat (Mind modified by Morale)

## Research

See [TODO/Roadmap#Tech_Tree](TODO/Roadmap#Tech_Tree "wikilink").

**Prerequisites:**

- Universal Serum
- XVI-related event or research (exact item to be determined later)
- 5 live aliens (must be retained throughout the research process)

## Implant

A psi implant is just a regular [implant](Proposals/Implants "wikilink")
that activates psionic powers for a soldier. We'll call that soldier a
psi-warrior. It will not effect the rest of his loadout.

## Psionic Warfare

A psi-warrior will be able to carry out psi-abilities on the
battlescape, but they will also be susceptible to psi-attacks from
aliens. Soldiers without the psi-enabling implant will not be
susceptible to psi-attacks.

The success or failure of a psi-attack will depend on the Mind stat of
the attacker and target, modified by the difficulty of the psi-attack
and the target unit's current Morale. This means that it will be easier
to carry out a difficult psi-attack on an alien with a low Mind stat. A
suggested equation for the Effective Mind Stat (Mind modified by
Morale):

`EMS = Mind * ( Current Morale / Total Morale )`

TU use for psi-abilities exposes a soldier to reaction fire in the same
way any other attack would.

*Note: We will need to rethink how the Mind stat increases and ensure it
is balanced.*

### Targetting

Some psi-abilities will not target specific aliens. These do not have
any targetting requirements and can be performed at any time during the
soldier's turn.

However, most psi-abilities will target a specific alien. These
psi-abilities will require that the psi-warrior is aware of the alien's
existence, either because they or a teammate has spotted them or because
the alien's existence has been revealed by another psi-ability.

### Psionic Power and Cooldown

Using a psi-ability will weaken a soldier's mental resistance (reduce
Morale points). A certain amount of Morale will be restored each turn,
but continued use of psi-abilities with no rest will, after 2-3 turns,
make a soldier very susceptible to alien psi-attacks, or could cause
them to panic, go berserk, etc.

The amount of Morale a soldier loses with each psi-attack is modified by
their Mind stat.

The effects of many psi-attacks scale depending on the EMS.

### Psionic Abilities (Phalanx)

**Read Network:** Scan psionic network to reveal alien presence. Weak
psi-warriors may reveal only estimates on numbers. Stronger psi-warriors
can reveal alien types, exact numbers, positions, equipment,
health/morale status and skills/abilities stats.

- Difficulty: Scaled (more info returned by better psi-warriors)
- Targetted: No
- Counter-attack Risk: None
- Technical notes:
  - Each alien will be tested individually, and information will be
    returned individually. So, an alien with a low Mind stat may return
    lots of information, but a psi-warrior may detect nothing more than
    the presence of an alien with a high Mind stat. Example:
  - Weak psi-warrior scans for alien presence. There are 5 aliens in the
    map: two Ortnoks, two Shevaar and a Taman.
    - Ortnoks are psionically weak, so the scan returns all the
      information about them.
    - Shevaars have medium Mind stats. One Shevaar is a bit weaker, so
      the scan returns their position and health/morale status. The
      other is a bit stronger, so the psi-warrior is able to detect
      them, but does not know their precise location.
    - The Taman has a very high Mind stat, so the scan does not even
      return that it exists. The player gets *no information* about this
      missing link.
    - The psi-warrior believes there are 4 aliens on the map, it can
      identify the location of 3, and has full details of 2.
- UI notes:
  - An ambiguous alien location model or particle will be needed to
    indicate a known alien location without knowing the alien. Another
    option is to not indicate an exact position, but all the center on
    alien function through the psionic hud window to approximate the
    location if alien type not identified (ie - they can tell roughly
    where it is, but not exactly).

**Read Node:** A Read Network attack that only targets a single, known
alien. The attack is stronger because it is more focused and the
psi-warrior is likely to retrieve more information than it did with Read
Network.

- Difficulty: Scaled
- Targetted: Yes
- Counter-attack Risk: None

**Degrade Node:** Attempt to weaken a target's Morale and cause it to
panic. Stronger psi-warriors are able to cause more Morale-loss.

- Difficulty: Scaled
- Targetted: Yes
- Counter-attack Risk: Medium
- UI Notes:
  - When a target's Morale drops to 0, their status in the psi-window
    should say "Link Broken".

**Mind Blank:** When a target's Morale drops to 0, their mind can be
blanked by an advanced psi-warrior. This will permanently sever their
connection to the hive mind, turning them into a civilian.

- Difficulty: Hard
- Targetted: Yes
- Counter-attack Risk: High (if performed on a target that hasn't
  reached 0 Morale)
- UI Notes:
  - Target should disappear from the psionic HUD window.

**Corrupt Link:** Corrupt target's connection to the network, causing
them to interpret all units as enemies. It will also reduce a target's
Morale to some degree.

- Difficulty: Medium
- Targetted: Yes
- Counter-attack Risk: High

**Mind Control:** Take control of a target. Each turn control is not
severed, the psi-warrior will start with 50% of TUs and lose a set
number of Morale points, modified by the Mind stats of both parties.

- Difficulty: Very Hard
- Targetted: Yes
- Counter-attack Risk: High

### Psionic Counter-attacks (Alien)

Some alien units will utilize psi-attacks (psi-specific units such as
the [Psi-Amplifier](Proposals/Alien_Bestiary "wikilink") and a new
advanced Taman). In normal play, alien psi-units will use Degrade Node,
Corrupt Link and Mind Control.

However, whenever a Phalanx psi-warrior performs a psi-attack, they risk
provoking a counter-attack. If an alien's EMS is higher than a
psi-warrior's, the psi-warrior will suffer a **Degrade Node** attack.

### Psi-controlled Aliens

Aliens under mind control will not be targetted by Phalanx soldiers
using reaction fire.

### XVI-effected Units

Civilians or soldiers on the battlescape that have been infected with
XVI (when that is implemented) will appear just like aliens for all psi
purposes.

### HUD

A psionic hud window will need to be made that will allow the soldier to
perform psi-abilities and access psi-related information. As a temporary
solution for the current HUD, I suggest the following image.

![<File:ui_psionics.jpg>](ui_psionics.jpg "File:ui_psionics.jpg")

- Firemodes: When clicked on, it will give a list of firemodes for
  psionics. Click on the firemode and then target the alien (no firing
  lines drawn).
  - Untargetted modes should have a button within the window to execute.
  - When a psionic power which can be targeted at a specific unit is
    clicked on, the cursor should change.
- Network: When clicked on, it will list all known aliens with whatever
  information is available.
  - Click for more detailed information if stats/equipment were
    accessed.
  - It would also be nice to be able to target an alien through this
    window.
  - Click anywhere on window to go to the alien (important to know which
    Taman is in front of your soldiers, for instance).
- Ideally, we would also have a Battlescape log somewhere that could,
  for instance, log the fact that a soldier's psi-attack failed and they
  suffered a counter-attack.

## Roadmap

A suggested outline for completing this proposal in stages.

### Mark I

A psi-implant can be researched after Universal Serum and Enemy on
Earth. That psi-implant can be installed, activated and deactivated at
the Hospital. In combat the soldier can perform Read Network (to
identify alien numbers, location, type and, if possible, morale/health)
and Degrade Link.

Tasks:

- [Implants](Proposals/Implants "wikilink") completed
- HUD support for psionic firemodes and network
- Artwork for psi implant
- Research text for psi implants
- Code for psionic battle
  - Effective Mind Stat (Mind modified by MOrale)
  - Degrade Node
  - Read Network (basic information)

### Mark II

Improve and balance the Mind stat increase. Implement alien
counter-attacks.

Tasks:

- Balancing
  - Ensure not every soldier is good at Mind, that only a few soldiers
    can improve above a certain limit.
  - Ensure there is a reasonable cap to Mind, so that no soldiers can be
    over-powered.
- Code for psionic battle
  - Implement counter-attack risks for psi-attacks.

### Mark III

Implement support in alien AI for psi-empowered aliens which can perform
psi-attacks during their turn and not just in response to an attack.

Tasks:

- Artwork
  - Special psi-enhancing alien that is very powerful
  - Particle effect that shows when a soldier or alien excutes a
    psi-attack.
- Code for psionic battle
  - Support alien AI that uses Degrade link
  - Psi-enhancing alien should boost all aliens' Mind stat when present
    on battlefield and improve recovery rate for Morale

### Mark IV

Implement enhanced Read Network/Node and all other psi-attacks.

Tasks:

- Artwork
  - Particle effect that shows an alien under enemy control.
- Code for psionic battle
  - Full Read Network/Node capabilities
  - Mind Blank
  - Corrupt Link
  - Mind Control

### Mark V

Proper animations to illustrate psionic attacks, defenses, status, etc.

[Category:Proposals](Category:Proposals "wikilink")