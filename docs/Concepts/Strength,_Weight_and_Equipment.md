This is document describes the weight and encumbrance system for UFO:AI.
The idea is that the weight of the soldiers equipment affects them in
different ways depending on their strength.

## Weight

- All items have assigned a weight value, this is given in kilograms.
- The maximum weight a soldier can carry, in kilograms, is equal to
  their strength.

## Encumbrance

Encumbrance is applied in three stages:

- Light weight: The soldier is carrying 20% or less of his/her maximum
  allowed load, soldier will receive maximum amount of TUs, this is the
  'bonus' stage.
- Normal weight: The soldier carries between 20% and 50% of his/her
  maximum allowed load, soldier will receive an average amount of TUs,
  this is considered a standard load and is the 'normal' stage.
- Heavy weight: The soldier has a load of more than 50% of the maximum
  allowed, the soldier is encumbered and will receive reduced TUs, this
  is the 'penalty' stage.

## Technical Details

The current formula to calculate the soldier's TU is as follows:



39 \* ENCUMBRANCE_MODIFIER + SPEED \* 20 / 100

Where ENCUMBRANCE_MODIFIER is 1 for 'bonus' stage, 0.7 for 'normal'
stage and 0.4 for 'penalty' stage.

### See also

[Skills improvement](Skills/Improvement/v2.5 "wikilink")