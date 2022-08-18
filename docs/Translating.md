<div style="border:2px solid red; background:black; padding:1em;">

**Please do not use a normal text editor, use \>= 1.5 instead!**

</div>

## General Information

We use the system for our translations. You don't even need to know how
it works, but the link is a good reference for certain rare situations.

- Grab the latest file for your language from our repository.
- Open it in poedit. Translate. Save.
- Submit a with the zipped po file as attachment.

That is the easiest and at the same time the worst way to do it. It only
works if you are sure that you are the only person working on that
translation. Otherwise it can produce merge conflicts and/or duplicate
work.

So if you have the chance,

- use GIT to get the repository
- create git patches and submit those
- try to devide your work into logigal chunks and make separate patches

## HowTos

### Create a new language file

If there is no translation for your language (ufoai-xx.po, where xx is
the code for your language) then you need to download ufoai.pot (means
po template).

And in PoEdit there is an option to "New catalog from POT file". Select
the ufoai.pot as template, set initial options, like and start
translating. Save as ufoai-xx.po.

If you would like to test your translation in game (before we added it
into the repository) - PoEdit can compile the po file into a mo. You'll
need to copy the mo file into a specific location into the same
structure other language files are stored in. - You'll need adding a new
entry into the file or create an additional language.ufo with the new
entry.

When you are done (with a part) of the translation you should upload
your po file as a patch to our and add the language.ufo entry in
description or so. You will need to register an account for the
bugtracker if you haven't done it so far for this. (Also attaching file
is available only after submitting a ticket.)

### Dealing with many 'fuzzy' entries

When the UFO gameplay changes, many texts may need adjustments.
Hopefully someone does that to the english version. If he does, all the
affected texts in all the other languages will be marked as 'fuzzy'.
It's very tedious to look through long fuzzy messages only to find that
merely half a sentence was changed.

Here's what you can do:

- get a one year old version of the ufoai-en.po
- load both that and the current ufoai-en.po in your editor (eg. C::B)
- use the editor's find cmd to find the fuzzy message in both files
- copy both messages into WinMerge and compare them

WinMerge can well detect that one changed paragraph, sentence or
sometimes even single character. Unfortunately WinMerge isn't available
on Linux.

## General Rules

Do not try to make the translation better than the original. Make a bug
report or FR to change the original instead, so other languages can
benefit from your improvements.

## Language-specific Style

In probably every language there are certain recurring words and phrases
that can be translated in more than one way, resulting in a slightly
different tone. It is of some importance that the same way is chosen
throughout UFO:AI. So translators can describe those language-related
rules in the following sections. They are of course not in english.

[Bulgarian](Bulgarian "wikilink")

[German](German "wikilink")

## Links

-

- [Po](Po "wikilink")-Files

[Category:Translating](Category:Translating "wikilink")
[Category:Contribute](Category:Contribute "wikilink")