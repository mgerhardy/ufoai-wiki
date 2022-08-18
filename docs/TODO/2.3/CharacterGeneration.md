## Overview

I hacked together a patch that picks character names from the "nation"
the character is from, e.g. russia or latin.

In addition to improving this name generation by means of nationality
categories, I would like expand this to include sounds and models. e.g.

nation russia {


...

nationalities {


russian 90

british 5

chinese remainder

}

A Russian character has a 90% chance of having the nationality
'russian'. His name will be generated as before from a list with only
Russian names, so let's say he's named 'Vladimir Putin'. The previous
code does support male/female last names in addition to neutral ones, so
that will be supported.

Vlad needs to sound Russian when he yells in pain so the list will
include nationality-specific voice lists.

Now to determine what Vlad looks like, we have to indicate that he's
Russian *AND* a scientist, or a soldier, or... etc. A Russian medic
would likely look different than a Chinese one (at least their head
model). And an Arab soldier head differs from an Arab worker.

human_soldiers/scientists and even civilians(?) should use the same set
of name/voice lists, not replicated across teams as they are now, but
their models do depend on class. I'm figuring out how to organize this
with the fewest redundancies and keeping it intuitive for others to
populate/modify the lists.

## Implementation

- Parse nationality lists per nation

- Names

  - Retrieve names per nationalities



For PC's only (excluding robots), not aliens

- - Parse names in team definitions by nationality

- Sounds

- Models

Details to follow, stay tuned.