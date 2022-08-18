## I am trying to do as stated to compile the code

I am running into various problems resp. inconsistencies:

- @External Dependencies: There is no folder "include\mfc" in my DirectX
  SDK installation (after fresh installation). Nonetheless, the
  description tells me to include it.
- @External Dependencies: There is a file referenced in the sentence "I
  put up some precompiled libs and prestructured zip file here...". This
  file could not be downloaded (probably non-existant).
- @Compile and run: There is no "ufo.sln" file in the trunk folders.
  Instead, I assume ufo.dsw is meant (which is a VC++ project file)?
- @Compite and run: When opening ufo.dsw with Visual Studio Express
  (exactly the VS Express referenced in the descriptions), the file has
  to be converted into the actual file format. This is not mentioned in
  the description.
- @Compile and run: There are 9 projects in the ufo.dsw. When compiling,
  only one of them successfully compiles. Most errors refer to "Unable
  to Link" (probably, not all libraries are included properly, e.g.
  libc.lib), or to missing files (e.g. src/client/snd.mem.c).

--[Tecturon](User:Tecturon "wikilink") 15:05, 17 August 2007 (CEST)