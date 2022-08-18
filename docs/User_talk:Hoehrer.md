## Upgrading wiki version

Hi, the Atom feed of the Recent changes page is outputing html instead
of wikisynthax. I think it might have to do with the mediawiki version.
would you mind upgrading to a newer version? We at
[freegamedev](http://freegamedev.net/) are planning to build a
feed-aggregator for wiki edit feeds of free software games.
--[Qubodup](User:Qubodup "wikilink") 02:24, 20 February 2008 (CET)

Updating the mediawiki version was planned to be done some time ago, but
we ran into (still unsolved) problems with character sets so it was
never finished (on a side-note: help here is welcome). But I'll have a
look at the php atom-code this looks like a simple bug at first glance.
--[Hoehrer](User:Hoehrer "wikilink") 20:22, 22 February 2008 (CET)

Ok, I think i've got the problem fixed. The atom links now displays the
html instead of dumping it's source.
<http://ufoai.ninex.info/wiki/index.php?title=Special:Recentchanges&feed=atom>

For anyboy who's interested in the fix to MediaWiki 1.5.6:

    --- Feed.php.original   2006-03-01 00:00:00.000000000 +0100
    +++ Feed.php.fixed  2008-02-22 21:35:48.000000000 +0100
    @@ -263,8 +263,8 @@
            <modified><?php print $this->formatTime( $item->getDate() ) ?>Z</modified>
            <issued><?php print $this->formatTime( $item->getDate() ) ?></issued>
            <created><?php print $this->formatTime( $item->getDate() ) ?>Z</created><?php } ?>
    -
    -       <summary type="text/plain"><?php print $item->getDescription() ?></summary>
    +
    +       <summary type="html"><?php print $item->getDescription() ?></summary>
            <?php if( $item->getAuthor() ) { ?><author><name><?php print $item->getAuthor() ?></name><!-- <url></url><email></email> --></author><?php }?>
            <comment>foobar</comment>
        </entry>

--[Hoehrer](User:Hoehrer "wikilink") 21:38, 22 February 2008 (CET)

Cool! You mean Wikisyntax, not HTML btw ;)
--[Qubodup](User:Qubodup "wikilink") 09:10, 24 February 2008 (CET)

Actually no, I definitely meant HTML in that sentence ... HTML that has
MediaWiki syntax embedded, but still. If the HTML source is displayed
instead of parsed&rendered it is displayed alongside the wiki-syntax
(i.e. the garbage we've seen). But now the HTML is parsed into HTML
tables (and some other formatting like that fancy CSS stuff) which
contains the wiki-syntax :D --[Hoehrer](User:Hoehrer "wikilink") 23:29,
25 February 2008 (CET)


I think I get it ^^ anyways, the "wiki watch" is working now, [check it
out](http://wikiwatch.freegamedev.net/)! (I hope this is not totally
useless :) ) --[Qubodup](User:Qubodup "wikilink") 00:57, 26 February
2008 (CET)

It's definately a nice idea :) Only problem I see is that you use our
transparent white logo (on a white background) :) Might be better to use
something like this [1](http://ufoai.sourceforge.net/img/logo.png)
(cropped of course). --[Hoehrer](User:Hoehrer "wikilink") 14:23, 26
February 2008 (CET)

## I have a question

I tried to propose some ideas to Winter, but I haven't heard from him in
months. Is he just busy or did I not propose the ideas correctly?

--[Brainy19](User:Brainy19 "wikilink") 4:27 PM, 13 March, 2008

No, he's around, if you contact him on IRC or the forum your should get
an answer pretty soon. Wikis are not a good place to do discussions in.
;) --[Hoehrer](User:Hoehrer "wikilink") 20:13, 14 March 2008 (CET)

## Research Tree Data and translation

Hi, i've found that sometimes the "Research Tree Data" is copied as-is
when translating an entry, and some other times is omitted.

It says "don't translate", but should it be omitted or copied without
modifying? --[Barbanegra](User:Barbanegra "wikilink") 20:43, 16 March
2008 (CET)

*Omitted*, these texts are often very much outdated or plain wrong, so
any work put into them is a waste of time.
From what I know of how the script to transfer the text into ufoai
works - whenever something is copied 1:1 from the original text (without
translating) that shouldn't actually be done - it just confuses other
people. Either put a translated version in there (maybe missing some yet
unfinished parts, but that is nothing a simple text-hint can't solve)
there or nothing at all. --[Hoehrer](User:Hoehrer "wikilink") 23:59, 16
March 2008 (CET)

## es and es_ES columns

Hi, in some categories there seem to be two columns for spanish language
(es and es_ES) but in some others there is only one (seems to be
"es_ES"). Also, at Equipment category, entries from both columns
complement each other, so one has what other lacks.

Are both intended to be used or just one of them?
--[Barbanegra](User:Barbanegra "wikilink") 20:55, 16 March 2008 (CET)

Actually I'm at a loss here, from what I know of the language code one
part indicates the land and the other the (if existing) local actual
language/dialect (maybe spanish vs. catalan or something along that
line?) --[Hoehrer](User:Hoehrer "wikilink") 00:08, 17 March 2008 (CET)

I'm not sure, I thought "es" could be spanish from South America
countries (es_ES is spanish from Spain) but reading them I've found
little differences, none related to these. Perhaps there was an
intention to create two separate spanish translations which hasn't
progressed much. I'll put work on es_ES (the one I know best).
--[Barbanegra](User:Barbanegra "wikilink") 01:15, 28 March 2008 (CET)

## lock a page

Hi, could you give me the rights to lock pages in the danish language.
thanx [Joedalton](User:Joedalton "wikilink")