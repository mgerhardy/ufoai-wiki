
It's unclear if this proposal or any part of it has been implemented
since it was created in 2008. Please add a note if you know if this is
obsolete, still relevant or not. --[H-hour](User:H-hour "wikilink")
14:29, 7 October 2012 (SAST)

## Scoring

This article describes the scoring screen the player receives after
completing (or abandoning) a tactical mission.

A player's total score is the sum of the following individual scores:

- Aliens killed. This score depends on the number of aliens killed
  during battle, and the types of aliens killed.
- Aliens captured. This score depends on the number of aliens captured
  alive, and the types of aliens captured. Capturing aliens is worth
  more than killing them. Stunned aliens that can not be taken to base
  because of a lack of space in AC are considered killed.
- Alien equipment captured. This score depends on the equipment
  initially given to the alien team that is taken back to base.
- PHALANX soldiers killed. This score is a negative value. For every
  PHALANX soldier that dies or is infected, this score is lowered by a
  value appropriate for that soldier's rank.
- Civilians killed or infected by aliens. This score is a negative
  value. For every civilian that dies or is infected, this score is
  lowered by fixed value. No penalty is awarded for civilians that were
  infected before the start of the mission.
- Civilians killed by PHALANX. This score is similar to the one above,
  but the penalty is more severe.
- Civilians saved. This score is equal to a fixed value multiplied by
  the amount of civilians that remain unharmed.
- Infected civilians spared. This score should not show up unless the
  mission contained infected civilians. For every civilian that was not
  killed but stunned, this score is raised by a fixed number. Note that
  this fixed number should be less than the penalty for letting
  civilians get infected.
- The time PHALANX takes to get to the mission. The longer it takes, the
  lower this score. This score can be positive for very fast responses
  (for example when PHALANX immediately lands at a crash site after
  shooting down a UFO with a combat dropship), but will usually be
  negative. The score decreases increasingly rapidly down to a certain
  minimum value. This means that the player is given at least some time
  to get his dropship to the scene before the penalty really begins to
  hurt.

Based on this score, an overall assessment should be given at the bottom
of the list. This assessment is based on the relative performance on
this mission. This can be calculated because the score for the best case
scenario (all civilians saved, all aliens captured, all equipment taken
to base, no PHALANX losses) as well as the worst case scenario (all
PHALANX soldiers dead, all civilians dead, no aliens killed, mission
failed) can be calculated at the start of the mission. Let's call the
best case scenario score 100% and let's call the worst case scenario
score -100%. Assessments can then be given as follows (as an example):

    -100% ~ -75%:  Disastrous
    -75%  ~ -50%:  Awful
    -50%  ~ -25%:  Bad
    -25%  ~  0%:   Unsatisfactory
     0%   ~  25%:  Mediocre
     25%  ~  50%:  Good
     50%  ~  75%:  Very Good
     75%  ~  100%: Excellent

Note that the effect on nation happiness should depend on the relative
score, but scaled by the absolute score. In other words, botching a big
mission hurts more than botching a small one.

Maybe scoring could depend on difficulty, for example by increasing the
negative factors, making it harder to get a good score.

[Category:Proposals](Category:Proposals "wikilink")