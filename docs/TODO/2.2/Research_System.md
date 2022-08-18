There are several things we need from the research system and UFOpaedia
that are not functional or only partially functional in the current 2.1
trunk. They are:

- (priority high) Pre- and post-research descriptions. Partly done in
  2.0, but has not been tested thoroughly. Are the messages displayed
  correctly at any time?

  - (priority low) Pre- and post-research descriptions are currently not
    displayed properly in UFOpaedia. Articles without pre-research
    descriptions still have the post-research button displayed on the
    top bar of the interface, which is not clickable but still there to
    confuse the player when there is only one article. This button
    should be hidden for articles without a pre-research description.

    - Done, please test if the behaviour is correct now.
      --[Hoehrer](User:Hoehrer "wikilink") 19:17, 4 February 2007 (CET)
    - It is not. I see no "real" research description (non-pre one)
      button. where it should be located?. Also I've just noticed that
      the articles in UFOpedia puts "DATE" header as it is, i mean,
      there is no real research-date there (sf bug \#1599131 part two).
      Not sure if it is not postponed to next release till we get real
      e-mail style messager--[Zenerka](User:Zenerka "wikilink") 00:34,
      20 February 2007 (CET)
    - Ok, it is fixed now (r6421), thanks
      Hoehrer--[Zenerka](User:Zenerka "wikilink") 11:36, 21 February
      2007 (CET)

  - (priority low) The layout of the UFOpaedia is old and obsolete, and
    requires significant revision and restructuring. A larger text area
    for the main article and much smaller stat boxes are a must. Only a
    tiny percentage of the stat boxes is actually used, even in the most
    stat-verbose items, and they cut down the size of the text box by a
    huge amount. Stat boxes should be shrunk and made scrollable for
    proper display.

  - Nicer formatting for research entries (e.g. graphical email header,
    coloured or formatted text etc ... whatever is possible)

- (priority medium) Timer dependency to enable researchable techs after
  some time has passed since their dependencies have been researched.
  Not done.

  - (priority low) The ability to attach cutscenes to the timer.
    Cutscenes should launch the player into into a video or -- in the
    absence of video -- an interlude screen with text like the game
    intro.

All the open changes listed on top are enough to fill a whole release
with no other things on the list ... What isn't finished when the rest
of the game is done will be postponed to the next release. Unless we get
some people doing some of the needed redesign (codewise and in smaller
parts gui-wise). --[Hoehrer](User:Hoehrer "wikilink") 19:17, 4 February
2007 (CET)

[Category:Contribute](Category:Contribute "wikilink")
[Category:TODO](Category:TODO "wikilink")
[Category:Development](Category:Development "wikilink")