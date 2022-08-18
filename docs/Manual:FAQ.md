## Manual

We have a [manual](Manual "wikilink") available that gives more
information on everything from installing to playing UFO: Alien
Invasion.

## Gameplay

- **Hiring soldiers**
  - More candidates become available at the end of each month. Scroll
    through the list using the mousewheel. More candidates are supplied
    if you use an easier difficulty level. More candidates are supplied
    if you are doing well and keeping your funding bodies happy.

<!-- -->

- **Saving from within the battlescape...**
  - ...is not allowed. This is because saving after killing an alien and
    loading after losing a soldier is not in the spirit of the game. It
    takes the fear away: and you should be afraid.
    [1](http://ufoai.ninex.info/forum/index.php?topic=937.0)
- **building a new base**
  - You can find "Create installation" button on the sidebar (GeoScape).
- **Why can't I use the medium alien armour?**
  - Alien armour is only for aliens! At version 2.2.x, the best armour
    useable by PHALANX is the nanocomposite. There will be more armour
    available when more dev work is done (need more 3D artists). See
    [Equipment/Armour](Equipment/Armour "wikilink").
- **Is there an easy way to compare weapons, and learn more about
  them?**
  - See [weapon tables](weapon_tables "wikilink"). Includes link to
    table with list of skills for different skills/firemodes.

## Gameplay for veterans

Notes for veterans of *UFO: Enemy Unknown* (also known as *Ufo Defense*
or just *X-COM*)

- **Where are the proximity mines?**
  - Not implemented yet (at version 2.3.x).
    [2](http://ufoai.ninex.info/forum/index.php?topic=1286.0) They will
    be implemented for sure.

<!-- -->

- **Why can't I destroy all the terrain like in X-COM?**
  - The 3D engine that is used to make UFO:AI (a modified Quake2 engine)
    does not support fully destructable terrain. There are plans to add
    some destructible items (furniture, barrels...), but even that will
    be a lot of work (mapping, models, particle-effects etc.) See also
    [3](http://ufoai.ninex.info/forum/index.php?topic=636.0) and
    [4](http://ufoai.ninex.info/forum/index.php?topic=673.0) for more
    details. Please do not post on the forum asking for fully
    destructible buildings. This has been discussed to death. If,
    however, you are are a coding genius and can implement this within
    the quake 2 based engine, and leave it running fast...

<!-- -->

- **The time units (TU) for reaction fire (RF) makes no sense**
  :\* The RF system mimicks most of the RF-features of X-COM. You can
  reserve TUs in your round which will not be used up but can be used
  for RF in the enemy turn.
  There is now an advanced system in place to reserve various things
  (e.g. the RF reservation as mentioned already or stuff that can be
  suede in the same round such as crouch/stand-up). There are still some
  rough edges (i.e. not all of this is usable yet) but time will help us
  iron them out.

## Multiplayer

- **What port is UFO:AI using?**
  - TCP 27910 since 2.2
  - you can also check whether your server is listed here:
    <http://ufoai.ninex.info/ufo/serverlist.txt> - if not, check your
    firewall settings.

<!-- -->

- **Nobody can connect to my server - what am I doing wrong?**
  - Make sure, that you have opened the game port in your router

<!-- -->

- **The server doesn't show up in the serverlist - what can I do?**
  - Again make sure, that the game port is opened in your router
    configuration - also make sure, that the [cvar](cvars "wikilink")
    has a value of 1. This can also be done in the multiplayer menu.
    Activate the public option in the menu when you create the server.
  - more networking tips in the [Multiplayer](Multiplayer "wikilink")
    article.

<!-- -->

- **Is there a mapcycle available?**
  - Yes, there is a mapcycle available. Just have a look in the UFO:AI
    installation directory. There is a with comments inside.

<!-- -->

- **Versions**
  - The players (clients) and server must use the same version of
    UFO:AI.

<!-- -->

- **Maps**
  - A checksum is calculated to ensure that all players (clients) are
    using the same version of the map. Maps compiled on different
    systems may have slightly different checksums (due to differences in
    floating point operations). So, for multiplayer, stick to installers
    (from
    [5](http://sourceforge.net/project/platformdownload.php?group_id=157793)
    for example) or mappacks (from
    [6](http://mattn.ninex.info/download/)).

## Compiling Maps

(If you just use an installer, do not worry about this.)

- Does it take a long time?
  - Yes, but if you use one of the make files in the repository then
    only the maps that need updating will be compiled.
- Can maps compiled for one OS or system be used on another?
  - Yes, and note the maps answer in
    [\#Multiplayer](#Multiplayer "wikilink")
- It says "Could not load image pk3 (/base/0pics.pk3)", does that
  matter?
  - No, it will load images from the normal filesystem, instead of from
    the archive file.

## Controls

- **How can I turn the soldier's direction without moving him?**
  - Position the 3D cursor on the terrain in the desired direction, then
    press Right MouseButton or use . See also the
    [Keymap](Manual/Keymap "wikilink"). See also [Key
    Bindings](Manual/Key_Bindings "wikilink")

<!-- -->

- **What console?**
  - The more you mess with UFO:AI, the more likely it is you will hear
    references to the console. If you hit then the console should come
    up. Press to return to the normal GUI. There are many console
    [commands](commands "wikilink"). The console is logged in a text
    file from the time you start UFO to when you quit. This is
    overwritten the next time you run it. See the
    [General](#General "wikilink") item below to find the path.

<!-- -->

- **What is a CVAR?**
  - Console variable [7](http://en.wikipedia.org/wiki/Cvar). For example
    to set your nickname in for multiplayer you can go to the console
    and type "/name iamthegodofhellfire" or whatever. There are many
    other [CVARs](Cvars "wikilink") which can be set.

## Common bugs

There is a file called distributed with all UFO:AI packages listing
major known bugs for this release. Please read it to avoid unneccesary
bug reports :)

Check our tracker [8](http://ufoai.org/bugs/) and the forum
[9](http://ufoai.ninex.info/forum/index.php?board=7.0) for a complete
list of known bugs.

Really common ones are listed here to save you time. If you have found
something new then tell the team about it (see [Bugs](Bugs "wikilink")).

- **Broken savegames**
  - Savegames generally do not work between versions. If you are
    compiling trunk look out for the giveaway commit messages.

<!-- -->

- **Estimates of hit probability are distinctly fishy**
  - Hit probability estimates are not great when your target has partial
    cover. The true calculation is done by the server (even in single
    player mode)

<!-- -->

- **Non-English characters in Windows' User profile**
  - If the User's folder contains Non-English (Non-Latin?, Non-ASCII?)
    characters the game will stop responding upon trying to enter a
    mission. A possible workaround is to create a new profile.

## General

- **Where can I find the savegames, screenshots, config.cfg and
  ufoconsole.log?**
  - This depends on your OS:
    - Linux:
    - Windows XP:
    - Windows Vista:
    - Windows 7:
      - In Windows 7 the \AppData folder is hidden by default.
    - Windows98 - german version:
    - MacOSX: (prior to 2.3)
    - MacOSX: (\>= 2.3)
  - Screenshots are in those directories in , savegames are in

<!-- -->

- **Game seems to be untranslated (missing texts). What did I miss?**
  - This may be due to a missing translation - generate a new one on
    your own and send it to us - see
    [translating](translating "wikilink") article (also see [available
    translations](available_translations "wikilink"))...
  - ...or the system can't find the locale (the installed language
    file). You can use the [cvar](cvars "wikilink") to set your language
    (see for valid languages) or you can copy the directory to e.g. the
    language prefix you need.
    - Linux users must have the locale installed they are trying to use
      in the game. You can try to set another locale via the environment
      variable *LANG*. Start ufo with `LANG=en; ./ufo`

<!-- -->

- **Under which licence is this game released?**
  - GPL and Creative Commons (mainly we can modify, adapt, build upon,
    and use commercially)

<!-- -->

- **What are the system requirements that I need to play UFO:AI?**
  - See [System requirements](System_requirements "wikilink")

<!-- -->

- **How can I contribute?**
  - See [contribute](contribute "wikilink")

<!-- -->

- **When will the game be ready?**
  - When it's done. No seriously, there will never be a fixed release
    date (for any given version), when the game is ripe enough to make a
    new release it'll be done.

<!-- -->

- **Where are the scripts (\*.ufo), maps, models, ...? (also what is a
  \*.pk3?)**
  - if you used an installer look in UFOAI-<version>/base/\*.pk3.
  - you can copy the \*.[pk3](pk3 "wikilink") somewhere (so the game
    still works!), rename them zip and unpack.
  - on windows you can just use
    [7zip](http://sourceforge.net/projects/sevenzip/), which works it
    out for itself.
  - \*.ufo scripts contain a lot of useful information.
    [10](http://ufoai.ninex.info/wiki/index.php/UFO-Scripts)
  - all the same information is also available to anyone from the
    subversion repository.
    [11](http://ufoai.ninex.info/wiki/index.php/SVN)

<!-- -->

- **How to make screenshots ingame?**

  The default [keybinding](Keybindings "wikilink") for ingame
  screenshots is

  It's defined in the file like this:


      bind F12 "screenshot"

  Screenshots are saved in a directory called . This directory is
  located inside your UFO:AI settings directory (depends on the
  operation system you use). See also
  [Manual/FAQ#General](Manual/FAQ#General "wikilink").

## Links

- [Running the game](Running_the_game "wikilink")

[Category:General](Category:General "wikilink")
[Category:Manual](Category:Manual "wikilink")