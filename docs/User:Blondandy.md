# about

- blondandy is Andy Buckle
- born 1977
- work as a radiotherapy physicist

contact: using the sf.net
system.[1](http://sourceforge.net/sendmessage.php?touser=1760416)

the day job:
this[2](http://scholar.google.com/scholar?as_q=&num=10&btnG=Search+Scholar&as_epq=&as_oq=radiotherapy+radiobiology&as_eq=&as_occt=any&as_sauthors=%22AH+Buckle%22&as_publication=&as_ylo=&as_yhi=&as_allsubj=all&hl=en&lr=)
google scholar search should return my work.

# todo

i know how to do this

- test range of levelflags of all brushes to spot brushes that are
  visible when they should not be. warn about brushes that are
  significantly taller than one level or span between levels.
- a test outside of all to check for nodraws that may be visible.

i may know how to do this

- auto brush merging

i have a very vague notion of

- auto reduce-exposed-faces
- make a replacement for FPV, where the viewpoint is behind the actor
  and the view is slightly down, so the view up through the floor thing
  is not an issue.

# my minor contributions

This is here to be an illustration of the righteous path to open source
contribution, and svn right access.

- wrote some java to generate the
  [weapon_tables](weapon_tables "wikilink").
- noticed that the weapon skills had no effect.
  [3](http://sourceforge.net/tracker/index.php?func=detail&aid=1725798&group_id=157793&atid=805242).
- patch to improve to-hit estimate
  [4](http://sourceforge.net/tracker/index.php?func=detail&aid=1727091&group_id=157793&atid=805244).
- patch to make skills increase fast when they are low (20-50) and slow
  down as they approach
  100[5](http://sourceforge.net/tracker/index.php?func=detail&aid=1733849&group_id=157793&atid=805244).
- patch to make combat knife rubbish against armour
  [6](http://sourceforge.net/tracker/index.php?func=detail&aid=1734000&group_id=157793&atid=805244).
- patch so that mouse click turn cancels aiming only on first click.
  second click required to turn.
  [7](http://sourceforge.net/tracker/index.php?func=detail&aid=1750036&group_id=157793&atid=805244)

then I got svn permissions

[<http://cia.vc/stats/author/blondandy>](http://cia.vc/stats/author/blondandy)

- i have worked on the check/fix functions of ufo2map, which are now
  available from radiant

# win tools for ufo:ai development

- \[<http://sourceforge.net/projects/psycle/%5DPsycle>: a
  tracker/sequencer
- \[<http://sourceforge.net/projects/audacity/%5DAudacity>: for messing
  with samples
- \[<http://gimp-win.sourceforge.net/%5DGIMP>: for messing with images
- \[<http://www.blender.org/%5DBlender>: 3D modelling
- \[<http://sourceforge.net/projects/codeblocks%5DCode>::Blocks. get the
  prepackaged version [Code::Blocks](Code::Blocks "wikilink") to make it
  easy
- \[<http://tortoisesvn.tigris.org/%5DTortoiseSVN>: svn client. good
  intro to svn. its a shell extension, tortoiseshell. geddit...
  - its "TSVNCache.exe" process hogs hard drive time. In the settings,
    turn of "icon overlays" to make it useable.
- \[<http://subversion.tigris.org/project_packages.html%5Dthe> tigris
  console svn client. slower to complete tasks than tortoise, but does
  not hog resources when you don't want it to. seems to hang on me quite
  frequently
  - just trunk
        svn co https://ufoai.svn.sourceforge.net/svnroot/ufoai/ufoai/trunk trunk
  - all (a lot!)
        svn co https://ufoai.svn.sourceforge.net/svnroot/ufoai/ufoai/ .
- \[<http://sourceforge.net/projects/poedit/%5DpoEdit>: compile po and
  play trunk. called by code::blocks as a post-build step.
- \[<http://reader.google.com%5Dgoogle> reader: for RSS feeds from
  ciabot [8](http://cia.vc/stats/project/ufoai).
- Chatzilla (Firefox plugin) for IRC. to edit startup use
  "<about:config>" URL and edit
  extensions.irc.networks.freenode.autoperform

[Category:UFO:AI Team](Category:UFO:AI_Team "wikilink")
[Category:Mapping](Category:Mapping "wikilink")