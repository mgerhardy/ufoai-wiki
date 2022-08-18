## General

PK3 files are normal zip files that we use in UFO:AI to organize the
game data. You can add new files on your own containing your customized
data. The pk3 files are loaded in order and doubled files will be taken
from the last loaded pk3 file. That means that if you want to provide a
mod for something, you can just overwrite a file that is also in another
pk3 file and give your own modded pk3 files a name that is lexically
ordered after the pk3 filename where the original file is included.
Example: you can name your pk3 file to ensure that is loaded after .

You don't have to create pk3 files to add your modded files to the game!
Files are not part of a pk3 file have a higher priority for the game.
That means that if you extract a file from the pk3, modify it and don't
put it back into the original pk3 - your changes will still be in the
game and the original file is ignored. This also means that you only
have to create a pk3 file if you want to do a release of your mod. If
you plan to add your data (see [License](License "wikilink")) officially
into the game, you can even skip this step and just send us your files
(included source files for e.g. sounds, textures \[with layers\] and map
sources).

## Example

Let's assume you are planning to provide a
[script](UFO-Scripts "wikilink") patch. You have two options here,
provide a new file because you are providing new content, or override an
existing file because you are patching existing stuff.

In both cases you have to create your pk3 file like this.

`-ufos/`
` \-ui/`
`   \- newUIScriptFile.ufo`
` \- updatedAndAlreadyExistingScriptFile.ufo`

In the case you are only providing new content you can name your pk3
file whatever you want. In the case you are providing updated content
you have to ensure that the existing content is overridden. This can be
achieved by choosing a pk3 file name that is lexically ordered after the
pk3 file with the content you are trying to override. E.g. the content
you are trying to override is in the file - all you have to do is to
name your pk3 file . Every gamer that will now copy your pk3 file into
this user directory (see [FAQ](FAQ "wikilink")) or into the game
installation folder (if he is an administrator on his machine) can
override the original content with your patched version.

[Category:Mapping](Category:Mapping "wikilink")
[Category:Contribute](Category:Contribute "wikilink")
[Category:UFO-Scripts](Category:UFO-Scripts "wikilink")