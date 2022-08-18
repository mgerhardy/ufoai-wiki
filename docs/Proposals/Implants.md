## Introduction

Soldiers can be surgically equipped with implants at the hospital to
augment or manipulate their abilities. Once installed in the hospital
they can only be removed at the hospital and, when removed, can not be
salvaged.

There are three types of implants: those that temporarily alter a
soldier's chemistry, those that permanently modify a soldier's
physiology, and the implant which enables psionic powers.

Soldiers can equip a maximum of two implants at any one time.

## Implant Types

*Note: All of the numbers here will need to be adjusted.*

### Chemical Implants

Chemical implants can be activated in the Battlescape and do not cost
TU. When activated, they inject chemicals into the soldier's
bloodstream. Each chemical injection can enhance performance in some
areas, but too much use (an overdose) can permanently degrade regular
performance.

**Amphetamine Injection:** Improves focus briefly but leaves the soldier
below normal performance when it wears off.

- Effect Duration: 3 turns
  - Accuracy: +10%
  - TU: +10%
  - Morale: +10%
- After-effect Duration: 3 turns
  - Accuracy: -10%
  - TU: -10%
  - Morale: -10%
- Overdose-risk: -20% Accuracy, -10% TU

**Stabilizers:** Reduces heart rate and calms nerves to steady the hands
and boost morale. But it weakens the Mind's resistances.

- Effect Duration: 2 turns
  - Accuracy: +10%
  - TU: -10%
  - Morale: +10%
  - Mind: -10%
- After-effect: None, regular performance resumes
- Overdose-risk: -10% TU

**Emergency Repair:** This implant automatically activates when a
soldier is wounded and provides life-saving adjustments to the body's
chemistry to slow blood loss.

- Effect Duration: 3 turns
  - Bleeding Damage: -2 per wound
- After-effect: None, regular performance resumes
- Overdose-risk: None

### Physiological Implants

Physiological implants are always on and usually produce cumulative
effects over time. They may improve one or another aspect of the
soldier's capabilities, but often degrade other aspects or stunt
development in other fields. There should be an upper-limit to how much
an implant can improve a stat. They can be removed at the hospital.

**Muscle Stimulant:** Improves protein intake and boosts strength over
time.

- 3% Strength value ADDED TO Strength each week
- 3% Mind value REMOVED FROM Mind each week

**Cerebral Activation:** Stimulates the development of new brain cells
and redirects energy consumption to brain repair.

- 3% Mind value ADDED TO Mind each week
- 3% Strength value REMOVED FROM Strength each week

**Retinal Augmentation:** Splices the feed from small cameras worn by
the soldier straight into the retina, expanding the soldier's field of
view.

- Expands soldier FOV to 180 degrees
- Reduces accuracy by 10%

### Psionic Implants

There is only one psionic implant. It enables a soldier to link to the
alien network and perform psi-abilities.

## UI

Implants should appear in the equipped or character stats window. Those
which must be activated in the battlescape should have a button that
appears somewhere.

## Script Definition

Here is a suggestion for how the scripts could be defined. I'm sure
whoever implements it will have their own ideas. If this was done
generically for all items, then we could use some of these effects for
other items (for instance, we could make a piece of headwear give an
accuracy boost). Or give an effect to a regular weapon's firemode.

`// Amphetamine Injection`
`item implant_amphetamine`
`{ `
`   /* Basic details */`
`   name        "_Amphetamine Implant"`
`   model       "weapons/implants/amphetamine"`
`   weapon      false`
`   price       8000`
`   size        1`

`   /* If we ever implement animations for activating an implant? */`
`   animationindex  2`

`   /* Implant-specific parameters */`
`   implant     true    `
`   `
`   /* A single firemode for those implants which are used on Battlescape */`
`   weapon_mod`
`   {`
`       weapon implant_amphetamine`
`       firedef`
`       {`
`           name    "_Use" // Probably not necessary`
`           projtl  null`
`           impact  null`
`           hitbody heal`
`           shots   1`
`           ammo    5`
`           firesnd "weapons/implant"`

`           /* Effects */`
`           effect active`
`           {`
`               duration    3   // 3 turns`
`               accuracy    10  // +10%`
`               tu      10`
`               morale      10`
`           }`
`           effect inactive`
`           {`
`               duration    3`
`               accuracy    -10`
`               tu      -10`
`               morale      -10`
`           }`
`           effect overdose`
`           {`
`               permanent   true`
`               accuracy    -20`
`               tu      -10`
`           }`
`       }`
`   }`
`}`

`// Muscle Stimulant`
`item implant_muscular`
`{`
`   /* Basic details */`
`   name        "_Muscle Stimulant"`
`   model       "weapons/implants/stimulant"`
`   weapon      false`
`   price       8000`
`   size        1`

`   /* Implant-specific parameters */`
`   implant     true    `
`   `
`   /* Cumulative effects outside of Geoscape */`
`   effect strengthen`
`   {`
`       period      7   // Frequency to add attribute`
`       strength    3   // Percent of attribute to add to attribute`
`       mind        -3`
`   }`
`}`

## Roadmap

An outline of how we can proceed in smaller steps. Psionics is ignored
as it will be developed alongside its own
[roadmap](Gameplay_Proposals/Psionic_warfare "wikilink").

### Mark I

Implants can be researched, produced and installed on a soldier to give
benefits. Chemical Implants only partially implemented, to provide
always-on stats bonus.

Tasks:

- Tech articles for implants and a tech tree if needed.
- Placeholder artwork for the implant tech items.
- Hospital UI to add/remove implants.
- Code:
  - Support for implants in data structure.
  - Support for implants in soldier equipment.
  - Simple, always-on status effects in the Battlescape. No
    cooldown/negative effects at this stage.
    - Amphetamine
    - Stabilizers

### Mark II

Support for temporary battlefield effects and the after-effect period.

Tasks:

- HUD:
  - Button to activate implants individually.
  - Display of effect and after-effect period.
- Code: Support for duration and after-effect duration.

### Mark III

Support for permanent overdose effects.

- UI:
  - Some sort of HUD representation of overdose risk, so player knows
    how much he's using it.
  - HUD and base display of overdose effects.
- Code: Implement effects

### Mark IV

Support for Physiological Implants with monthly effects.

- Tech entries for these implants.
- Models for these implants.
- UI: Some sort of representation of stat growth/decline in Implants
  window.
- Code:
  - Support for time-based effects on stats.
  - Save data on when implant was installed.

### Mark V

Support for special implants Emergency Repair and Retinal Augmentation.

- Tech entries.
- Models.
- UI:
  - Emergency Repair: display how long it will last before bleeding
    begins going at full strength again.
  - Retinal Augmentation: maybe just an icon above a soldier with this?
    Or in their stats window?
- Code: Implement the features necessary for these.

## Concept Art

<File:Injection> implant concept art 1.PNG\|Injection implant

[Category:Proposals](Category:Proposals "wikilink")