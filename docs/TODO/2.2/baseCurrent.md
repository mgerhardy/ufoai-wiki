# Status

## baseCurrent

- cl_actor

- all other files (no list yet)

## curTeam

**The last patch (with some minor tweaks) is in svn since Revision
10484** --[Hoehrer](User:Hoehrer "wikilink") 18:48, 1 August 2007 (CEST)
<small>
<s>Update: 5th patch: <http://pastebin.ca/641807> - seems to work most
of the time ... actor-changing with 1-9 keys does not re-center though
.. might be some deeper problem.</s>
--[Hoehrer](User:Hoehrer "wikilink") 16:31, 1 August 2007 (CEST)
<s>Update: 4th patch: <http://pastebin.ca/641793> - Some cleanup in
character\<-\>teamlist sync, still needs heavy testing.</s>
--[Hoehrer](User:Hoehrer "wikilink") 16:14, 1 August 2007 (CEST)
<s>Update: 3rd patch: <http://pastebin.ca/641653> removed nearly every
curteam and teamnum stuff.</s> --[Hoehrer](User:Hoehrer "wikilink")
13:27, 1 August 2007 (CEST)
<s>Update: new patch: <http://pastebin.ca/641594>''' "teamSize" is no
pointer anymore.</s> --[Hoehrer](User:Hoehrer "wikilink") 12:29, 1
August 2007 (CEST)
<s>Big patch - testing welcome: <http://pastebin.ca/641578></s> </small>

- Make sure all singleplayer and multiplayer teams behave as intended.

- cl_basemanagement.c \<-- this is one of the most annoying files when
  it comes to curTeam usage IMO

- cl_actor \<-- no big deal. Nice function GetActorChr takes care of all
  problems.

- cl_team.c \<-- the only curteam stuff that is useful in here is the
  one for the display-list (to display one type if empl). But this can
  be done via a "`static empl_list[]`" the earlier the better.

- cl_menu: MN_Drag - I think this has to share its info with cl_team AND
  the battlescape ... that might get more tricky. The foundation is
  layed out, see the todo comments in the file. The main thing todo is
  to use the display-array as cl_team.

- cl_aircraft.c \<-- one of the last things to change I think

- cl_basemanagement.h \<--The very last thing ;)

<small>

- cl_main.c it's just "CL_SendCurTeamInfo"

- g_client.c \<-- Nothing to do in here, it's just a comment.

- g_client.h \<-- Nothing to do in here, it's just a comment.

</small>

# baseCurrent pointer

baseCurrent pointer is global variable which is used in most of client
code. The purpose of this pointer is to point to currently selected
base.

# the problem

Unfortunately currently it is used not only for the functions handling
things with currently selected bases, that is menus, but also it is used
in many core functions regarding aircraft selecting, team generating,
equipment management and so on. As the result, this pointer very often
does not point to the currently selected base, as it should be, which
leads to make things out of sync.

# the solution for singleplayer

Code cleanup and rewrite. :-)

## mission handling

When aircraft reaches mission, cls.missionaircraft is being set to this
aircraft. In every case of misison handling, use:

    base_t *base = CP_GetMissionBase();
    aircraft_t *aircraft = cls.missionaircraft;

to get both aircraft used in given mission and its homebase. Every usage
of baseCurrent and baseCurrent-\>aircraftCurrent should be replaced by
the code above.

## team handling

Cleanup in cl_team.c is needed. Almost every function in there, which
handles teams (actors generating, names generating, equipment
generating, equipment handling) uses baseCurrent and/or
baseCurrent-\>aircraftCurrent.

# the solution for multiplayer

Currently multiplayer team handling assumes that we use first base
(gd.bases\[0\]) and first aircraft (AIR_AircraftGetFromIdx(0)) and this
aircraft is aircraftCurrent (base-\>aircraftCurrent). In the long run
removing usage of aircraft and base in multiplayer is needed - base and
aircraft info is not needed for multiplayer. In the short run, make sure
that cl_team.c functions which are being used in team generation, are
able to handle things without baseCurrent and
baseCurrent-\>aircraftCurrent set. See
cl_team.c/CL_MultiplayerEnvironment_f() as a current ugly workaround.

# the desired behaviour

baseCurrent SHOULD have base value assigned ONLY when we are selecting
the base on the geoscape and entering it. baseCurrent SHOULD be used
only in any base menu (building menu, research menu, transfer menu,
etc), because it indicates CURRENTLY SELECTED base. Usage of baseCurrent
in every "core logic" function which handles stuff not regarding given
menu should be replaced by something else.

[Category:Contribute](Category:Contribute "wikilink")
[Category:TODO](Category:TODO "wikilink")
[Category:Development](Category:Development "wikilink")