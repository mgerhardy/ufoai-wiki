## Software Requirements

- Windows XP (older versions are not supported)
- Linux
- MacOSX

## Minimum Hardware Requirements

See [Talk:FAQ](Talk:FAQ "wikilink") for several examples of system specs
that work. Based on the comments there, it's likely that you could go a
bit lower and still be ok.

The lowest common denominator posted so far seems to be about:

- CPU: 500MHz
- RAM: 128MB
- Video Card: 32MB (must have 3D acceleration)

## Suggested Hardware

- RAM: 512MB

## What doesn't work

### Intel

- This maybe needs update - intel card users, please test latest
  revision in trunk
  - The **Intel i810 Linux video driver** unfortunately lacks several
    features and is at this point not usable for UFO:AI
  - The **Intel 915GM/GMS/910GML Express Graphics Controller Linux video
    driver** unfortunately does not work.
  - The **Intel G965** works, but you need to start it with **./ufo +set
    r_programs 0**, otherwise it will crash at start (as of r29155,
    2010-03-27)