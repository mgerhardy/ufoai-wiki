Nice Tutorial, Wanderer. I could to help you out if you, say, dont want
to write a certain paragraph or so. Otherwise, heres some proposals:

-The Button "T" (texture browser) is missing where you explain how to
apply textures in the controls section.

-In Mattn's video tutorials, he says corners from two walls should
always be built with two faces coming together, like an "angle
bisector". Shifting edges may be a bit sophisticated, but if thats the
best way to do it a newbie should learn it right from the beginning.

-Somewhere you talk about selecting the whole map or large parts of it
by Shift+dragging. It might be easier to just press i (invert selection;
and then maybe unselect few brushes).

-I would emphasize stronger that one should set level flags for level-1
brushes. I one had a nasty memory allocation error trying to load my
compiled map that disappeared after I set all level flags correctly.
Might have been by chance, but who knows.

--[Xav](User:Xav "wikilink") 20:42, 2 May 2007 (CEST)

## Levelflags

They should be set for level 1, too - otherwise the radiant plugin will
not filter them (they will work in game)
--[Mattn](User:Mattn "wikilink") 22:27, 2 May 2007 (CEST)

------------------------------------------------------------------------

\- the default view always has the texture window open, which is why I
didn't include this. You'd only need this if you use a floating window
configuration.

## Reduce face count

- Not understanding German, I have no idea what Matt says in the
  videos... :) Seriously though, I have absolutely no idea what you're
  talking about here with an 'angle bisector'. Do you mean that the edge
  of the wall should be cornered into the 90 degree turn, so each wall
  would end with a 45 degree angle? This seems overkill... and painful
  when you start thinking about midpoint walls internally, ceilings and
  floors... and also most of the existing maps do \*not\* use that
  technique... So I think I must be misunderstanding you.

<!-- -->

- - see this:

![](Mapping_3faces.png "Mapping_3faces.png")

and

![](Mapping_2faces.png "Mapping_2faces.png")


--[Mattn](User:Mattn "wikilink") 07:44, 4 May 2007 (CEST)

- - Yep, Xav finally got this through my head a little bit ago, but
    thanks for the screens. Martin, this change does nothing unless you
    caulk the edges according to the documentation. If we're going to
    include func_breakables for most walls (so you can pretty much
    destroy an entire building from outside, one of the fun things to do
    in UFO), we don't want 'non-drawn' edges. Is this worth it?
    --[Wanderer](User:Wanderer "wikilink") 17:14, 4 May 2007 (CEST)

<!-- -->

- - Imo it is worth it. If you make something func_breakable (e.g. a
    wall) you should not make it the hole wall (it's ok for windows,
    imo) - you should keep some brushes, it should look like a real
    break, not like just a removed wall (do you know what i mean - or
    should i do a shots again) --[Mattn](User:Mattn "wikilink") 19:01, 4
    May 2007 (CEST)

<!-- -->

- - No, I understand what you mean by the 'real break', such as the
    tutorial in 'wall breaks' that recently went up, I assume. The only
    way I've seen in the current editor to do that is to have an
    overlapped brush. The full wall breakable at a much lower level then
    the broken brush (if the broken piece is breakable at all). The way
    I've imagined this is having a corner 'post', some 'broken' pieces
    to show the wall blown out, and then a nice flat wall over the top
    of the broken point. More faces, more draws, massive file size
    because of overlap. Since you're da boss and believe this is worth
    it, I'll introduce it when I introduce caulking, or I'll introduce
    caulking earlier. As Xav said, if this is to be the 'standard', it
    should be introduced early and used often. I still can't see the
    overwhelming benefit, but hey, I just got here. (Damn those
    newbies!!!) --[Wanderer](User:Wanderer "wikilink") 21:21, 4 May 2007
    (CEST)

## Other

\- Inverting: Nah, it's more along the lines of... hm... open up the map
with all the ships on it and attempt to select just the cabin by
shift-dragging. You end up with the ocean, pieces of the boat, and a few
extra brushes. Certainly not an 'invertable' scenario. I'll have to
figure out a way to explain myself better there.

\- Level 1 flags: Yes, I mention they should always set them, but I
didn't want to lie to them regarding if they'd appear or not (thinking
that not setting a flag would make it invisible, like a nodraw). I'll
add some extra to this when I re-edit the doc.

--[Wanderer](User:Wanderer "wikilink") 23:41, 3 May 2007 (CEST)


I meant, when you get to a point where two walls come together, you drag
the edges of both of them so they have a 45° angle at the end. That way,
you can 'save' one face per 'corner'. I don't know if thats a real
improvement and I don't know if this is done in most maps. Maybe Mattn
could comment on that?

Overkill - for mapping? I don't think so... takes just a few clicks per
corner... Anyway, when three walls come together it makes no more sense,
so mostly has no relevance for floors and ceilings.
--[Xav](User:Xav "wikilink") 00:15, 4 May 2007 (CEST)


Ah, okay, I understand what you mean by the angles now... yes, I did
understand you. I'm not sure it's that important, honestly. You can just
'caulk' the invisible face so it doesn't have to draw, and it's built
into the editor as the Best Method. I'm not sure if we want to do that
however once we start including more func_breakables, so I didn't chase
this down. Also, I don't understand how you'd save a 'face'. The end 90
deg face would just be turned....

<!-- -->



I agree that Martin's verdict on this would be best. However, I see it
adding a ton of work for very little gain. You'd also have the
mathmatics behind the calculation for the additional angles adding to
render time from what I understand of the modeling. I just don't know.
--[Wanderer](User:Wanderer "wikilink") 00:27, 4 May 2007 (CEST)

<!-- -->



Well as I said I don't know how big the impact is either, but you
definitely have one face less to draw (e. g. 10 instead 11 if you
combine to walls/brushes like that). I would understand if you leave it
away for a beginners tutorial. Lets just wait for Martins opinion...
--[Xav](User:Xav "wikilink") 01:06, 4 May 2007 (CEST)

<!-- -->



'eh, I could see it, kinda. I just can't see a heavy level of impact and
according to the documentation on GtkRadiant, the walls are still drawn
unless you apply the caulking feature, so 'hiding' the extra face does
nothing for you unless you do other things. We'll see if it's that
important to Martin. --[Wanderer](User:Wanderer "wikilink") 01:54, 4 May
2007 (CEST)


The caulking feature is a feature for Quake, and doesn't apply here.
There is no texture that I'm aware of for UFO:AI that will not draw the
wall. Oops.


That's an option for the map compiler or the renderer - if a face isn't
visible at all, it must not be drawn (at least there is space for
optimizations). But the more important part (at least at the moment) is,
that texturing a wall is not that much work - you don't have to align 3
but only 2 faces. One could say that this is a minor thing, but believe
me it mustn't be a minor thing if you ever retextured a huge brush
amount. In every case it is not a must have, but a cleaner way of
mapping. --[Mattn](User:Mattn "wikilink") 14:02, 13 May 2007 (CEST)