## Summary

This is a proposal for a simple weight system for UFO:AI. The purpose is
to provide additional tactical possibilities in the battle field, (fast,
light units vs slower, heavier ones), extend the usability life of
lighter armours, and give a meaningful purpose to the (almost) unused
strength ability.

## Design

### Weight

All items should have assigned a scriptable weight value.

- I suggest using kilograms as the units for this, but an abstract unit
  could be used as well.

### Strength

Actors should have a weight threshold based on their strength, when
exceeded they are considered encumbered and should suffer a penalty.

- To keep it simple, I propose having the penalty to be max TU
  reduction.
- Other things to consider:
  - A bonus for actors that are carrying a very low weight.
  - Maybe an absolute max to the weight an actor can carry, based on
    strength?

### UI

At least some form for the user to tell the current and max load of a
soldier must be implemented, some form of clear, unobtrusive warning
when a soldier is encumbered would also be nice.

## Feedback Welcome!

Check the [talk
page](Talk:Proposals/Strength,_Weight_and_Equipment "wikilink") and feel
free to share your thoughts.