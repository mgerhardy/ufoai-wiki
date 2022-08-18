    <nowiki>
    /*
     * This is a simple spec for a info.ufo file that could be included
     * with each mod project and used to display information in-game
     * about the mod. In addition, an image file thumb.*** could be
     * included in the root directory of each mod to be displayed in-game.
     */
    mod mymod {
        name        "My Mod"
        author      "H-Hour, Mattn"
        version     "1.0"
        ufoai-version   "2.4"   // Which version of UFOAI it was designed to work with
        release-date    "2012-05-08"
        description "This is a mod that makes everything better!"
        website     "https : // example.org"
        license     "GNU GPL 2 or later"
    }
    </nowiki>

I think this will suit us fine for a long period, but if we get to a
more advanced stage with more mods, we can add parameters for defining
type of mod, controlling ownership of mod (if we maintain an online
download center for mods), using a revision number to track whether it's
been changed, other dependencies (other mods), etc.


In this case, i think the main block is useless. And it is technically
not a problem cause we will not using the default parser (cause mods are
not yet loaded). Or at least it should be an anonymous block.
[Bayo](User:Bayo "wikilink") 16:32, 8 May 2012 (SAST)


Sorry, but I don't understand what you mean by "main block".
--[H-hour](User:H-hour "wikilink") 16:45, 8 May 2012 (SAST)


I mean this part "`mod mymod {`", and this part "`}`" are useless.
[Bayo](User:Bayo "wikilink") 16:50, 8 May 2012 (SAST)


Ahh ok, it can be removed. I simply built it this way to mimic our .ufo
formatting, but if it's not needed that is just as good.
--[H-hour](User:H-hour "wikilink") 17:46, 8 May 2012 (SAST)

[Category:Proposals](Category:Proposals "wikilink")