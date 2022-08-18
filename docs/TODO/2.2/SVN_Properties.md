Add properties to svn data files:

[`svn:copyright`](svn:copyright)` list of all authors that were involed`
[`svn:license`](svn:license)`   the exact license the data is placed under`
[`svn:source`](svn:source)`    derived work? source url`

`svn ps `[`svn:license`](svn:license)` "Creative Commons Attribution-Noncommercial-ShareAlike 3.0" David01.ogg`
`svn ps `[`svn:copyright`](svn:copyright)` "David Reeves (Destructavator)" David01.ogg`

- Use `svn proplist -R -v` to show the current properties in the current
  directory.
- there is a script in contrib/scripts named textures.sh which might be
  very helpful, too
- List of directories:

:\* base/models/aircraft/: inter_stiletto and ufo_carrier left

:\* base/models/aliens/

:\* base/models/civilians/

:\* base/models/geoscape/: inter_stiletto.\*, ufo_carrier.\*, and
missile.\* left

:\* base/models/soldiers/: ugv_phoenix and ugv_triax left

:\* base/models/weapons/

:\* base/models/objects/:

:\* base/music

:\* base/sound/weapons: many left

:\* base/sound/aliens

:\* base/sound/misc: klonk\*.wav, plopp\*.wav, big_boom.wav,
metalbreak.wav and glassbreak.wav left

:\* base/sound/ambience

:\* base/sound/footsteps

[Category:Contribute](Category:Contribute "wikilink")
[Category:TODO](Category:TODO "wikilink")
[Category:Development](Category:Development "wikilink")