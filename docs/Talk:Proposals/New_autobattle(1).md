I have two concerns with such a complicated proposal. First, if we find
that it is giving us unexpected results at some stage -- performance is
too good or bad -- it will be incredibly difficult to debug/fix. We
already ran into this problem with our old reaction fire mechanism,
which was unreliable but we couldn't quite figure out why. Second, this
entire mechanism will be invisible to the player. With so many factors
involved, the player could face some serious problem -- maybe his play
style is leading to bad results for automission, maybe his weapon
choices are bad, etc. But the player will have no idea what the problem
is. With all this happening behind the scenes, it raises the possibility
that the player will feel cheated when he performs poorly but doesn't
understand why. Whenever the player is responsible for an outcome in the
game, it should be clear how he can influence the outcome. Autoresolve
will always have this problem, so it can not be avoided. But it should
be reduced wherever possible. --[H-hour](User:H-hour "wikilink") 00:04,
31 May 2012 (SAST)


I can't say I agree with you on the "complicated" part. It's just a
dozen of arithmetic formulas. I think it's not even a problem to provide
"behind the scene" button to show all the calculations, so we can easily
check the reason for every number. And of course in DEBUG build we can
provide the whole story, so that every calculation step could be
checked.

As for letting know the player why his result was unsatisfactory...
Well, in proposed mechanics soldiers die only for two reason: if they
run out of ammo (which already wasn't accepted by geever) or they got
too many wounds. In any case we can tell this to the player. I think the
results screen for AB should be different as for normal battle. Not only
"killed phalanx, survived phalanx", but "your soldiers got N wounds,
soldiers died of wounds -- XXX, you soldiers shot N rounds, soldiers
died because they were left barehanded -- XXX, do you want to replay
mission manually?". This way player will know what exactly is wrong with
his play style, why his soldiers are dying during AB. And I have to
note, that if player have soldiers died from "got too many wounds" in
the stats, it means that either he allows his soldiers to be wounded
much during the normal battle, and then dying soldiers is not something
out of ordinary for him, or he just didn't play missions manually for a
long time, so his stats lowered. In the latter case the reason probably
should be noted to the player.

[Morse](User:Morse "wikilink")


It was mentioned twice now you want to give the player the chance to
'auto' the mission, and replay it manually if the outcome is
unfavorable? And probably more by 'Retry' over and over again? Which of
those will go into the stats? [ShipIt](User:ShipIt "wikilink") 20:14, 31
May 2012 (SAST)


Do you have any doubts in that question? I mean it's obvious which
outcome will be used generally, like for items and exp of soldiers,
right? Why stats should be somehow different from that?
[Morse](User:Morse "wikilink")


Well. My guess is the last one (the best one) will count. My concern
here is you are about to create a 'Auto Win' situation.
[ShipIt](User:ShipIt "wikilink") 07:32, 1 June 2012 (SAST)


First: and what's so bad about that? If the player won all previous
battles it's only logical that he'll win again.

Second: wins are different. Soldiers will spent more ammo and will get
more wounds than if played manually, and statistically - that's all what
matters.

And finally: the current system is much, MUCH more abusable in a sense
of "Auto Win" (in every other possible sense also, but that's the
different story). With my system to "auto win" the players needs to
perform good during ground missions constantly (as soon as he stops, his
"auto" results will gradually became worse). With the current system to
"auto win" the player needs just to reload the game a couple of times
just before the battle. He can even forget about ground missions at all,
as it doesn't change anything: a couple of save/loads - and you're the
boss! [Morse](User:Morse "wikilink")