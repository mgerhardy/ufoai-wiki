## Visibility

This is a proposal for the implementation of visibility (and lack
thereof) in the game.

At the time of writing, a target is visible when:

- There is a LOS (=Line Of Sight) from an allied actor to the target.
- The allied actor is facing the target.

I think most people will agree that this is not desirable. Stealth and
detection must play a role in tactical combat, especially at night.

Whether an actor spots a target should be a function of two factors: the
actor's ability to detect and the targets visibility.

### Detection

The ability to detect should be fixed for each species (human, Ortnok,
Taman, etc), but can be modified by equipment such as IR goggles (better
detection) or gas masks (worse detection) or implants. In addition, the
(unaided) values should differ depending on whether it is day or night.
Here is an example of a detection ability table:

<table border="1">
<tr>
<td>

Species

</td>
<td>

Day

</td>
<td>

Night

</td>
</tr>
<tr>
<td>

Human

</td>
<td>

50

</td>
<td>

25

</td>
</tr>
<tr>
<td>

Ortnok

</td>
<td>

60

</td>
<td>

60

</td>
</tr>
<tr>
<td>

Taman

</td>
<td>

25

</td>
<td>

75

</td>
</tr>
<tr>
<td>

Shevaar

</td>
<td>

50

</td>
<td>

50

</td>
</tr>
<tr>
<td>

Hovernet

</td>
<td>

75

</td>
<td>

75

</td>
</tr>
</table>

These values are the base values that apply to the actor's own square.
The value should gradually decline with distance from the actor. Say, by
1 per metre.

Note that this might unbalance multiplayer. Perhaps all actors should be
given the same values in multiplayer to prevent this.

### Stealth

A target's visibility (though, given the counter-intuitive values in
this section, a better term would be "stealth factor") should be
influenced by:

- The lighting of the space the target is on. A square in full daylight
  will have stealth factor 0, and a square right underneath a street
  light will have a stealth factor of -10 (since these squares are
  especially noticeable in the darkness), while a square in a deep
  shadow at night could have stealth factor 20.
- The stance of the target. See partial obscurity.
- Any stealth bonuses the target receives from camouflage or other
  cloaking methods, such as smoke screens.
- Aliens could get small stealth bonuses or maluses as a result of the
  difficulty setting.

If the unit's visibility is equal to or less than the actor's detection
value at that range, and the conditions mentioned at the start of this
article are met, the target is spotted. Otherwise, the target remains
hidden.

### Partial obscurity

An issue is partial obscurity. For example, a prone soldier lying on a
roof would be hard to spot while a prone soldier in a pit would be
really easy to spot.

If either full obscurity or the simpler stealth factors mentioned above
result in non-visibility of the target, we're already done. When the
target is deemed visible, however, we must do more work.

#### Option 1: Ray-casting

In total, ten rays must be traced:
- One for either foot of the target
- One for either hand of the target
- One for either hip of the target
- One for either shoulder of the target
- One for the target's torso
- One for the target's head

A ray must be traced from each of these ten points to the eyes of the
spotting actor. For every ray that can't be traced, the target receives
a stealth bonus, which may or may not bring his stealth factor above the
spotting actor's detection ability. If so, the target remains hidden. If
not, the target is visible. Note that if the target could not possibly
become invisible even with the ray tracing modifiers, the ray tracing
step may be skipped as the actor will be visible anyway.

I believe that with a limited amount of rays as described here, we can
implement a fast partial obscurity model that is nevertheless accurate
enough to be convincing.

#### Option 2: Image rendering

I believe this is something that Arisian spoke about before, and I may
not be exact on the details. But it seems pretty straightforward. It
involves rendering an image from the unit's point of view. All non-enemy
items are rendered black, all enemy units are rendered white. Then it's
just a matter of comparing how many pixels are rendered white. If enough
are rendered white the enemy unit is considered visible.

In addition, a second image could be rendered with proper colors to test
camoflauge. These images could be compared to see which areas of the
second image represent the enemy unit. Then some calculations could be
done to see if the enemy unit's colors match the colors around him. If
so, then his visibility decreases.

## Roadmap

This is an attempt to organize the proposal here and several of the
suggestions from the talk page into a staged timeline for development.
Since visibility is such a large and complex system, this roadmap
attempts to lay out a series of intermediate systems on the way to a
more complete system. These steps would be more easily implemented and
would allow us to move forward without committing to such a major
project in one release.

### Mark I

Implement reduced visibility based on distance, time of day and race
attributes (listed above). A unit's probability to see another unit will
reduce depending on how far away from the unit he is, whether it is day
or night and his race's visibility attribute. Player should receive some
visual feedback on which tiles are visibile and which tiles are not.
Very easy to implement and will function as expected in most situations.
But it does not take into account lights on night-time maps or the
benefits of hiding part of an alien's body behind an object.


Tasks:


Changes to files to add race sight attributes

Adjustments to visibility code to take into account these factors

Basic UI display of tiles visible. This could be as simple as a green
circle displayed on each visible tile when the player clicks a button.
It could be a cloud-like particle that is put over tiles the player can
not see.

### Mark II

Implement support for adjustments to visibility based on movement and
adjustments to visibility during reaction fire. When a unit is moving,
his visibility should increase dramatically. Moving while crouched
should still increase visibility, but less than moving while standing. A
unit should only be able to perform reaction fire if he has direct
visibility of the unit. Visibility should not be shared across the team
in this case (not sure if it is at the moment, but this is responding to
a comment on the talk page from BTAxis).


Takes:


Adjustments to visibility code based on movement

Adjustments to reaction fire code

### Mark III

Implement support for smoke grenades, visible weapons and enhanced UI
visibility display. A soldier's probability to see an alien will reduce
if smoke from a smoke grenade exists between the soldier and the alien.
If a unit fires a highly visible weapon (flamethrower), he should beome
more visible. Any areas not visible at the beginning of the map should
be covered in black. When the player has seen an area it becomes
visible, but areas the player has revealed but can not yet see should
display with some kind of cloudy or grey overlay indicating the player
can not currently see them.


Tasks:


Adjustments to LOS code to take into account whether or not the ray cast
passes through smoke.

Particle effect for smoke.

A way for smoke to grow/fade over time.

Adjustments to weapons.ufo to indicate how much a weapon show "expose" a
unit when fired.

Ability to calculate whether an area should be
unexplored/explored/visible.

Some way to make the transition between the unexplored/explored/visible
look nice.

### Mark IV

Implement support for adjusting visibility based on the unit's lit
state. If a unit is standing in the light, he should be more visible
than if he is standing in the dark. This would supercede the visibility
calculations based on time of day of the map.


Tasks:


Option 1: Rendering engine must be able to apply lights from all sources
(light entities, lights created from surface textures during rendering
time, sunlight) and a unit's visibility should be based on that.

Option 2: The game compiles information about each grid tile's
visibility during compilation (like the pathfinding, this is embedded in
the .bsp). The game can then determine a soldier's visibility based on
the grid tile they are in.

### Mark V

Implement partial visibility based on ray-casting or image rendering.
Units with parts of their bodies behind cover should be less visibile.
For full details, see Partial Visibility above.


Tasks:


Depends on whether ray-casting or image rendering is implemented.

## Technical

There is already `CM_GetVisibility`. This function is not fully
implemented yet.

[Category:Proposals](Category:Proposals "wikilink")