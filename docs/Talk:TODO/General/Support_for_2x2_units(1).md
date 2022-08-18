Hello all,

I am just getting back into this game (and by the way, it rocks since
2.0!), and happened to see this page. I have done code like this before,
and am working on an overhaul of your pathing code. As an example, I
have condensed the Grid_MoveMark code from about 188 lines to 150, and
at least 25 of those are a huge block of comments I added describing
what my code is doing. I use math based loops, which actually use less
code and perform fewer checks than the old code. This math based
approach would allow for even larger (3x3 anyone?) actors. I have also
edited Grid_CheckForbidden to use this math based approach, and am
looking at Grid_MoveCheck because it duplicates a lot of what
Grid_MoveMark does. I may be a little in getting a tested patch to you;
I'm just reinstalling my C compiler for Windoze.


Of course - would be nice to see the patch when you are done. we are
currently discussing stuff like that on our internal mailinglist. if you
are interested, tell us your mail adress and we will add you to the
list. there are some other things we have to keep in mind concerning
pathfinding - if you find the time, please join our irc channel and as
me (mattn2 in irc) about this topic. --[Mattn](User:Mattn "wikilink")
13:58, 14 February 2008 (CET)

<!-- -->


I agree with mattn. Every help in that part of the code is much
appreciated. The current code is partly very old code and partly
modified to support 2x2 units by me (very hackish at that, i just wnated
to get it to work at all), so any streamlining already helps a lot :)
--[Hoehrer](User:Hoehrer "wikilink") 20:48, 14 February 2008 (CET)