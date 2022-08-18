## General

I started this page so we can discuss specific license-related topics
and issues. Licensing may not be of interest to a lot of the people
playing UFO:AI, but it has great impact on the development, distribution
and last but not least the "free"dom of the game.

We have a short summary of licenses we plan to use for all code &
content of UFO:AI with is located on the [License](License "wikilink")
page.

Every code or content that is licensed under a fully compatible license
as the ones listed on the [License](License "wikilink") page should not
be a problem to use in UFO:AI.

Everything else needs to be confirmed/checked.

If you find any code or content that you believe is not covered by a
supported license (or has no hint where it comes from) please speak up.

Personal note: I ([Hoehrer](User:Hoehrer "wikilink")) am aiming for the
game to be distributable in the main repository of the
[Debian](Debian "wikilink") [Linux](Linux "wikilink") distribution. Not
because I want to have it as a package for my distribution (which is a
nice side effect btw :)), but because they have quite strict rules when
it comes to licenses. If we can get it in *there* we can get it into
virtually any other distribution as well.

## Creative Commons Sampling Plus 1.0 License

@mattn: Actually I think the ambient bird sound (, acquired from
[here](http://freesound.iua.upf.edu/samplesViewSingle.php?id=17517))
'may' be a problem in terms of usage, but I'm not sureabout that.


'fixed' in r14177 --[Mattn](User:Mattn "wikilink") 19:56, 23 January
2008 (CET)

To quote the license ([Creative Commons Sampling Plus 1.0
License](http://creativecommons.org/licenses/sampling+/1.0/)) it uses:
*You are free: To perform, display, and distribute copies of this whole
work for **noncommercial purposes** (e.g., file-sharing or noncommercial
webcasting).*

This is in contrast to version of the GPL (or non-restrictive CC)
license we use (commercial use is allowed as long as the rest of the
terms is met as well) and I don't know if this might prevent UFO:AI to
be incorporated in several distributions.

On the other hand we have the part where it says: *You are free: To
sample, mash-up, or otherwise creatively transform this work for
commercial or noncommercial purposes.*

As much as I'd like to add these things I also don't want to have UFO:AI
*not in the main repositories of several of the free
[Linux](Linux "wikilink") distributions*. This would be a big
disadvantage in terms of our own distribution of the game.

Is there anybody who can tell us how the these licenses would influence
the distribution of UFO:AI?

The question above aside ... we need to at least credit the artist(s) by
name (not just a link to the place where we found it in the svn logs) if
we include this sound as to the "Under the following conditions:" part
of the used license here. This will spare us the searching afterwards if
e.g. the page suddenly vanishes etc... Not to speak of the "For any
reuse or distribution, you must make clear to others the license terms
of this work." part, so the license used for the file needs to be made
clear as well.

--[Hoehrer](User:Hoehrer "wikilink") 10:28, 13 February 2007 (CET)

To summarize my own thoughts on this ... the license allows us to
include sound samples (or generally content) under the [Creative Commons
Sampling Plus 1.0
License](http://creativecommons.org/licenses/sampling+/1.0/) as long as
we "creatively transform" it (what would this mean for the sounds we
include?) for use in UFO:AI and credit the author correctly. I may be
wrong since I'm far from being an expert in this field.

--[Hoehrer](User:Hoehrer "wikilink") 11:56, 13 February 2007 (CET)

Quoted from
<http://creativecommons.org/licenses/sampling+/1.0/legalcode> (the full
legal text of the license)

    ...
       a. Re-creativity permitted. You may create and reproduce Derivative Works, provided that:
             1.

                the Derivative Work(s) constitute a good-faith partial or recombined usage employing "sampling," "collage," "mash-up," or other comparable artistic technique, whether now known or hereafter devised, that is highly transformative of the original, as appropriate to the medium, genre, and market niche; and
             2.

                Your Derivative Work(s) must only make a partial use of the original Work, or if You choose to use the original Work as a whole, You must either use the Work as an insubstantial portion of Your Derivative Work(s) or transform it into something substantially different from the original Work. In the case of a musical Work and/or audio recording, the mere synchronization ("synching") of the Work with a moving image shall not be considered a transformation of the Work into something substantially different.
    ...

If we really use the sound 1:1 as provided by the creator I think the
only thing we can build upon is the "*You must either use the Work as an
**insubstantial portion of Your Derivative**...*" part of the
license.The UFO:AI background sounds (all of them together being the
derivative work ... but it is pretty far-fetched.

--[Hoehrer](User:Hoehrer "wikilink") 12:19, 13 February 2007 (CET)

## CC Noncommercial

Does anybody know how a "noncommercial" Creative Commons license relates
to e.g. the license guidelines of the Debian distribution. i.e. can
stuff with that license be shipped with Debian?
--[Hoehrer](User:Hoehrer "wikilink") 13:54, 24 July 2007 (CEST)

- It can not. To quote: The maintainers of the Debian GNU/Linux
  distribution do not believe that even the Creative Commons Attribution
  License, the least restrictive of the licenses, adheres to the Debian
  Free Software Guidelines due to the license's anti-DRM provisions and
  its requirement in section 4a that downstream users remove an author's
  credit upon request from the author.\[6\] As the other licenses are
  identical to the Creative Commons Attribution License with further
  restrictions, Debian considers them non-free for the same reasons.
  There have been efforts to remove these problems in the new version
  3.0 licences, so they can be compatible with the DFSG.\[7\] As of July
  2007, it remains to be seen if version 3 of the Attribution and
  Attribution-ShareAlike licenses will be approved by Debian.
  - see also [cc version3 to cover debian people
    claims](http://wiki.creativecommons.org/Version_3#Debian)
  - personaly i do not think that we should care about debian in such
    case :-P--[Zenerka](User:Zenerka "wikilink") 15:11, 24 July 2007
    (CEST)

## See also

- [License](License "wikilink")
- [Licenses in UFO:ai
  (base/)](http://phidev.org/~dino/ufo/html/index.html)