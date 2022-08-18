## General

Used only for editor convenience. All brushes in a single func_group
count as single entity, and thus you can select one brush from the
group, press and you'd have whole group selected. It is a good practice
to group brushes that belong together, so do that often. Grouping
brushes that belong together and form a single object is good, it makes
mapping much easier - and it does not impact map compiling or game
performance in any way.

Don't clone func_group objects (they stay in the same group). Actually,
better do not clone things at all, copy-paste them - that works much
better to prevent 10 accidentally grouped beds in a map.

Note that, as opposed to most other entities, you don't have to set
levelflags for the func_group entity - you still set them for individual
brushes.

## Links

- [Entitylist](Mapping/Entities "wikilink")

[Category:Contribute](Category:Contribute "wikilink")
[Category:Mapping](Category:Mapping "wikilink")
[Category:Entity](Category:Entity "wikilink")