## General

![](export_md2_skins_3dsm.jpg "export_md2_skins_3dsm.jpg") Our models
need skins of course - these skins are images in jpg, png or tga file
format. They should be in the same directory as the model (the
[md2](md2 "wikilink")) (somewhere below . You should enter the skin path
as . The game will know to look in the same directory as the model for
any jpg, png or tga file with that filename. The dimensions of these
images should always be power of two.

### Fileformat

To change the filenames of the textures or the amount of available skins
you maybe (depends on the model format) have to edit the model files.

To change the filenames of the textures or the amount of available skins
you have to edit the [md2](md2 "wikilink") files.

There is a perl script available for that in called . With this tool you
can change the texture sizes, upgrade the number of skins & change
skinnames.

You need a Perl distribution to be able to execute the script. A good
one for Windows would be .

Be careful. The tool/script is not able to downgrade the number of skins
in the [md2](md2 "wikilink") file, just to upgrade them. To downgrade
this number you have to edit byte 20 with a Hex-Editor (see md2
file/header definitions).

## Links

- [Modelling](Modelling "wikilink")
- [md2](md2 "wikilink")
- [.md2 File Format Specification (new)
  (tfc.duke.free.fr)](http://tfc.duke.free.fr/coding/md2-specs-en.html)
- [.md2 format description and implementation for C++ including the
  entire file architecture
  (tfc.duke.free.fr)](http://tfc.duke.free.fr/old/models/md2.htm)

[Category:Contribute](Category:Contribute "wikilink")
[Category:Modelling](Category:Modelling "wikilink")