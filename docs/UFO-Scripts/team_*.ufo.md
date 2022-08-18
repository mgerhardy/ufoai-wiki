### Datatypes

- **size**: [V_INT](V_INT "wikilink") The field size on battlefield
- **hit_particle**: [V_STRING](V_STRING "wikilink") The particle that is
  shown if an actor from the given team was hit
- **name**: [V_TRANSLATION_STRING](V_TRANSLATION_STRING "wikilink") The
  name of the team (translatable)
- **race**:
- **robot**: [V_BOOL](V_BOOL "wikilink") Team is for robots
- **armour**: [V_BOOL](V_BOOL "wikilink") Team can carry armour
- **weapons**: [V_BOOL](V_BOOL "wikilink") Team can carry weapons
- **templates**: List of [character
  templates](UFO-Scripts/team_templates.ufo "wikilink")
- **names**: A list of actor-names for the given language. Uses
  sub-lists as follows:
  - **neutral**:
  - **female**:
  - **male**:
  - **lastname**:
  - **female_lastname**:
  - **male_lastname**:
- **models**: A List of model-paths with the following syntax:

<path/to/model/relative/to/base/models>` `<model_file_name>` `<model_head_filename>` `<skinnumber>

The skinnumber is always refering to the reference texture saved in the
header of the body model file. The heads have at present time usually
just one skin defined. To change the filenames of the textures or the
amount of available skins you maybe (depends on the model format) have
to edit the model files.

Model file name & model head filename are always refering to md2 files,
the references to the path, the name & the amount of skin-textures are
stored inside the header of the md2s.

The model file name is the name for the unarmoured model. If the actor
was equipped with armour, the path is extended with the values from the
particular [armour definition](UFO-Scripts/armour.ufo "wikilink").

If e.g. a taman is equipped with the alien light armour (which has the
armour path "light") the path is extended by the engine to . Thus the
*bodyXX* and *headXX* [md2](md2 "wikilink") files will be used from .

The skin that is used here must be available in the head *and* the body
model.

Another example:

`models {`
` neutral {`
`  aliens/ortnok body01 head01 0`
`  aliens/ortnok body01 head01 1`
` }`
`}`

An Ortnok that is not equipped with any armour will use the models from
(both body01.md2 and head01.md2) - either with skin 0 or 1.

Now let's equip the Ortnok with some armour (depends on the equipment
definition you are using for the mission you are spawning). The path
where the engine will load the model from now depends on the armour item
that was equipped. Imagine we added the **armour_light_alien** item to
the Ortnok inventory. The path the engine will search for and is now
(notice the **light** in the path name).

Uses sub-lists as follows:

- - **neutral**:
  - **female**:
  - **male**:

- **actorsounds**: A list of soundfiles for the various sound-events.
  Syntax

<sound-event>` `<path/to/soundfile/soundfile/relative/to/base/sound>

Uses sub-lists as follows:

- - **neutral**:
  - **female**:
  - **male**:

Possible sound-events are:

- - **hurtsound**:
  - **deathsound**:

## Example

`team shevaar`
`{`
`   name            "_Shevaar"`
`   tech            "rs_alien_shevaar_autopsy"`
`   race            shevaar`
`   armour          false`
`   size            1`
`   hit_particle    blood`

`   names {`
`       neutral {`
`           Akrokk`
`           Mkeek`
`           Rniuk`
`       }`
`       lastname {`
`           "Uk Kronok"`
`           "Np Zlrok"`
`       }`
`   }`

`   models {`
`       neutral {`
`           aliens/shevaar body01 head01 0`
`           aliens/shevaar body01 head01 1`
`       }`
`   }`

`   actorsounds {`
`       neutral {`
`           hurtsound aliens/shevaarhurt01`
`           hurtsound aliens/shevaarhurt02`
`           hurtsound aliens/shevaarhurt03`
`           hurtsound aliens/shevaarhurt04`
`           hurtsound aliens/gurgle`
`           hurtsound aliens/shevaarcall01`
`           deathsound aliens/slithering`
`           deathsound aliens/shevaar`
`           deathsound aliens/shevaardeath01`
`           deathsound aliens/shevaardeath02`
`       }`
`   }`
`}`

[Category:UFO-Scripts](Category:UFO-Scripts "wikilink")