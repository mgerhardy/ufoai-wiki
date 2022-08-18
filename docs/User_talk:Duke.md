- In regard to the UGV TODO. I will attempt to sum up what I believe is
  necessary for UGVs to be included in the game. Some of this may
  already be implemented, and there may be things that are missing or
  need fleshing out.
  - Art: GUI support, in terms of dropship assignment, UGV equipment and
    display/handling on the battlescape (including the selection of
    boxes in mid-air).
  - Code: Pathfinding support for 2x2 units and flying units. This is at
    least partly done - what's the status?
  - Code: Support for differentiating between soldiers and regular UGVs.
    They occupy different spaces in the dropship and are not
    interchangeable in this regard. See
    <http://ufoai.ninex.info/wiki/index.php/File:Assignment.png>
  - Code: Allow UGVs to fire properly, meaning that the point of origin
    should be placed at the UGV's weapon barrel.
  - Code: Miscellaneous UGV related changes to scoring, autoresolve,
    experience, summaries, etc.
  - Models: separation of turrets and frames.
  - Models: Animations, including turret rotation and barrel
    inclination, death, movement, etc.

--[BTAxis](User:BTAxis "wikilink") 23:44, 19 June 2010 (UTC)

Pathfinding support for 2x2 ground units is in place, but untested and
disabled. I'm very uncertain if the flying code will work.

I see 4 milestones:

- skirmish minimum
  - automatic assignment of one UGV as the 8th soldier
  - some default equipment for the UGV
  - NO turning turret, NO correct origin for firing
- skirmish expanded
  - assign it as the \*9th\* soldier
  - adjust muzzle height
  - add turret control
- campaign
  - variable \# of UGVs per mission
  - dropship assignment, UGV equipment
  - changes to scoring, autoresolve, experience, summaries, etc.
- full support
  - 2x2 spawnpoints on all maps

We have a few maps with 2x2 spawnpoints, eg. fighter_crash.map. I tried
to automatically assign an UGV to the team, but failed. Then I was
distracted...

([Duke](User:Duke "wikilink") 20:44, 20 June 2010 (UTC))

africa now has 2x2 entities, too - and the skirmish game mode is
updated - you are now able to spawn ugvs. have fun with it ;) please
also see css.displayHeavyEquipmentList - this is something that should
be fixed, extended or removed.

`--`[`Mattn`](User:Mattn "wikilink")` 13:26, 26 June 2010 (UTC)`

The next ToDos:

- Spawnpoints
  - Not all the maps have 2x2 spawnpoints. It will be needed to test
    pathfinding to have at least one point per map.

  - The existing spawnpoints are not always configured correctly (like
    the one Mattn fixed for fighter_crash in r31866). Is there a nice
    way to check them before doing a rollout to all maps ? Edit: there
    aren't so many. I'll do that.

  - Is there a minimum for the number of spawnpoints for all maps ? A
    maximum ? If so, how do we transport that information to the
    equipment screen ?
    - farm heracles has only one 2x2 spawnpoint
    - farm raptor too
    - harbour map too

<!-- -->

- Skirmish setup
  - The number of soldiers is persistent, the number of UGVs is not.
  - The UI allows to set up 8 soldiers plus 2 ugvs, totalling 10
  - Entering battle with 7 soldiers and no ugv: 8th button is greyed,
    but hovering over it displays the 7th soldier. Edit: of the
    previously shown soldier (can be any).

<!-- -->

- battlescape
  - the ugv model is not displayed where pathfinding thinks it is.
    Should be in the middle of the 2x2 box.
  - the 2x2 cursor is centered around the position of the model
    (probably a consequence).
  - the ugvs carry normal weapons ?? ie. plasma/laser rifle ?
  - we'll also need a specialized inventory screen. Or what's the
    holster of a ugv ;)
  - IR goggles on an ugv ?
  - ugv can turn, but not (yet) move of course.
  - shooting a civilian causes return to menu

<!-- -->

- crouching
  - current UI allows ugvs to crouch/uncrouch, consuming TUs
  - What's the height of an ugv ? The model looks about the height of a
    crouched human. The height has a big impact on
    - LoS
    - LoF
    - pathfinding
  - An easy way out might be to consider ugvs as 'perma-crouched',
    taking the movement penalty for crouching.

--[Duke](User:Duke "wikilink") 21:04, 25 August 2010 (UTC)

## Priorities

Some thoughts about priorities in a project. Imagine the following
scenarios:

**Scenario 1:** The complete devteam has left the project. Some rookie
devs took over. After a year or two you come back and find
\*everything\* is broken. In which order will you start to fix things ?

**Scenario 2:** There is no UFO:AI project, but you want to create one.
Where do you start ?

Not too surprising, the order is the same in both scenarios. Arguably
you could also start with prio 2 (The Plan) in scenario 2 and write it
down on paper.

Note that some very important aspects like 'internal communication',
'external communication', 'organization' and 'marketing' are not slotted
in here because they depend on other factors (size of dev team, \# of
users) and can not be compared directly to the priorities listed below.

Also note that priorities are applied on a per person basis. That is, if
the project has a 'prio n' problem and you are not the person to do
anything about it, you can of course move on to a 'prio n+1' problem,
unless the guy(s) working on the 'prio n' problem ask you to keep
certain areas of the project constant (eg. feature freeze).

### 1. development tools

Compiler, debugger, profiler, IDE, repository, various editors and test
infrastructure for all supported platforms.

**Reason:** without your tools you can't accomplish anything.

### 2. code structure

Design, file structure, coding & doc guidelines, technology & gameplay
strategy

**Reason:** Without a good plan, your work will end in chaos. At least
in much duplicate work.

### 3. checker tools

Compiler warnings, cppcheck, valgrind, helgrind, doxygen and automated
tests (cunit).

**Reason:** many tools can sometimes give you hints to hidden bugs. So
before starting to hunt a bug, you will want to make sure that none of
the tools already 'knows about the bug'. This is best achieved if there
are no warnings whatsoever from all the tools.

### 4. patches

Keep the patch tracker clean !

**Reason:** It saves us some work on bugs & features. And although
applying a patch can be more work than fixing the bug yourself, it's
worth it, because that's what 'prospect devs' usually start with.
Ignoring the patches they send in for too long discourages them.

### 5. bugs & features

That's what it's all about. We want to add features to our application
and make sure that it works. My personal reflex here is "kill ALL the
bugs before adding the next feature". But that's definitely WRONG. Users
tend to accept a certain amount of bugs if they get the desired
features. And they don't accept if the dev team spends ages to fix some
bugs that 95% of the users never encountered. So it's a rather delicate
\*balance\* here, and I can give no rules for that balance.

I only know that

- both bug reports and feature request should be \*treated\* somehow.
  That is, assigned to a dev that is qualified to at least accept or
  decline it.
- bug reports with high priority values are really more important than
  new features
  - In some cases, though, bugs require specialist knowledge (renderer,
    pathfinding) or we simply don't know how to fix them. In these
    cases, feature addition shouldn't necessarily be held up while we
    wait for a fix. Also, developer motivation is a factor in a
    volunteer project. I fully support your push to get the team more
    focused on bug-fixing. But people need to enjoy their work some,
    too. --[H-hour](User:H-hour "wikilink") 03:46, 23 November 2012
    (SAST)

## Deficits

### 1. development tools

We have no easy to use and install IDE for Windows. Don't know about the
other supported platforms.

### 2. Strategy

We have no written-down overall strategy. Our current strategy seems to
be "fix a little here, add a little there, release". With one exception:
the gameplay strategy seems to be to move the endgame further into space
step by step and add the features necessary for that.


you've seen our [TODO/Roadmap](TODO/Roadmap "wikilink")?
--[Mattn](User:Mattn "wikilink") 23:04, 2 December 2012 (SAST)


I'd call it the overall ToDoList, but good enough for me as far as
gameplay is concerned--[Duke](User:Duke "wikilink") 00:45, 3 December
2012 (SAST)

For myself at least, my strategy is not to push forward the endgame. I'm
more interested in improving what we've got within the current framework
-- improving maps, adding key mechanics, ensuring the game is balanced,
user-friendly and engaging to play. There are still a lot of gameplay
issues that I'd rather see resolved before we start lengthening the
end-game. --[H-hour](User:H-hour "wikilink") 13:03, 3 December 2012
(SAST)

### 3. Checker tools

We have many of them, starting with the compiler warnings. But nobody
seems to be willing to care much.

### 4. Patches

As of today (Dec 2nd, 2012) we have 17 open patches, some of them dating
back 2.5 years.

### 5. Bugs & Features

We manage to fix nearly as many bug tickets as are reported. So the
number of open bug tickets tends to increase slowly, but steadily. We
should find a way to make it drop.

## Solutions

As long as I'm the only one who dumps his brain here, this section
should rather be called 'Potential Solutions' or 'Proposals'. But if you
guys join in, I'm positive that it **will** deserve the title
'Solutions' ;)

The first thing is to make sure that we all at least roughly agree with
the order of priorities I lined out above. So please vote right here:

### 1. development tools

If mattn agrees to make github the location for the official C::B
package, I think I can (with some help from Sandro and maybe Nate and
ShipIt as guinea pigs) get the best out of C::B.

### 2. Strategy

#### 2.1 Design

We have recently renamed all our .c files to .cpp. That implies that we
want to move to C++. But the code is still \>95% plain C. So how will we
get there ?

One approach can be to change all our typedef'd structs into class X {
public:...} . Then slowly but surely add getters and setters and move
the suitable code to member functions. But there is a high risk that the
structs our ancestors designed will not result in a good class
hierarchy. So we need at least a rough design for the major entities to
get an idea if an existing struct would fit in there as a class.


No - there is no need that everything must be a class - not everything
is meant to be a class. We switched to c++ to use it where it is
reasonable and useful. We didn't switch to use it everywhere just
because we can. And beside that, a struct is also a class with only
public members and methods. Oh, and plain C is also C++ in most cases ;)
--[Mattn](User:Mattn "wikilink") 08:48, 7 December 2012 (SAST)

#### 2.9 Gameplay Strategy

I'm not sure what you're hoping for in this section -- do you want a
full development roadmap out to whenever? To be honest, I think it's
pretty unlikely. First, the amount of developer time we have is so small
that I think few people want to spend much of that time on organizing.
Second, most of the half-a-dozen or so active developers are interested
in developing the features they're interested in. We've all got
different priorities. I'm very grateful when someone is willing to
investigate and work on something that I'm interested in, but I know
that only happens when that other person is interested themselves.

I'm not sure we'd have any luck with a roadmap. Look at the UGV
development. None of the developers have a clear, convincing and
compelling vision for this feature, which is why it has languished in
the kind-of-but-not-quite WIP state for years. This is compounded by the
fact that each of us finds different elements of the game compelling --
we prioritize problems/features differently.

Good features need strong advocates. Throwing "psionics" or "implants"
or "ugvs" onto a roadmap is no replacement for someone who really
strongly believes in what these things bring to the game, and has the
patience to write out good proposals, discuss the game mechanics, and
motivate people to work on them. Without this, the game accumulates
content and features that "exist" but don't "work".

I think a roadmap (with x, then y, then z ordering of features) needs
someone capable of reaching a consensus among the team on priorities --
and this isn't just the kind of consensus where we accept it, but one
where we're really motivated to add something new to the game. We're all
volunteers. Without the sense that this or that feature really is
important, it will be hard to steer all the developers in one direction.

I don't think this is necessarily a bad thing. Somehow we manage to
cover all the elements we need, even though we're all sometimes tending
our own little area in the game. I'm not sure if I have contributed
anything to this section, now that I'm done. Perhaps we need a new way
of organizing our work, or thinking about our long-term goals?
--[H-hour](User:H-hour "wikilink") 01:18, 7 December 2012 (SAST)


I already stated that the 'Roadmap' is good enough for me. And 'add what
you are interested in' is a valid strategy for OSS projects. But
gameplay is only a small part of the
strategy.--[Duke](User:Duke "wikilink") 01:34, 7 December 2012 (SAST)

### 3. Checker tools

Compiler warnings: The -Werror (=treat warnings as errors) is there for
a reason. It indicates that warnings can be dangerous and that they can
be avoided. We might be able to ask occasional contributors to deal with
them. This way they can apply their knowledge without learning too much
about the ufoai code.

CppCheck: How serious do we take the CppCheck output ? Can we safely
ignore it ? The interesting red lines in the output are embedded in ten
times more white lines that seem to be useless. So the first step should
be to filter the output. Most of the red lines are of one of 5 types. If
we decide that a certain type must be ignored, it should be filtered
away too.


I check the output from time to time and it already helped to optimize
and even to fix a few bugs in the past. So why should we not use it?
Open the output and search for "(error)"
--[Mattn](User:Mattn "wikilink") 08:59, 7 December 2012 (SAST)


So our policy is: take care of (error), but ignore (style),
(performance), (warning), (portability),...
?--[Duke](User:Duke "wikilink") 14:00, 7 December 2012 (SAST)

Doxygen: Do we really want doxy-style comments in our code ? I do. I
never use the html output, but I like the structure and the tool to
check if everything is documented. But if the Project Leader commits
code that is free of doxygen, the question arises if doxygen is still
project policy.


We can of course comment a function like: "const char
\*getAircraftName();" with "returns the aircraft name" but I really do
think that speaking function/method names and speaking variable names
are more needed than comments for each step. I do agree (and If you
remember it, I was also the person who pushed this a few years ago) that
doxygen style comments are needed, useful and wanted where it makes
sense. But I also think that comments that are too specific (and we
had/have some of them) like "in function CL_DoSomething in file
whatever.cpp we do stuff" with this comment being in a totally unrelated
header file.... well, they just are useless and tend to get out-of-date
faster as light. But to be honest it's not my goal to let doxygen run
warning/error free. It's my goal to comment the code (where reasonable).
Function comments should also not describe the inner mechanics of the
function - because this might change without the comment being changed.
And this situation is worse that no comment. It should only describe the
interface contract for the caller. The input parameters should be
explained, too. But it also helps a lot if we have typedefs or enums for
the ints that are given to a lot of the functions/methods. Being
typesafe and using speaking names is often more than enough. I don't
need a comment for "aircraftType_t type" with "@param\[in\] type This is
the aircraft type". --[Mattn](User:Mattn "wikilink") 08:59, 7 December
2012 (SAST)


I immediately agree that speaking function/method names and speaking
variable names are the best choice in the first place. Unfortunately
most devs I know (and they go by the hundreds) usually fail to find
speaking names that also speak to \*other\* devs.

I also agree that "@param\[in\] aircraftType This is the aircraft type"
\*seems\* to be useless to the dev who is familiar with the ufoai code
IF and only IF there is a full documentation at the decl of the typedef,
which you can reach by rClicking in your IDE. But...

- at least one of us (geever) doesn't use an IDE


I really think that vi can resolve those things, too. emacs or whatever
he is using is able to do the same. And if someone is using ed why
should we work around this?

- by leaving out the doxy for that param you give away the chance to let
  doxygen check for the completeness of the documentation
- an experienced but newbie to ufoai dev might wonder what the type
  actually is. Is it UFO vs. Phalanx ? or dropship vs. fighter ? or
  Stiletto vs. Firebird vs. Stingray ? or crashed vs. landed ? So
  "@param\[in\] type (Stiletto, Firebird, Scout, Harvester,...) may give
  him the right idea and might even save me the rightclick ;)

Looking at the aircraftType_t in our code I was amazed (thx for the
example btw) to find that it's something different from the above. Guess
;)--[Duke](User:Duke "wikilink") 14:00, 7 December 2012 (SAST)


Then there should be no comment to work around a bad name. And i also
disagree about adding the names to the comment. They might change, get
extended or whatever - and you are out of date.
--[Mattn](User:Mattn "wikilink") 16:38, 7 December 2012 (SAST)

### 4. Patches

Assigning all patches and then applying or dumping them should be the
easiest of all tasks listed here.

### 5. Bugs & Features