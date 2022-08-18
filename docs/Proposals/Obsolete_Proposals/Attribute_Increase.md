## Attribute increases

This article describes mechanics for the increase of a soldier's
attributes.

A soldier will, in the course of the game, gain "experience" in a number
of fields (as many as there are attributes). The soldier will gain
experience in any one field based on the things that he or she did in
combat and on time spent in a training facility. Experience only ever
goes up, never down.

How experience should be gained is a tricky business. I will attempt to
come up with methods that are fair and that make sense, but this issue
is very much open for debate. Please use the talk page to discuss this.

- **Strength** increases when the soldier carries and uses heavy
  equipment. Heavy weapons will affect strength experience, and to a
  lesser degree assault and explosives as well. Moving around in heavy
  armour also affects strength experience. The heavier the armour, the
  faster the experience value rises.
- **Speed** increases when the soldier uses TUs. TUs spent on Reaction
  Fire count less heavily than TUs spent on actively firing and moving.
- **Accuracy** increases when the soldier uses a weapon. All weapons
  increase accuracy, but sniper weapons do so fastest, followed by
  assault.
- **Mind** increases when the soldier damages or kills enemies, as well
  as when the soldier uses support equipment like medikits.
- **Close** increases when the soldier uses close combat weapons.
- **Heavy** increases when the soldier uses heavy weapons.
- **Assault** increases when the soldier uses assault weapons.
- **Sniper** increases when the soldier uses sniper rifles.
- **Explosive** increases when the soldier uses explosives.
- **Health** increases a little bit whenever any other experience value
  rises. Health also rises when the soldier is being healed in a
  hospital.

All of the above will increase when the soldier is training at a PHALANX
base, but training yields much smaller gains than real combat
experience.

With this basic mechanic in place, we can go about actually increasing
the soldier's attributes. Every once in a while (for example, every 24
game hours), the soldier's attributes are updated as follows:

    attribute = basic_value + experience^0.5

Where basic_value is the value the soldier got at generation time (see
[Actor Generation](Proposals/Actor_Generation "wikilink")). The power
used in this example is subject to tweaking.

The net effect of this is that soldiers will initially improve quickly,
but their rate of improvement will reduce over time. However, there is
no real limit to their capacity to grow (other than basic datatype
overflow limits, of course). It also means that a soldier who got a poor
score at an attribute when he was generated will have great difficulty
reaching an outstanding value for that attribute, while a soldier who
got a good score right off the bat will have a clear advantage.

Let's assume that a soldier should, in the course of 100 missions, be
able to get a stat up by 50 points if he's not neglecting that stat.
With a power of 0.5 (the square root), we get 50^(1/0.5) = 2500 points
of experience to be gained in those 100 missions, making for 25 points
per mission. So after one mission, the soldier will have 25^0.5 = 5
points extra for his stat. After 100, he will have 50. If the soldier
trains really hard and earns double the baseline amount of experience
points, he will gain 5000^0.5 = 70.7 points for the stat, which isn't
all that big an improvement over 50.

Moving the power closer to 1 will make the soldier improve less quickly
at the start compared to the later stages, but he will reach higher
values than the baseline 50 with more ease. Conversely, moving the power
closer to 0 will make the soldier improve quite rapidly in his first few
weeks, but almost not at all once he becomes a veteran.

Myself, I think a power of 0.6 with an experience gain of 6 per mission
(at ideal rates) would work well.