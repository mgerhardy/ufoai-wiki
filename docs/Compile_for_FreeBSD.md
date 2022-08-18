## General

Make sure you have all dependencies installed on your system. After you
checked out the source from our
[repository](Getting_the_source "wikilink"), you only have to run
`./configure` and install all the missing packages. After that run
`make` to compile the game.

## Install packages

Create a file with the following content named e.g. :

`*default host=cvsup3.freebsd.org`
`*default base=/var/db`
`*default prefix=/usr`
`*default release=cvs tag=.`
`*default delete use-rel-suffix`
`*default compress`
`ports-all`

check if you have /usr/ports directory created

`csup -g -L 2 this.file`
`cd /usr/ports`
`make fetchindex`
`make search name=PACKAGE`
`cd /usr/ports/something/PACKAGE && make install clean`

[Category:Coding](Category:Coding "wikilink")