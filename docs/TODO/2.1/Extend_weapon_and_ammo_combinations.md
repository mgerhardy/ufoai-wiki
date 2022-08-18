## Progress

**This thing as done ... further features (like firemode-combinations
and weapon extensions as mentioned below) will be handled in a seperate
entry if needed.** --[Hoehrer](User:Hoehrer "wikilink") 13:38, 10
February 2007 (CET)

Extend weapon and ammo combinations

- Create a [\#Branch](#Branch "wikilink") of the effected directories so
  myself any anybody who wants to help here can develop this without
  disturbing the trunk. --[Hoehrer](User:Hoehrer "wikilink")

- Add basic code and data so firemodes are split up in a
  per-weapon/multiple-firemodes structure. See [\#Implementation
  proposal 1](#Implementation_proposal_1 "wikilink").
  --[Hoehrer](User:Hoehrer "wikilink")

- \[Priority low\] Add c-code to display the new firemode gui.
  --[Hoehrer](User:Hoehrer "wikilink")

- \[Priority high\] Fix problems with sending (it's ok before writing)
  and receiving (the obj index is always 0) the firedefs on
  EV_ACTOR_START_SHOOT, EV_ACTOR_SHOOT, EV_ACTOR_SHOOT_HIDDEN and
  EV_ACTOR_THROW.

  - See a quick summary of the problem in [\#ReadFormat
    problem](#ReadFormat_problem "wikilink") .. any ideas?
    --[Hoehrer](User:Hoehrer "wikilink")

- \[Priority high\] Where in the code is distinguished between primary
  and secondary firemode and WHY? .. This needs to be changed to support
  more firemodes. This includes but is not limited to [\#Shoot
  types](#Shoot_types "wikilink").

  - Found `cl.cmode` in cl_input and cl_actors. It has the following
    states assigned right now:
    `M_FIRE_PR, M_FIRE_PL, M_FIRE_SR, M_FIRE_SL`

  - [\#Shoot types](#Shoot_types "wikilink")

    - Basic code changes as listed in [\#Shoot
      types](#Shoot_types "wikilink") and all related code (**Major
      change**)

    - (Postponed to [TODO/2.1](TODO/2.1 "wikilink")) Check if firedefs
      in `AI_FighterCalcGuete` in are calculated correctly.

    - (Postponed to [TODO/2.1](TODO/2.1 "wikilink")) Search for all uses
      of `byte fmode1` and `fmode2` and check if this needs improvement.

  - more ...

- \[Priority low\] Finalise the GUI stuff in menu_hud.ufo

  - Change GUI so only one button for list-showing is needed.

  - Fix the position of the lists.

- \[Priority high\] Merge the [\#Branch](#Branch "wikilink") back into
  the trunk.

<!-- -->

- \[Priority medium\] Additions for Reaction Fire:

  - Add variable to track the last selected firemode of each soldier.
  - Tweak reaction fire to use last selected firemode for reaction fire,
    or use default firemode if no previous selection exists.
  - Create a flag to prevent flagged firemodes from being used for
    reaction fire. Display note on the firemode selection box if it
    cannot be used for reaction fire.
  - My personal favourite (a combination of the above) is to let the
    user select one firemode (of a "reaction-enabled" list) for reaction
    fire. i.e. only the ones useable for reaction fire are possible to
    select. Default will be the first reaction-firemode in the list (or
    one that is defined in the ufo file if this proves to be
    inflexible). The last selected firemode is not needed here ... but
    it might be if he have other stuff that requries it.
    --[Hoehrer](User:Hoehrer "wikilink")
    - I think that would slow down play by an unacceptable amount and
      make the GUI seem more cumbersome. I don't support it.
      --[Winter](User:Winter "wikilink") 15:54, 4 February 2007 (CET)
    - Why that? The selection would be in the same list (a small
      checkbox next to each firemode) and the user just switches the
      default firemode if we wants a different one. Doing this with the
      last selected firemode would leave us guessing what the user wants
      if he constantly uses a non-reaction firemode.
      --[Hoehrer](User:Hoehrer "wikilink") 17:36, 4 February 2007 (CET)
      - Ah, that sounds far more manageable than what I thought you
        meant. I withdraw the comment. Still, the default firemode of
        the soldier's weapon should be automatically selected/enabled
        for reaction fire at combat start.
        --[Winter](User:Winter "wikilink") 19:26, 4 February 2007 (CET)
      - Ah, ok then :) Default firemode selected on combat start: Yes,
        that's what I had in mind with the "*Default will be the first
        reaction-firemode in the list (or one that is defined in the ufo
        file)*" part of my explaiantion above..
        --[Hoehrer](User:Hoehrer "wikilink")

## General discussion

We need to adapt the ammo-weapon stats so we can define different stats
for different ammo that is used in different weapons. A possible
solution might be "modifier" based (suggested by Winter) but this sure
needs some serious discussion.

To quote him:

    (22:04:59) winter: Ah. But that's the case in the shotgun as well.
    (22:05:23) winter: The flechettes fired from the Micro Shotgun should have significantly more spread and less range than the Riot Shotgun.
    (22:05:48) hoehrer: they _should_ .. i'm sure thay do not do that yet
    (22:06:07) winter: Ah. Hm. Can we code some simple modifiers?
    ...
    (22:07:23) winter: Well, the simplest way -- it seems to me -- would be to make a modifier on the ammo item's stats based on the weapon it's loaded into.
    (22:07:51) winter: So we'd place modifiers in the weapon entry.
    (22:07:59) winter: Or something like that.

Additional note: This topic will also deal with other item-related TODO
entries, such as "Grenades have no timed explosion secondary fire mode."

## Desired behavior

We'll try to maintain a list of all possible weapon and ammo
combinations and their properties so we can get a feel for what's
needed.

List of shared-ammo weapons and their behavior:

### Shotguns

- [Riot Shotgun](Equipment/Primary_Weapons/Riot_Shotgun "wikilink")
  - [Flechette Shells](Equipment/Ammunition/Flechette_Shells "wikilink")
    (shared with Micro Shotgun)
    - Standard spread, standard range
  - [Saboted Slugs](Equipment/Ammunition/Saboted_Slugs "wikilink") (not
    shared)
- [Micro Shotgun](Equipment/Secondary_Weapons/Micro_Shotgun "wikilink")
  - [Flechette Shells](Equipment/Ammunition/Flechette_Shells "wikilink")
    (shared with Riot Shotgun)
    - Increased spread, reduced range

### Lasers

- [Laser Pistol](Equipment/Secondary_Weapons/Laser_Pistol "wikilink")
  - [D-F Cartridge](Equipment/Ammunition/D-F_Cartridge "wikilink")
    (shared with all other laser weapons)
    - Larger ammo capacity
- [Laser Rifle](Equipment/Primary_Weapons/Laser_Rifle "wikilink")
  - [D-F Cartridge](Equipment/Ammunition/D-F_Cartridge "wikilink")
    (shared with all other laser weapons)
    - Standard ammo capacity
- [Heavy Laser](Equipment/Primary_Weapons/Heavy_Laser "wikilink")
  - [D-F Cartridge](Equipment/Ammunition/D-F_Cartridge "wikilink")
    (shared with all other laser weapons)
    - Smaller ammo capacity

### Other Items

- [Plasma Blade](Equipment/Secondary_Weapons/Plasma_Blade "wikilink") &
  other one-hit weapons (can be thrown or used to stab once)
- [Grenades](Equipment/Misc "wikilink")
  - Lob firemode
  - Roll firemode
  - Time-delayed detonation, X-COM style. Should be useable with the
    above two firemodes; possibly using Winter's firemode concept from
    TODO/General:

<!-- -->

    So to sum it up, we would have two or more firemodes, represented by 2 or more bars of 3 options
    each, and each bar can have a different set of options for using the weapon (e.g in the case of
    the grenade there is the lob & roll, and in the case of the grenade launcher there would be the
    airburst & timed mode).

    Possibly any button on any bar could be set to have completely different fire modes?

- [Grenade
  Launcher](Equipment/Primary_Weapons/Grenade_Launcher "wikilink")
  - [25mm HIT
    Grenades](Equipment/Ammunition/25mm_HIT_Grenades "wikilink")
  - [25mm IC Grenades](Equipment/Ammunition/25mm_IC_Grenades "wikilink")
  - [25mm Flechette
    Grenades](Equipment/Ammunition/25mm_Flechette_Grenades "wikilink")
- [Rocket
  Launcher](Equipment/Primary_Weapons/Rocket_Launcher "wikilink")
  - [HE Rocket](Equipment/Ammunition/HE_Rocket "wikilink")
  - [IC Rocket](Equipment/Ammunition/IC_Rocket "wikilink")

### Planned Weapon Extensions

- None yet

## Implementation

### Current behaviour

- The information on which ammo can be used in what weapon is defined in
  the research tree by "weapons" entries in the require_AND part of the
  ammo=tech. This stuff works fine and may not need to be changed.

Ok, currently we have 2 fixed fire definitions (primary and secondary).
They are defined like this:

    typedef struct objDef_s {
        ...
        fireDef_t fd[2];    /**< primary and secondard fire definition */
        ...
    }

    /** this is a fire definition for our weapons/ammo */
    typedef struct fireDef_s {
        char name[MAX_VAR];         /**< script id */
        char projectile[MAX_VAR];   /**< particle */
        char impact[MAX_VAR];
        char hitBody[MAX_VAR];
        char fireSound[MAX_VAR];    /**< the sound when a recruits fires */
        char impactSound[MAX_VAR];  /**< the sound that is played on impact */
        char hitBodySound[MAX_VAR];
        char bounceSound[MAX_VAR];  /**< bouncing sound */
        byte soundOnce;
        byte gravity;           /**< does gravity has any influence on this */
        byte launched;
        byte rolled;            /**< can it be rolled - e.g. grenades */
        byte dmgtype;
        float speed;
        vec2_t shotOrg;
        vec2_t spread;
        float modif;
        int delay;
        int bounce;             /**< is this bouncing? e.g. grenades */
        float bounceFac;
        float crouch;
        float range;
        int shots;
        int ammo;
        float rof;
        int time;
        vec2_t damage, spldmg;
        float splrad;
        int weaponSkill;        /**< what weapon skill is needed to fire this weapon */
        int irgoggles;          /**< is this an irgoogles */
    } fireDef_t;

See also Com_ParseItem in scripts.c and q_shared.h

Where the primary firemode is stored in obj.fd\[0\] and the secondary is
stored in obj.fd\[1\].

### Ammo modifiers

Proposed by [Mattn](User:Mattn "wikilink") See the talk page for more

Modifiers in the weapon entry is not good - they would affect other
weapons, too - they should be in the ammo entry imo. something like this
is imageable

    item assault_ammo
    {
        name        "_Assault Rifle Magazine"
        model       weapons/assault/assault_clip
        type        ammo
        category    0
        shape       "0 0 1 2"
        center      "0 0 0"
        scale       1.25
        price       130
        buytype     0

        primary
        {
            name    "_Snap Burst"
            skill   assault
            projtl  bullet
            impact  bulletImpact
            hitbody blood
            firesnd weapons/assault.wav
            speed   0
            spread  "1.4 1.4"
            modif   0.7
            crouch  0.7
            range   60
            shots   3
            ammo    3
            rof     5
            time    15
            damage  "37 0"
            dmgtype normal
            modifier assault {
                range 70
            }
            modifier whatever {
                range 10
                shots 5
            }
        }
        secondary
        {
            name    "_Aimed Burst"
            skill   assault
            projtl  bullet
            impact  bulletImpact
            hitbody blood
            firesnd weapons/assault.wav
            speed   0
            spread  "0.8 0.8"
            modif   0.7
            crouch  0.6
            range   60
            shots   3
            ammo    3
            rof     10
            time    18
            damage  "37 0"
            dmgtype normal
        }
    }

### Implementation proposal 1

Proposed by [Hoehrer](User:Hoehrer "wikilink")

As seen in [\#Current behaviour](#Current_behaviour "wikilink") we
currently have a simple list if fire-definitions/modes with two entries:
fd\[0\] and fd\[1\].

Now if we want to add modifiers (see [\#Ammo
modifiers](#Ammo_modifiers "wikilink") by mattn) and multiple firemodes
(i.e. more than 2 - i'll reach a bit into the future here) we need to
overthink the whole structure of this.

We need:

- Modifiers/stats per weapon
- Firemode 1,2,3,4, etc... for each weapon.

So how about re-structuring this like the following:

    fireDef_t fd[MAX_WEAPONS_PER_AMMO][MAX_FD_PER_WEAPON];
    char weap_id[MAX_WEAPONS_PER_AMMO][MAX_VAR];

    fd[weapon1]
        [0] fire-def1
        [1] fire-def2
        [2] fire-def3
    fd[weapon2]
        [0] fire-defA
        [1] fire-defB
        [2] fire-defC

- MAX_WEAPONS_PER_AMMO = the weapon
- MAX_FD_PER_WEAPON = the fd per weapon

If we need a default list of fire-modes we could define it as the first
weapon-entry (i.e. fd\[0\])

If we use this thoroughly (i.e. we define the correct weapon for every
single ammo) we could even use this as a definition for what weapons
this ammo can be used in (i.e. we store the weapon-idx (weap_idx) as
well here and replace the "weapon" requirements from the tech-tree with
this)

Shortened ufo-definition example (coudl be streamlined):

    item assault_ammo
    {
        ...
        weapon_mod assault {
            firedef {
                name    "_Snap Burst"
                ...
            }
            firedef {
                name    "_Aimed Burst"
                ...
            }
        }
        weapon_mod whatever {
            firedef {
                name    "_Snap Burst"
                ...
            }
            firedef {
                ...
            }
        }
    }

**Simple throwing** (in case of grenades i mean without activating)
should be a **default action for all items** (except some special ones
and doesn't need to be in here IMO.

Comments? Critics? Improvements? Please use the talk page and refer to
"Implementation proposal 1".

#### Branch

The branch
(http://svn.sourceforge.net/viewvc/ufoai/ufoai/branches/ufoai_firemode_patch/)
is now defunct.

#### Shoot types

Problem solved

#### ReadFormat problem

Solved: Never every use `byte` variables for network ReadByte (and
implicitly WriteByte as well). The network code always uses `int` for
transfer, so this will just cause problems.

[Category:Contribute](Category:Contribute "wikilink")
[Category:TODO](Category:TODO "wikilink")
[Category:Development](Category:Development "wikilink")