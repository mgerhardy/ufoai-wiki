## General

Tags are attachment points for other models. They are stored in a
separate file besides the model with the file ending *\*.tag*.

We have exporters for the following model software:

- [Blender](Modelling/Blender#MD2-TAG_Script "wikilink")
- [3DSMax](Modelling/3DSMax#Export_tag_file "wikilink")

We have importers for the following model software:

- [3DSMax](Modelling/3DSMax#Import_tag_file "wikilink")

### Characters

We are using *tags* for [character
models](Modelling/Character_Animation "wikilink") to tell the engine
where to place the head and the weapons and where the floor for the
model is. For characters we need animated tag files. That means, if the
character moves the hand, the tag for the hand (either tag_rweapon or
tag_lweapon, see below) has to move, too.

List of tags we need for characters:

- tag_floor (only for internal usage - for calculating the other tags
  positions)
- tag_head
- tag_rweapon
- tag_lweapon

### Weapons

Besides characters our weapons can have a tag assigned to determine the
position of the muzzle particle.

List of tags we need for weapons:

- tag_muzzle

[Category:Modelling](Category:Modelling "wikilink")
[Category:Contribute](Category:Contribute "wikilink")