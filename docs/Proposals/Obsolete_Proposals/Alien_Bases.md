# Alien Bases

## Summary

Alien bases are a position on the map that represents alien occupation
of that location. They provide a point from which alien missions can be
launched and another type of mission which the Phalanx team can
undertake, namely an alien base attack.

## Solution Design

Alien Bases have the following features:

1.  They are supplied by UFO Supply ships.
2.  They can spawn alien missions from earth (no UFO is involved in the
    mission).
3.  They can be attacked by phalanx team.
    - The size of the map used during an alien base attack will increase
      with the amount of supplies the base received.
    - Alien bases are invisible to phalanx player when they are created.
      They can be detected by:
      - scouting with aircraft
      - with help of the nation where it is located, every week (the
        less the nation is infected by [XVI](XVI "wikilink") and the
        smaller the alien base, the less nation will help).

## Technical Design

See existing code in / . The alienbase map tiles are in .

## Links

- [Campaign system](Gameplay_Proposals/Campaign "wikilink")
- [Off-base Installations](Proposals/Off-base_Installations "wikilink")
- [Off-base UFO Yards](Proposals/Off-base_UFO_Yards "wikilink")
- [Random map assembly](Mapping/Random_map_assembly "wikilink")