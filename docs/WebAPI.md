## General

The game allows players to share their data with other players or just
backup their savegames and teams. For this to work, they need a forum
account and log into it from within the game.

## Webserver

The current implementation of the server side is written in php and is
located in .

### Authentication

We are using a SimpleMachines API for doing the authentication against
the forum user credentials.

## Client

The client side code is located in . There are some console commands
available for the file management. They are all prefixed by *web_* (as
well as the available [cvars](cvars "wikilink")). Available commands
are:

- web_uploadcgame
- web_deletecgame
- web_downloadcgame
- web_listcgame

Their usage should be printed to the game console when they are issued
without any parameters.

Every user could theoretically run it's own webserver with the webapi
installed and just redirect the webapi calls by changing the cvars:

- web_cgamedownloadurl
- web_cgamelisturl
- web_cgamedeleteurl
- web_cgameuploadurl

These [cvars](cvars "wikilink") can contain placeholders for the current
selected [cgame](ClientGame "wikilink"), the userid, the category (for
example savegame or team) and the file. Available placeholders:

- \$cgame\$
- \$userid\$
- \$category\$
- \$file\$

An example download url could be:

`h ttp://myserver.com/cgame/$cgame$/$userid$/$category$/$file$`

The corresponding upload url could be:

`h ttp://myserver.com/api/cgameupload.php?cgame=$cgame$&category=$category$`

[Category:Coding](Category:Coding "wikilink")
[Category:Contribute](Category:Contribute "wikilink")