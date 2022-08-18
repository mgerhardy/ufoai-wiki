## General

UFO:AI supports multiplayer in different scenarios. You can play 1on1,
2on2 and so on. Even cooperative games are possible. But you have to be
aware, that not all maps are coop playable - or maybe only with a
specific team. Some smaller maps will have the spawn points of the
aliens near the spawnpoints of multiplayer team 1 or 2 - so no real coop
gameplay comes up here.

## Lobby and IRC

- We have a multiplayer lobby implemented ([IRC](IRC "wikilink")) since
  version 2.1 of UFO:AI. Use it to talk to others that might want to
  play a game. Make sure, that you changed your nickname in the options
  menu before you connect - otherwise you will be *unnamned*.

<!-- -->

- If you find that no-one is around to play when you visit the channel,
  then try using a different [IRC](IRC "wikilink") client. Set your
  client to alert you when someone uses words like multiplayer, multi,
  MP, play, game etc. For example, in Chatzilla this is done by using
  preferences/global/lists/Stalk words.

## Setting up a dedicated server

See the [dedicated server](Manual/Dedicated_Server "wikilink") article.

## networking

First check your machine can listen on port 27910.

- set your firewall software to allow incoming TCP connections on port
  27910.
- if your computer sits behind a router, then you have to tell that too.
  your router connects to your internet service provider (ISP), which
  will assign the internet protocol (IP) address which you appear to
  have to the rest of the internet. on the inside of your local area
  network (LAN), you have a different IP address, which is assigned by
  your router. When your router gets an incoming connection, it will not
  know which computer on your LAN to send it to, unless you tell it. It
  uses the port number (27910) to identify it, then if you have set the
  correct rule, it will forward it to your PC (port forwarding), by IP
  address. If there are several computers on your LAN, it be useful to
  set your router to always assign the computer you want to use as a
  server the same IP address (it can do this by using your computer's
  network card's physical or MAC address). Then your port forwarding
  rule will always go to the right IP address.
- to reiterate: your LAN IP is not the same as the IP the outside world
  would have to use to connect to your server. To find out how your
  computer appears to the rest of the world you could use a site like
  this. [<http://whatismyip.com/>](http://whatismyip.com/). If you are
  using IRC, the /whois command will often tell you the IP of a user
  (including yourself).

## Starting the server

Then you can start the server in two ways - from within the game (server
is a client) or as a dedicated server with only a command prompt to
enter commands in.

- From within the game
  - Enter the multiplayer menu
  - [Assemble a team](Manual/Multiplayer/Assemble_a_team "wikilink")
  - Hit the create button to create the server
  - Select the map and the options to play with from the menu (see
    [Multiplayer cvars](Multiplayer_cvars "wikilink"))
  - Hit the start button
  - Your team will enter the map's battlescape. You should now wait for
    an opponent to join your game.
- As a dedicated server
  - Select the gametype (type to get a list of all defined gametypes and
    their [cvars](cvars "wikilink"))
  - Type to get a list of all available maps in
  - Choose a map and type

## Connecting to server

- [Assemble a team](Manual/Multiplayer/Assemble_a_team "wikilink")
- If the server was made public it should be displayed in the server
  list automatically - if not, check your firewall settings
- Even if the server is not shown up (and your firewall settings are ok)
  you two more chances to connect to this server
  - Open the [console](console "wikilink") and type
  - Select **Internet** in multiplayer menu and use the box at the
    bottom to specify the ip to connect to
- Clicking on a server in the list should display details about the
  game. At this point you can join the game by clicking the Connect
  button displayed on the left-hand-side.
- Once connected you will enter the map in battlescape mode. You may
  have to wait for your opponent to finish his turn.
- Note: just like in any mission, you will not see your opponents until
  you bump into them on the map. You can use the talk button to chat to
  your opponent however.

## Links

- [Multiplayer cvars](Multiplayer_cvars "wikilink")

[Category:General](Category:General "wikilink")
[Category:Multiplayer](Category:Multiplayer "wikilink")
[Category:Manual](Category:Manual "wikilink")