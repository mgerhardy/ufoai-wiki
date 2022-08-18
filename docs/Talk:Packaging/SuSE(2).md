I think this is a good point for discussion / requests / wishes for
changes for the packages I create for you.

So if anyone has a bug in the RPM Packages for SuSE, write it down here!

## Problem (by Anonymous user)

I'm not sure if this problem occurs for everyone, but I had to set the
working directory of UFO by hand by editing the entry in the start
menue.

*`Solution`*
`This was a problem (when entering the first mission, the screen remained black) `
`and was solved. get the latest ufoai binary rpm (version 2.0rc6-7.1 IIRC) `
[`DimStar`](User:Dimstar "wikilink")` 15:17, 14 December 2006 (CET)`

## ufo-data

Hi,

I'm just interested, why the ufo-data rpm is so huge. \>600MB!

[84.160.22.239](User:84.160.22.239 "wikilink") 02:05, 14 January 2007
(CET)

`Answer`
`Where did you try to get this RPM? The one I did (available on repos.opensuse.org/games:/data/Generic is 225MB`
`The Map-Pakcs take quiet some space. Most likely, this size will reduce towards a final package, `
`as different things might be used or not used`
[`DimStar`](User:Dimstar "wikilink")` 11:58, 14 January 2007 (CET)`

Thanks for your answer. I used my openSuse YAST2 GUI to install the
file. As you can see, the filesize is appearently more than 600MB, as
shown in the YAST2 GUI.

![Image:OpenSuse Yast2 Size of
ufoai-data.png](OpenSuse_Yast2_Size_of_ufoai-data.png "Image:OpenSuse Yast2 Size of ufoai-data.png")

But if I check my Installation-path
(http://software.opensuse.org/download/games:/data/Generic/noarch/),
then I have a filesize of 225MB. I'm not so familiar to rpm, but maybe
the data is compressed inside an rpm an the YAST2 GUI shows the
uncompressed filesize? Or is it the required place for installation?

Regards

(now as User) [E^(nix)](User:E^(nix) "wikilink") 14:28, 15 January 2007
(CET)

`Answer`
`Ah, now I see what you mean. Thanks for the screenshot. YaST indeed shows the uncompressed size required for the installation.`
`The RPMs themself contain a bzip2 compressed cpio archive (just for some technics)`
`There are very much graphic data inside this game. hopefully this does not case any problems to you.`
[`DimStar`](User:Dimstar "wikilink")` 15:25, 15 January 2007 (CET)`

Oh no, that's no problem. I just thought something could possibly have
went wrong during package-creation. Thanks for the technics :-) I'm very
interested in such things. [E^(nix)](User:E^(nix) "wikilink") 19:23, 15
January 2007 (CET)