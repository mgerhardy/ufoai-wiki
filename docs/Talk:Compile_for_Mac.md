I think setting the prefix (installation directory) to /opt/local is not
such a good idea, because that is the default place for the macports
installation, which could lead to conflicts between port installations
and libraries installed manually. For unmanaged software packages it
would be better to choose a neutral default, for example /usr/local.

- The wiki was incorrect. The configure script does not override
  \$PREFIX with /opt/local. It uses /usr/local (by default) like all
  other configure scripts I have come across. What it does do is add
  /opt/local/lib to LDFLAGS and /opt/local/include to CFLAGS if
  /opt/local exists. In other words, the configure script is aware of
  where MacPorts installs and tries to automatically find dependencies
  there. Having said that, using make install on Mac OS X is almost
  certainly not going to work correctly for you. It certainly has never
  worked for me. --[Tchristney](User:Tchristney "wikilink") 08:18, 17
  December 2008 (UTC)

There are several severe problems with the instructions for compiling
using Fink and Port when running mac OS X 10.5.5 Intel/Universal.

- You can't build universal binaries using Fink. Period. Fink does not
  support them. If you must build universal binaries you have to follow
  the direction for using MacPorts (or figure out how to build all the
  dependencies as universal binaries - good luck.)
  --[Tchristney](User:Tchristney "wikilink") 08:24, 17 December 2008
  (UTC)

If anyone can compile for mac on or for either ppc or intel, please put
a note here, and ideally update the instructions to match.

- I have had success compiling with MacPorts. I've updated the sections
  of the wiki that I know to be incorrect.
  --[Tchristney](User:Tchristney "wikilink") 08:24, 17 December 2008
  (UTC)

Need the \*.dev versions of various packages installed by Fink and
MacPorts, not the regular packages
--[Doc.Torr](User:Doc.Torr "wikilink") 27 Dec 08

## Clarify "Make macinstaller" please

The page states:

You can have the last steps automated by choosing

make macinstaller

from the root directory, but this will also upload/download stuff and
create an disk-image, which might be not desired in your case.

Would someone who knows what's going on please indicate what gets
upload/downloaded, and just what exactly that step does?

## dylib loading (SDL_mixer)

-dylib_file
@loader_path/Frameworks/smpeg.framework/Versions/A/smpeg:/Library/Frameworks/SDL_mixer.framework/Versions/A/Frameworks/smpeg.framework/Versions/A/smpeg

see
<http://playcontrol.net/ewing/jibberjabber/big_behind-the-scenes_chang.html#SDL_mixer>

might help to fix our problem with no ogg sound


I think this was talking about an issue that was already fixed in
MacPorts.

More likely, we may need to switch to the downloaded official
distribution, rather than the MacPorts distribution -- there were
linking changes made that I am beginning to wonder if MacPorts picked
up. MP is nice for the auto update, but if it does with with
distribution and not with MP, then a bug needs to be filed with MP.

## Making it easier to follow

I got this PM from a newbie to all this:

So, one thing at a time: when I download and copy over the .dmg version
of 2.3, I get a message saying that it's not supported on this
architecture.

Next, the wiki instructions and my limited understanding of them. I'm
basing this on the
<http://ufoai.ninex.info/wiki/index.php/Compile_for_Mac> page. I start
off downloading the four SDL frameworks and copy them over to the main
library/frameworks folder. Then I do what? The layout of the
instructions seems to guide me down to the Without Fink--gettext
portion, since I don't have fink or mac ports, so I downloaded that as
well. From there, I'm looking at the section labeled Compilation, which
starts off with the instruction to run the configure script. At this
point I'm lost--is this configure script something for gettext
specifically? Looking at gettext, I'm not sure how to go about using it
to do anything.

Also, at which point in general does Terminal come into play? From what
I've found, the wiki instructions don't actually say when to use
Terminal, how to use it, or even mention it by name. Are all those
dotted boxes supposed to be Terminal inputs? If so, I haven't been able
to utilize those commands. So, at this point, my understanding of the
process fails before a log of any kind could be helpful. Sorry if it
seems like I'm being unbearably dense or obtuse, but this is way outside
my field of experience thus far, and so I feel like I need remedial
guidance on how to get 2.3 working.

You and I are so used to this that we forget what new people go through.

## Explain the "disc image" vs. "non-universal binary" way.

The "General" section right now just has a statement with no explanation
on why you'd want to do one thing rather than the other. A newbie coming
here will just be sorely confused, as there's no explanation of what a
disc image or a binary or compiling is - the vast majority of people
just want to play the game.[Parjlarsson](User:Parjlarsson "wikilink")
18:18, 2 May 2011 (CEST)