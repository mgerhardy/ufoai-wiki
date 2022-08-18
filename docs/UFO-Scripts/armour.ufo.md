## DataTypes

- **useable**: Parameter that defines which team can use it:
  - **phalanx**
  - **alien**
  - **civilian**

<!-- -->

- **protection**: ("dmgweight" values)
- **normal_steelblade**: is here for the combat knife
- **normal_monomolecularblade**: is here for the kerrblade (and similar
  monomolecular weapons).

It ensures that the superior tech blades are much better against armour
and keeps the kerrblade scary.

- **rating**: ("dmgtype" values) - see [Damage](Damage "wikilink")

## Example

`//weights 100`
`item armour_light`
`{`
`   name        "_Combat Armour"`
`   image       armour/light`
`   type        armour`
`   shape       "0 0 3 4"`
`   center      "0 0 -5"`
`   scale       0.7`
`   price       1400`
`   size        60`
`   armourpath  "light"`
`   useable     phalanx`

`   protection {`
`       normal_light        20`
`       normal_medium       18`
`       normal_heavy        12`
`       normal_spray            9`
`       normal_steelblade           10`
`       normal_monomolecularblade   5`
`       blast               25`
`       fire_medium         15`
`       fire_heavy          15`
`       fire_flamer         1`
`       shock               0`
`       plasma_light        7`
`       plasma_medium       6`
`       plasma_heavy        5`
`       laser_light         18`
`       laser_medium        16`
`       laser_heavy         12`
`       particlebeam_light  7`
`       particlebeam_medium 6`
`       particlebeam_heavy  5`
`       stun_electro        0`
`       stun_gas            0`
`   }`

`   rating {`
`       normal              30`
`       blast               30`
`       fire                20`
`       shock               10`
`       plasma              10`
`       laser               20`
`       particlebeam        10`
`       stun_electro        10`
`       stun_gas            10`
`   }`
` }`

## Links

- [Equipment](Equipment "wikilink")
- [Skills](Skills "wikilink")
- [Damage types](Damage "wikilink")
- [tweak weapons](Equipment/Tweak_weapons "wikilink")

[Category:Equipment](Category:Equipment "wikilink")
[Category:Weapons](Category:Weapons "wikilink")
[Category:UFO-Scripts](Category:UFO-Scripts "wikilink")