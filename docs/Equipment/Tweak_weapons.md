Weapons are tweaked for game balance, as well as for eye candy (and for
fun). Currently some weapons are still in need of the initial tweak
(e.g., mines) and some others are half-broken (e.g., particles are off).
To tweak a weapon (or any other equipment item) you have to find it in
one of the
**[base/ufos/weapons\*.ufo](UFO-Scripts/weapon_*.ufo "wikilink")**
files. Tweaking armor or other non-weapon equipment piece is similar to
tweaking a weapon.

The weapon is described by a multitude of
[variables](UFO-Scripts/weapon_*.ufo "wikilink"). Tweak the variables
and test the results in-game.

Weapons often use some [sound effect](Music_and_sounds "wikilink") files
and [particle effect](UFO-Scripts/ptl_*.ufo "wikilink") files. If you
want to change these then find new ones somewhere, request them on the
forum or create them yourself.

## FAQ

- Why do the name fields begin with underscore, as in "_Assault Rifle"?

  The underscore indicates that the *following* text will be
  translateable via [Gettext](Translating "wikilink").

<!-- -->

- What is the in-game effect of the "weapon" variable?

  Among others, when an alien is assigned one primary weapon from the
  equipment, the flag is used to tell weapon from ammo, even if it has
  the same "buytype".

<!-- -->

- Does "shape" or "scale" variables also influence the size of the
  weapon in the battlescape?

  No. So take care that small things do not have huge inventory icons.
  On the other hand, it might a good idea to keep most primary weapons
  the same inventory shape (even if, e.g., [Rocket
  Launcher](Equipment/Primary_Weapons/Rocket_Launcher "wikilink") is
  very long in the battlescape) and most secondary weapons the same
  (smaller) inventory shape. This way they fit nicely in the backpack or
  holster. As for ammo shapes --- enjoy yourself.

<!-- -->

- What is the meaning of the "center" vector? Is it a translation vector
  or rotation or what?

  I know the middle coordinate has something to do with the **z** axis,
  probably a rotation. The first is a translation to the right, the
  third is a translation downwards. One unit seems to be 5 pixels on a
  1024x768 screen. Note that horizontal parameter moves to the left for
  positive values, and vertically positive values move downwards.

<!-- -->

- Should I scale the weapon (with the "scale" variable) so that it fills
  all the "shape" variable inventory box?

  Approximately, but just try to make it look nice. In particular, if
  the weapon has high area to background ratio (e.g. the [9mm
  Pistol](Equipment/Secondary_Weapons/9mm_Pistol "wikilink")), usually
  it looks better slightly smaller, unless you feel the bulkiness fits
  the theme (for the pistol, IMHO, it doesn't, even if it's Desert
  Eagle).

## Links

- [Equipment descriptions](Equipment "wikilink")
- [Obsoletable equipment](Equipment/Obsoletable_equipment "wikilink")
- [Skills](Skills "wikilink")
- [UFO-Scripts/weapon_\*.ufo](UFO-Scripts/weapon_*.ufo "wikilink")
- [UFO-Scripts/ptl \*.ufo](UFO-Scripts/ptl_*.ufo "wikilink")

[Category:Equipment](Category:Equipment "wikilink")
[Category:Weapons](Category:Weapons "wikilink")
[Category:UFO-Scripts](Category:UFO-Scripts "wikilink")
[Category:Skills](Category:Skills "wikilink")