## Technical Hurdles

This proposal requires a significant amount of coding, to ensure that
all battlescape actions that cost TU are reported to the UI *when and as
they happen*. It will also need to execute a UI function *when and as
reaction fire is taken*, so that the UI can highlight which soldier
panel is taking the shoot and remove it afterwards. Here is a list of
actions that would need to be reported:

- Move
- Crouch
- Turn in a direction
- Fire weapon
- Pickup/drop equipment
- Use headgear
- Take reaction shot

Currently movement only updates TUs when movement has completed.
Ideally, we would see the TU update as it moves across each grid.

## Embedded UI

aDuke suggested that we could instead use small bars above each target's
head in the battlescape. If this is possible, it would be ideal,
although aDuke pointed out that the UI elements would not be
customizable via the scripts if done this way.