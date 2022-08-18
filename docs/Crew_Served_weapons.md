## Crew Served Weapons

------------------------------------------------------------------------

Crew served weapons are weapons that are served by two or more crew
members. These tend to be a bit more powerful than infantry weapons, but
are harder to move around.

There are two ways to implement crew served weapons in UFOAI:

1\. Have them already set up on the map. In which case:

- The weapon is spread across, say, three tiles.
- When a soldier steps on one of the tiles occupied by the weapon, that
  part of the weapon appears on the ground, but if you click on it, the
  soldier mans that part of the weapon.
- All three tiles must be manned or the weapon won't be as effective as
  it could be.
- All the soldiers manning the weapon can't move until they stop manning
  the weapon.

2.Bring them along with the troops. This is a bit more tricky. So:

- We'll need another screen for assigning CSWs. This will probably fit
  between the inventory screen and the assignment screen, or as another
  button on the heavy weapons assignment screen.
- The CSWs will probably use troops assigned to the aircraft to man the
  weapon. The men assigned to the CSWs will have equipment for running
  the CSWs, putting a limit on what they can carry besides the CSWs.
- a CSW and it's crew act as a single unit (when moving; might want to
  have the crew members and weapon have individual health bars) on the
  battlefield until the CSW is destroyed.

## Suggestions

- Grenade machine guns
- Heavy machine guns
- Large missile launchers
- Mortars
- Bolter Cannons
- Alien Plasma cannons

etc...

[Category:Proposals](Category:Proposals "wikilink")