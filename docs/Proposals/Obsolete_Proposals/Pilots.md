# Pilots

## Summary

## Solution Design

### Interface

The new interface for pilots includes the following features:

- Hiring of pilots through the standard employee hire screen.

  - There is always a full list of unhired pilots available
  - The unhired pilot list is refreshed during the budget processing.

- Temporarily able to assign pilots to aircraft through the "aircraft
  equip" screen. This will eventually be replaced with an
  employee/aircraft assignment screen that will include pilots.

- A new type of aircraft that doesn't require a pilot. This aircraft
  type is an unmanned aerial vehicle or UAV.

- All non UAV aircraft must have a pilot assigned to be active.

**Temporary addition of pilots to aircraft equip screen**

- New "pilot" button next to the "items" button.
- Pilots can be added and removed from an aircraft using the existing
  equip screen iterface.

![Image:Aircraft-equip-pilot-screenshot.png](Aircraft-equip-pilot-screenshot.png "Image:Aircraft-equip-pilot-screenshot.png")

### Stats

Pilots will have statistics that affect their performance in air combat
and other actions.

There will be three main statistics for a pilot:

1.  A "piloting" statistic (This is the main stat that the player will
    see).

    This statistic will govern how effective the pilot is in air combat.
    It will be a modifier to a number of factors in air combat.
2.  A "crash survival" statistic (hidden from player)

    This statistic would determine how likely a pilot was to survive a
    crash and thus able to be recovered.
3.  A "UAV coordination" statistic (visible to player, but shown
    somewhere as a whole number)

    This would govern how many UAV's a pilot could control during air
    combat.

Pilots will gain stat increases using a similar system to soldiers with
the following exceptions:

- There will be no starting stats, all stats will start at 1 (no
  experience)
- Stats will be calculated on the fly from the experience figure for
  each stat.

### Air Combat

Pilots "piloting statistic will impact the following aspect of air combat:

1.  Evasion

    This would modify the effectiveness of the pilots usage of ECM's and
    his chance of being hit.
2.  Accuracy

    This would modify how likely the pilot is to score a hit.
3.  Maneuvering

    Modifies how quickly the pilot can fly, so how quickly he can get
    from point a to point b.

Pilots "UAV coordination" statistic has the following effects on UAV's:

1.  Number of UAV's in the air

    This could either mean that the UAV's would need to be part of an
    air group that the pilot could control, or we need some way to
    decide which pilot is controlling what UAV's. Its also possible
    that, if say there are two pilots in the air, it is their total for
    this stat that determines how manu UAV's can be in the air at one
    time.

### Accumulating experience

experience caps for pilot skills:

- Piloting = ?
- Crash Survival = ?
- UAV Coordination = ?

## Technical Design

### Interface

### Statistics

The current statistics for a emplloyee are stored in this struct:

    typedef struct chrScoreGlobal_s {
        int experience[SKILL_NUM_TYPES + 1]; /**< Array of experience values for all skills, and health. @todo What are the mins and maxs for these values */

        int skills[SKILL_NUM_TYPES];        /**< Array of skills and abilities. This is the total value. */
        int initialSkills[SKILL_NUM_TYPES + 1];     /**< Array of initial skills and abilities. This is the value generated at character generation time. */

        /* Kills & Stuns */
        int kills[KILLED_NUM_TYPES];    /**< Count of kills (aliens, civilians, teammates) */
        int stuns[KILLED_NUM_TYPES];    /**< Count of stuns(aliens, civilians, teammates) */

        int assignedMissions;       /**< Number of missions this soldeir was assigned to. */

        int rank;                   /**< Index of rank (in gd.ranks). */
    } chrScoreGlobal_t;

to handle stats for pilots i plan on adding a new array to this struct
as follows: int experience\[PILOT_SKILL_TYPES\]

The following typdef will define the skills for pilots:

    typedef enum
        SKILL_PILOTING,
        SKILL_CRASH_SURVIVAL,
        SKILL_UAV_CONTROL,
        PILOT_SKILL_TYPES
    } pilotskills_t;

### Air Combat

## Links