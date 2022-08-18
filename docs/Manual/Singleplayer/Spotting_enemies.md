Every character model has a field of vision that is basically described
by a cone shape in front of him. The character can see anything within a
45 degree angle compared to the direction he is facing.

In the example below the indicated soldier is facing in the direction of
the yellow arrow. He can see both aliens (red circles) as they are
within his field of vision. He may not see anything that is in the
stable (the cow) on the left side of the screen.

<figure>
<img src="Manual_LOS1.JPG" title="Manual_LOS1.JPG" width="500"
alt="Manual_LOS1.JPG" />
<figcaption aria-hidden="true">Manual_LOS1.JPG</figcaption>
</figure>

The field of vision for the left soldier is constricted as the stable
walls block a large part. He is able to see the cow but not the aliens.
Notice that the feeder and the fence do not block his vision as they are
not high enough.

<figure>
<img src="Manual_LOS2.JPG" title="Manual_LOS2.JPG" width="500"
alt="Manual_LOS2.JPG" />
<figcaption aria-hidden="true">Manual_LOS2.JPG</figcaption>
</figure>

To spot an enemy a character has to have line of sight (LOS) to that
enemy. That means it must be possible to trace a line from your
character model to the enemy, which is not blocked by solid objects
(i.e. wall). The enemy must not be completely visible to spot him, if a
LOS can be traced to any part of the enemies model, this enemy will be
seen.

You characters will spot anything even when moving. If at any point of
your move your soldier spots an enemy that was unseen before, his action
will be interrupted and you will be informed. During your turn the
program will remember the enemies you have spotted even if you move your
characters to new positions where they would not be able to see the
enemy any more.

If during the enemies turn, at any point an enemy character walks into
your forces field of vision, you will be able to see them and if this
enemy was unseen before you will be informed. If you see enemies
vanishing into thin air, this means that he left your forces field of
vision.

And remember: It’s easier to kill, what you can see!