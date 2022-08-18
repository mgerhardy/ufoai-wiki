"*The stance of the target. Crouched units are harder to spot than
standing units (+5 stealth), and prone units are harder to spot still
(+10 stealth).*"

This is not necessarily true. If seen from a height (the top of a
building for instance), the unit would be <B>more</B> visible prone than
standing up. The above would be easy to implement, but it would be a lot
better if this stealth modifier was a function of how much of the
target's model is actually inside the actor's LOS. It should still have
a maximum, though, so simply dividing 1 by the percentage of the model
visible isn't the way to go. --[BTAxis](User:BTAxis "wikilink") 17:44,
18 June 2007 (CEST)

maybe you could use the "to-hit" estimate function to return a "to-spot"
probability. It takes account of distance to target, crouching and
partial cover. (though the partial cover bit isnt very good - though
making it better would probably make it too slow).
--[Blondandy](User:Blondandy "wikilink") 14:30, 21 June 2007 (CEST)

## Addendum: Visibility and firing

It occurred to me that as it stands, a soldier can fire at an enemy he
can't actually see if another soldier can see that enemy. I feel that,
especially in the case of direct-fire weapons, a soldier should not be
allowed to accurately attack targets that are invisible to that soldier.
Therefore, I want an accuracy penalty to apply in such cases. Reaction
fire should also not trigger unless the soldier who is using RF can
actually see the target. --[BTAxis](User:BTAxis "wikilink") 14:07, 4
July 2007 (CEST)

## no crouching in the near future

There will be no prone stuff in the near future - because this would
alrise the need for new animations (no real problem, because we have the
bip files) - and we have no animator at the moment.

## Detection

The detection table doesn't make sense when the stealth mode takes the
light level of the target into account. Humans do see dark targets
better if they are standing in a dark area. I think a good solution
would be to have a function that gives the detection value for the light
level of the target for each species. This can either be done by a (may
be 10 item) table or coded as a real function. This would allow non
linear panelties including aliens that are blinded by too much light or
have an special twightlight blindness. The fact that eyes do adjust the
the light level and that is more difficult to see from the light to the
darkness should be ignored IMHO as it is too difficult to be implemented
sanely.

Having a real (C) function for each race would allow to also take other
parameters into account. May be some races do not see movement or have
difficulties seeing at very short or very long distances or have eagle
eyes and are not affected by distance...

- This is far too complicated. I'd rather stick with something simple.
  That way the player can at least somewhat predict how his detection
  and stealth will behave and that is beneficial to the gameplay
  experience. --[BTAxis](User:BTAxis "wikilink") 01:13, 28 September
  2007 (CEST)

## Movement

Much more than visible size and light level does movement influence the
visibility (or better the recognizability) of an object. Persons that
did move and are visible at the beginning of the round should be much
easier to spot as nonmoving (at least 3 times further). During the own
movment other persons could have their stealth factor be modified by
their used up tus (may be only tus used for moving). This would allow
people to sit in the darkness and watch the enemy walking into the set
trap.

- Good point. We should make moving actors have a lower stealth factor
  than static ones. --[BTAxis](User:BTAxis "wikilink") 01:13, 28
  September 2007 (CEST)

## Spotting & stealth ability/skill

I was reading btaxis' proposal about [attribute
increase](Proposals/Attribute_Increase "wikilink") then got here; could
we have "spot" and "stealth" abilities/skills on actors? That would give
deeper gameplay, and a potential new "recon" class (with short range
weapons and light armours also affecting that); i never played the ufo
after\[math\|shock\] game serie myself, but a friend of mine told me
there's something similar implemented in those games. However in general
i think this proposal about actor visibility would represent a great
plus on the ufoai gameplay. --[Flea](User:Flea "wikilink") 20:41, 17
November 2008 (UTC)

## Displaying visibility information

As I've been working on the new rendering system, I've been thinking
that it would be nice to have a better way of displaying the per-team
(or per-actor) visibility information. Right now, it's impossible to
tell what parts of the world your soldiers can see right now, what parts
they've seen in the past, and what parts they haven't explored yet. I
think that we should try to change that.

I'm envisioning a system where "unexplored" areas might be completely
black, or covered in grey fog, or something, so that the player wouldn't
know the exact layout of areas that hadn't been seen before. This would
be particularly meaningful on the RMA maps, because it would actually
force the player to explore, rather than simply moving around known
terrain. In the original X-COM, I think that this type of exploration
added to the sense of drama, because you never quite knew what you were
going to find.

The other thing I'd like to have is some visual representation of a "fog
of war" that would let the player know what areas had previously been
explored but were no longer in direct view of any soldiers. This could
be some sort of interface toggle that would cause an overlay (e.g. a
green cone, or something) that would show what was currently visible to
the team. Alternatively, it could be an "always-on" type of effect, like
having areas that couldn't be currently seen rendered in greyscale, and
directly observed areas rendered in color.

Not only would these things improve the atmosphere, I think they would
be useful gameplay additions as well; right now, it's hard to know where
an alien could be hiding, because you can't really tell which squares
are directly observed and which aren't.

I'm open to suggestions about how this should look, or what information
we want to display; what do people think?


i think this would be a nice feature (but should be switchable of
course) - something like in warcraft 3 maybe. unexplored = black, not
visible but explored earlier gray, visible ... well no color overlay.
--[Mattn](User:Mattn "wikilink") 16:08, 19 June 2010 (UTC)