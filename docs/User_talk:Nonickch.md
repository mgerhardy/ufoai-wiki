Hello, I'll be doing things here and there with the AI. For personal and
3rd party reference, I'm keeping my todo list here:

- Finetune GUETE values -Made initial checks, need people to test some
  values and tell me what they think of the changes in behaviour (Set
  src/game/g_ai.h \#defs for GUETE_HIDE to 30 and GUETE_CIV_FACTOR to
  0.15. Do not change GUETE_HIDE if you're working on development
  trunk). Try and fiddle with the values in the 10% range and see if you
  get a better experience. Please make a large enough set of games
  (prefferably while playing the campaign) in order to have a more
  complete and map-independent view. --Work in progress
- Dodon's patch made aliens too agressive. Tone down via possibly making
  them evaluage visible threats better (AI_HideNeeded)
- Switch&test CLOSE_IN bonus to use pathing distance instead of absolute
  distance.
- Try and find the 'aliens shoot through walls' bug
- Get aliens to shoot prone if it needs be.
- Switch GUETE bonuses to multiplicative and observe the new behavior,
  re-tune GUETE's
- Grenade/knife throwing from inventory and indirect fire shots.

## Current work

Fixing/augmenting damage estimation of the AI via using the
g_combat.c/G_\* shooting functions, CL_GetHitPercentage, aswell as the
AI_HideNeeded. The performance penalty of the G_Shoot\* functions is to
too great, but are currently the only viable ways of estimating splash
and gravity-based weapons. The attempt is to use G_Shoot\* for those
weapons and an improved version of CL_GetHitPercentage for the rest.
Optimal future solution is to work solely from the math of
hitpercentages.

`These will *probably* fix the following:`

- Aliens properly evaluate the possible outcome of their shots. That
  does include splash damage from all weapons.
- aliens can apply indirect fire properly. Best case scenario: they can
  throw grenades above obstacles. As it is right now they think grenades
  move in a straight line. Timed grenadelauncher shots are possible, but
  currently not checked vs open space in order to get the extra range
  via bounce.
- aliens will stop being so suicidal since they know when they can get
  easily killed the next turn
- Aliens might be able to employ med-packs
- An overall balance between aggression and hiding, provided the
  GUETE_HIDE is fine-tuned again
- Aliens are aware of the difficulty level and their bonuses because of
  it (extra dmg)
- Possibly solve the aliens-shoot-walls issue (LOF properly calculated
  and G_IsVisibleForTeam dropped for LOS calculations because it uses
  the vismasks)
- Pave the way for grenade/knife-from-backpack throwing support
- Aliens can shoot on different z-levels of the target (does it make any
  difference???).
  - see
    [r30900](https://sourceforge.net/apps/trac/ufoai/changeset/30900)
    --[Mattn](User:Mattn "wikilink") 07:23, 6 July 2010 (UTC)
- Overall encounter difficulty will go way up (pending GUETE
  optimization)

As you can see there's a whole lot of things that stand to be gained
from this, thus I'm taking my sweet time.

Unfortunately, this will also mean that the aliens tap into their
god-o-vision a little more.