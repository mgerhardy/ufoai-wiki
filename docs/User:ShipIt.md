### Introduction

I dropped into the forum to complain and went out starting my \[ first
mapping attempt\].

One note. Although contributing to this project, I am not a computer guy
at all. This might be not entirely true, because I use computers for
gaming since I got my first one. (The Commodore C64 was a computer,
wasn´t it?) Also most of my business nowadays relies on using computers.
But I can neither read nor write code in any way. So I would call myself
an experienced (Windows®-) user.

### City Map Project

### Prelude

Inspired by [H-Hour´s](User:H-hour "wikilink") City map I always thought
about how to make something like this possible. Now I finally want to
take a shot at this. At current stage I am about to make the last
details on the 'proof of concept'. This is a huge project, will need a
lot of time and is probably going to never be 'finished'. But I hope I
can take it far enough to give the game a map that can compete with the
alienbase.

#### Goals

- The theme should be generally darker than the other maps. I want much
  more 'Blade Runner' than 'Miami Beach'. This gives the opportunity to
  work with lights much more than usual. The dropships will land in an
  abandoned part of the city.
- The RMA needs to be flexible, so buildings (tiles) of very different
  sizes can be used.
- RMA needs to support every mission type (all UFOs, missions without
  UFO).
- Maps should take advantage of the material system as much as possible.
- Try to make it not too huge. Seems to be the biggest task for me, as I
  don´t like my soldiers to jump out of the dropship and get shot at the
  blink of an eye. So I tend to make the dropship tiles somewhat bigger
  than usual, to provide a save landing zone. This of course stretches
  each mission by one turn or two.

#### Needs

- A texture to mark stairs up/down.

### Todo

#### Concept

- proof of concept

  - proof of concept for small assembly (Scout UFO, Fighter UFO), max
    size 7x6

  - proof of concept for medium assembly (Harvester UFO, Gunboat UFO,
    Supply UFO), max size 9x9

  - { proof of concept for large assembly (Corrupter UFO, Bomber UFO),
    max size 11x12

  - proof of concept for huge assembly (Corrupter UFO, Bomber UFO), size
    14x14

#### Lighting

- check out the lighting system to find a configuration that fits the
  goal

#### Dropsip tiles

- Dropship tiles (for testing some very simple tiles are in place)

  - - For those I thought to make the dropships land on some kind of
      "aircraft station". For the start a helipad is enough.

  - Firebird dropship

  - Herakles dropship

  - Raptor dropship

#### UFO tiles

- UFO tiles

  - Scout UFO

  - Fighter UFO

  - Gunboat UFO

  - Supply UFO

  - Harvester UFO

  - Corrupter UFO

  - Bomber UFO

  - crashed Scout UFO

  - crashed Fighter UFO

  - crashed Gunboat UFO

  - crashed Supply UFO

  - crashed Harvester UFO

  - crashed Corrupter UFO

  - crashed Bomber UFO

#### Street tiles

<figure>
<img src="C3_street_v_1.png" title="C3_street_v_1.png" width="400"
alt="C3_street_v_1.png" />
<figcaption aria-hidden="true">C3_street_v_1.png</figcaption>
</figure>

- street lines, corners and crossings

  - street tile horizontally

    - workaround the stretched floor brush of the sidewalk

  - street tile vertically

  - street corner sw ¯\|

  - street corner se \|¯

  - street corner nw _\|

  - street corner ne \|_

  - street crossing X -\|-

    - Not sure if this is needed at all. It would require a lot of space
      and doesn´t add much.

  - street crossing s ¯\|¯

    - reduce brush- & facecount once the layout is final

  - street crossing w -\|

    - reduce brush- & facecount once the layout is final

  - street crossing n _\|_

    - reduce brush- & facecount once the layout is final

  - street crossing e \|-

    - reduce brush- & facecount once the layout is final

  - tunnel crossing vertical street

  - tunnel crossing horizontal street

  - Camera Control Center for traffic cameras

  - Camera Conrol Center for subway cameras

#### Maps

- ideas what tiles could be adapted from existing maps

  - +city parking lot

    - add some proper sounds

  - +cemetery

  - +transport

  - +spedition

  - +tower

  - +construction

<!-- -->

- ideas for new buildings

  - abandoned building

    - reduce brush- & facecount once the layout is final

  - cinema

  - hospital

  - bottom levels of the +city2 highrise

  - mall

  - railway station

#### Updates

<File:C3> street v 1.png <File:C3> crossing s.png <File:City> theme
a.png <File:City> theme b.png <File:City> theme c.png <File:City> theme
d.png

[Category:UFO:AI Team](Category:UFO:AI_Team "wikilink")