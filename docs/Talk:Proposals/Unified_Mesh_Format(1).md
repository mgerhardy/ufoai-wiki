I realize this is far beyond my expertise, but is there a reason that
we're not looking to implement an existing, widely used and widely
supported format? Are we talking here about creating our own format?
Does that mean maintaining our own tools, import/export plugins, etc? Or
am I missing something? --[H-hour](User:H-hour "wikilink") 02:37, 30
November 2012 (SAST)


In fact, this is about the *internal* representation of mesh data, not
the storage (file) format (which I think Sandro would also like to
unify, but that's a different matter).

--[DarkRain](User:DarkRain "wikilink") 03:57, 30 November 2012 (SAST)

## Naming: TextureCoordinate is way too long, \[…\] What is better?

As far as I know, the compiled code has no names of variables. When you
write the code you can use autocompleting and other tips, so readability
and clearing of code is better than economy of symbols.

- Sure, but they take space in the editor window. So, I prefer to keep
  balance between being concise and being easy to understand.
  [Sandro](User:Sandro "wikilink") 23:13, 1 December 2012 (SAST)

## mAliasMesh_t

What about this? this was my approach (from egl afair) to unify the
rendering - as we earlier used the raw model formats to render
everything. --[Mattn](User:Mattn "wikilink") 16:05, 30 November 2012
(SAST)

Multiple objections:

- It is not a pure mesh format, it encapsulates animation data (bones),
  texture data (skins), animation morphing data (next_\*), and even the
  filesystem data. Why keep all that together?
- No support for lightmaps
- Last, but not least: name is misleading. id modellers did use
  **Alias** software, but we do not.

<!-- -->

- Said that, I did analyze all the mesh formats used in game, and my
  proposal is based on making the least common multiple of those. That
  is my point. [Sandro](User:Sandro "wikilink") 23:09, 1 December 2012
  (SAST)

## AABB

We have \*two\* classes named AABB in our project. Which one ?
--[Duke](User:Duke "wikilink") 21:59, 30 November 2012 (SAST)

- Game defines only one. I don't care for Radiant.
  [Sandro](User:Sandro "wikilink") 22:55, 1 December 2012 (SAST)