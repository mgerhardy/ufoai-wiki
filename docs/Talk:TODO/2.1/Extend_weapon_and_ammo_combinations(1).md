I don't the point here - why not just another ammo definition with some
other values but the same name?


[Mattn](User:Mattn "wikilink") 08:13, 28 January 2007 (CET)

Modifiers in the weapon entry is not good - they would affect other
weapons, too - they should be in the ammo entry imo. something like this
is imageable: **Moved this to
[TODO/2.1/Extend_weapon_and_ammo_combinations#Ammo_modifiers](TODO/2.1/Extend_weapon_and_ammo_combinations#Ammo_modifiers "wikilink")
--Hoehrer**


[Mattn](User:Mattn "wikilink") 08:21, 28 January 2007 (CET)

I think something like that was what winter meant in the quote. As long
as we can get all sort of combination (as listed in [TODO/2.1/Extend
weapon and ammo
combinations](TODO/2.1/Extend_weapon_and_ammo_combinations "wikilink"))
to work without problems, the _way_ of implementation isn't really
important, we just need to make sure we do not need to rewrite/extend it
again in the future. The solution above sounds good to me, but we still
need to solve the issue with combined fire-modes like for grenades ...
so this whole thing is finally
resolved.--[Hoehrer](User:Hoehrer "wikilink") 12:01, 28 January 2007
(CET)

## Comments on Implementation method 1

### firemode buttons

Implementation method 1 looks good to me. Perhaps we can set (in the
weapon's firemode entry) the location of the firemode button on the
modified interface? For example, if we have 6 buttons, 2 rows of 3, we
could have something like this:

firemode_button = 3

Then we could grey out/disable any buttons that aren't used by the
weapon as required.

--[Winter](User:Winter "wikilink") 12:19, 29 January 2007 (CET)

@Winter: Remember that "Implementation method 1" is just the backend,
and there is nothing about the GUI in it yet. I like you gui suggestion
and I'll post an example of what I have in mind (GUI) for different
firemode-actions (e.g. the lob&roll for grenades) as well in the future
for comparison. It's very similar to the original UFO:EU GUI (i.e.
list/popup style) with some additional features for these things. I
dunno how much combinations we'll ge5t, but for now I'm concentrating on
the code- and data-backend to enable these things later on ;)

--[Hoehrer](User:Hoehrer "wikilink") 13:34, 29 January 2007 (CET)

- An X-COM-style popup GUI would be fantastic, and I'd be happy to ditch
  my idea in favour of it. We'd need to make it look a bit better than
  it did 10 years ago, however. I'd be happy to create some more buttons
  or other graphics of that style if we can use them.

<!-- -->

- --[Winter](User:Winter "wikilink") 22:45, 29 January 2007 (CET)

### All cases covered?

Implementation proposal 1 does not solve everything, if I understand it
correct.

- We need:
  - different firemodes per ammo
  - different firemodes per weapon
  - logical AND for 1) and 2)
- Look, an example:
  - laser rifle primary mode name: snap shoot
  - laser rifle secondary mode name: aimed shoot
  - heavy laser primary mode name: burst
  - heavy laser secondary mode name: overload
  - both laser rifle and heavy laser uses the same ammo in this example,
    so that's ok if we define firemodes here per weapon.
- But then another example, what if we use two different weapons, both
  with two kinds of ammo (read: ammo1 and ammo2 can be used in both
  weapon1 and weapon2), and **the firemode type differs for ammo**? So,
  the situation:
  - weapon1, ammo1, primary firemode name: "firemodeW1A1"
  - weapon1, ammo2, primary firemode name: "firemodeW1A2"
  - weapon2, ammo1, primary firemode name: "firemodeW2A1"
  - weapon2, ammo2, primary firemode name: "firemodeW2A2"
- IMO if we want to change the current behaviour, try to do this as much
  flexible as possible, to cover ANY future
  ideas.--[Zenerka](User:Zenerka "wikilink") 12:57, 29 January 2007
  (CET)

@Zenerka: No, if I understand you right you can do that all right with
this implemention ... the worst case would be a duplication of the
firemode-information in the ufo file. The firemode definition(s) for
each weapon is in the ammo. In your example: Remember that you have
**two** weapon entries (weapon1 and weapon2) with **two** firemodes in
**each of the two ammo** (ammo1 and ammo2) you can define anything you
want.

If i understood you wrong we can discuss this on jabber later today or
tomorrow (if you have time)

--[Hoehrer](User:Hoehrer "wikilink") 13:34, 29 January 2007 (CET)

Example (quick draft) with the shotgun-shells:

    item Flechette_Shells
    {

        weapon Micro_Shotgun {
            firedef { name  "_Firemode 1" ... }
            firedef { name  "_Firemode 2" ... }
        }
        weapon Riot_Shotgun {
            firedef { name  "_Firemode 1" ... }
            firedef { name  "_Firemode 2" ... }
        }
    }

    item Saboted_Slugs
    {
        weapon Riot_Shotgun {
            firedef { name  "_Firemode 1" ... }
            firedef { name  "_Firemode 2" ... }
        }
    }

--[Hoehrer](User:Hoehrer "wikilink") 14:34, 29 January 2007 (CET)

- Yes, with that concept (ammo definition contains weapon entries, which
  can use this ammo, and those weapon entries contain every fire
  definition, the weapon can use with this particular ammo) every case I
  can imagine is being covered - that's good. It should be remembered,
  though, that such firedef { } inside weapon { } inside item { } should
  contain more parameters, not only name (spread, range, damage, maybe
  particles...).--[Zenerka](User:Zenerka "wikilink") 23:51, 29 January
  2007 (CET)