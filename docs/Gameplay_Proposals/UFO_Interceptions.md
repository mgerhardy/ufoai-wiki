## UFO Interceptions

This is a description of how I believe UFO interceptions should behave.
I believe the current UFO interception scheme, which happens directly on
the geoscape, is crude and insufficient. It can not effectively deal
with multi-UFO flight groups, and the range at which combat happens is
absurd, not to mention contrary to the UFOpaedia's weapon descriptions.

## Concept

### Interception

UFO interceptions should behave similarly to the ones in X-COM in the
sense that an intercepting aircraft should attempt to rendezvous with
the target UFO (or UFO flight group). If the interceptor succeeds in
attaining the same geoscape coordinates as the target, the interception
is successful, and combat commences.

### Combat

Combat happens in a separate interface. This interface is a close-up of
the immediate area, showing only a few square kilometers. In this
close-up view, the UFO(s), interceptor(s) and weapons are shown flying
around in actual combat. The player can actively influence the battle by
giving his interceptor(s) orders in this interface.

### Combat versus the geoscape

While combat occurs, time on the Geoscape does not stop. It is possible
for new missions to appear or research to finish while the player is
busy dealing with a combat scenario. However, since combat happens at a
low time setting (5 seconds to 10 seconds, most likely), this is not
very likely. The most notable effect of this concurrent time flow is
that it is possible for new objects to enter combat, and craft to flee
from it. For example, if the combat occurs within range of a
ground-based weapon, such as a base defence facility, then the
projectiles or beams from this weapon can appear in combat and attack
the UFO.

The player can also choose to leave the combat view and return to the
geoscape. Combat will still continue, however, and can be over almost
instantly if the player speeds up time on the geoscape. A player may
wish to leave a combat if there is another combat going on at the same
time, or to tend to some other important task.

## Interface

### Interface elements

A new mockup of the planned interception screen is available here:
[1](http://crossedswords.co.nr/downloads/UFOAI/interceptionmockup.png)

Air combat is initiated when interceptors meet UFOs on the geoscape,
when the two groups are right on top of each other. No weapons fire
should be exchanged between aircraft on the actual geoscape. Only ground
installations can fire/be fired upon on the geoscape.

The geoscape interface zooms in on the interception site and becomes the
interception screen, giving us a full 3d overview of the combat zone
with a representation of the terrain below, much closer-up and more
detailed than the geoscape. (In early implementations or if terrain is
too difficult to generate, the terrain can be replaced by simple fog.)
Once the interception screen is reached, zooming should be placed under
the control of the player by way of the mouse wheel or keyboard. It
should only be possible to zoom out a few kilometres during air battles;
the player must not be able to go back to the geoscape without clicking
on the 'back to geoscape' button.

Zoomed out to the maximum, the combat participants would be only icons
flying around over the terrain or fog, essentially there only to show
their location and heading (as well as craft-specific info as in the UI
mockup above). Zoomed in to more realistic distances, we should be able
to see the actual craft models flying around, getting behind each other
and firing their weapons. Possibly we can even offer different camera
positions, it'd be cool to follow over the shoulder of your planes as
they cut through the chaos.

The player's view of the action should be fully rotateable -- you can
look at the fight from the top, from the side or even from underneath at
any zoom level. The globe and/or terrain should not be drawn when the
camera is underneath it. The camera should be able to focus on any
specified participant in the combat. By default it should focus on a
'central point' calculated to be the average X/Y centre between all
combat participants, looking directly down on the combat at medium zoom,
and the player should be able to return the camera to this default
position at will.

All craft participating in combat are listed in the 'participants' box,
as seen in the UI mockup above. Left-clicking a friendly craft selects
it and makes it available to receive orders. Left-clicking on an enemy
craft assigns the enemy craft as target to the currently-selected craft.
Right-clicking on a friendly craft pops up the 'orders' menu, allowing
the player to determine the craft's combat posture and at what range the
craft should engage the enemy. The orders should be treated as strong
suggestions by the AI -- since these combats are mainly AI-driven, the
pilot AI shouldn't always take the player's word as law when it's
clearly not the right thing to do, but should treat it with the
appropriate weight. Default orders are Defensive Posture (first try to
survive, then try to shoot down enemies) and Weapons Range (maximum
range at which all weapons can fire).

The currently-selected craft is displayed as a paper doll in the 'craft'
box. Below the paper doll is the craft's weaponry and equipment, and
below that is the craft's target. Any listed equipment can be
right-clicked to turn it off or on.

### Combat Behaviour

The main UFO will attack any interceptors if armed, will try to
disengage if unarmed, and generally wants to get back to its mission as
defined by the [campaign
framework](Gameplay_Proposals/Campaign "wikilink"). If all human craft
or the main UFO are disengaging, then any craft that stray too far from
the main UFO will leave combat. These craft will have to catch up with
the main UFO to re-enter combat. When not in combat, a craft can not
attack. If all PHALANX interceptors leave the combat then the combat is
over. This means that if the main UFO speeds up and the interceptors
can't keep up, the UFO will outrun the interceptors and end combat.

A craft can fire a weapon at its target when the target is within range
of that weapon and within the weapon's firing arc. Different weapons
have different ranges and firing arcs. An interceptor will conform to
the engagement range specified in its orders: Max Range (the maximum
range of the longest-ranged weapon on the craft), Weapons Range (the
maximum range of the shortest-ranged weapon on the craft), or Kill Range
(the range at which distance modifiers to accuracy are smallest).
Depending on the weapons the player enables or disables in the 'craft'
box, this means the interceptor can fight at many different ranges.

Interceptor/UAV behaviour is also dependent on their player-selected
'Posture'. Available postures are: Aggressive (try to shoot down
enemies, all other considerations are secondary), Defensive (first try
to survive, then try to shoot down enemies), and Disengage (try to leave
combat).

#### UAVs

Any UAVs joining the combat with their assigned interceptors start out
'slaved' to their interceptor by default. When slaved, they attack the
interceptor's target and protect the interceptor's rear as best as
possible. They can be toggled out of slave mode by the player,
'unslaved', at which point they can be assigned specific orders by the
player which they follow as best as possible. UAVs automatically become
unslaved if their interceptor is destroyed. Individual UAVs can be
slaved or unslaved by double-clicking on them in the craft list.
Double-clicking on an interceptor will toggle slaved/unslaved status for
all UAVs assigned to that interceptor.

### Hitting and missing

In combat, being able to hit a target is a major factor. Quite a lot of
attacks should miss their target. Since UFO interceptions are much
simpler than tactical ground combat, it is not necessary to include a
complicated accuracy model. It suffices to calculate a to-hit chance
depending on a few factors (base weapon accuracy, countermeasures used
by the enemy, distance between attacker and enemy). Then a simple roll
is made, and depending on the outcome the animation on the combat screen
shows a hit, a miss or an attack thwarted by countermeasures.

[Category:Proposals](Category:Proposals "wikilink")