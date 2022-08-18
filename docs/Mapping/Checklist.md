This is a quick checklist of best practices, common pitfalls, hints and
frequently asked questions regarding maps.

## UFORadiant usage

- To select func_group, select one brush of the func_group, then press .
  See [func_group description](Mapping/Entities/func_group "wikilink")
  for more hints on grouping brushes.
- To create holes in existing brushes, create a brush where you want the
  hole to be, select it and press . Remove the temporary brush
  afterwards.
- [Brush
  splitting](Mapping_For_Dummies/Lesson2#Clipper_Tool_.28X.29 "wikilink")
- Remember that results of object rotation depend on chosen grid size -
  rotating with different grid sizes will result in different object
  placement.
- Do not apply flags with whole brush selected if there are any flags
  that differ for the faces of this brush. Radiant will reset parameters
  for all faces in this case.

## Best practices and tips

### Brush alignment

- "actorclip" brushes should always be aligned at lower boundary (0, 64
  and so on).
- Spawn points should always be aligned to 32 unit grid in x/y
  directions.
- "actorclip" brushes that are meant to prevent actors from stepping on
  a tile altogether should always cover full 32 unit in x/y directions.
- Walls, railings and other things should be aligned [with the 32 unit
  grid](Mapping/Dimensions#Top_view "wikilink") in such a way that they
  are between 32 unit tiles and occupy [no more than 4 units on each
  direction](Mapping_For_Dummies/Lesson1#The_Shed "wikilink").
- Floors should be in relative height 0-4 (0-4, 64-68 etc) and [never
  below absolute heigth 0](Mapping/Dimensions#Side_view "wikilink").

### Performance improving tips

- [minimise amount of exposed
  faces](Mapping_For_Dummies/Lesson1#Reducing_Exposed_Face_Count "wikilink")
- Minimise brushcount wherever possible.
- Avoid [overlapping
  brushes](Mapping_For_Dummies/Lesson1#The_Shed "wikilink") whenever
  possible.

### Generic tips

- Assign "func_breakable" to [individual brushes
  only](Func_breakable#Warning "wikilink") (note, there might be some
  exceptions - for example, fueldump map).
- Don't make stairs steeper than 45 degrees. don't make steps too large,
  they will get in the way.
- Always set your levelflags, even if you think that setting none and
  having the brush appear in all levels will work for you. even if your
  map has only 3 levels, set levelflags up to 8th level, if the brush
  should be visible in higher levels. Otherwise adding a new level above
  or below existing ones will be near impossible.
- If you want to copy an object from another map, copy it from prefabs,
  if available - prefabs are most likely to have latest fixes to the
  object that could be yet not in the other maps.

Some of the hints at [Mapping/Testing](Mapping/Testing "wikilink") might
be useful in map fixing.

If you have a weird problem, check out [common problem and generic
improvement list](Mapping/Problems_and_improvements "wikilink").

[Category:Mapping](Category:Mapping "wikilink")