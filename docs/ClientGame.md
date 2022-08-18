## Client side game types

Since version 2.4 it is possible to extend the game with so called cgame
implementations. These are client side mods for custom game types. Such
a cgame implementation has to implement the *cgame_export_t* interface
(see ). It may only use the functions that are available in the
interface *cgame_import_t* and those that are explicitly linked to the
shared object.

If you add a new cgame mode, you have to copy the shared object into the
folder and create an entry in [script file](UFO-Scripts "wikilink") .
The id of a cgame entry in the script file is the name that is used to
resolve the shared object file. The referenced window in the body of the
gamemode definition must exists of course and must contain your custom
cgame ui entry window definition.

## Starting with a new cgame mode

A good starting point is for sure the skirmish game mode, as it's very
small from the c-code side and only contains one window definition. You
always have to support hard linked cgame stuff and cgame via shared
object/dll. Use the macro *HARD_LINKED_CGAME* for this. There is a list
of the cgame GetCGameAPI function pointers in for the hard linked
cgames.

## Example C-Code

`static const cgame_import_t *cgi;`

`#ifndef HARD_LINKED_CGAME`
`/* this is only here so the functions in the shared code can link */`
`void Sys_Error (const char *error, ...)`
`{`
`   va_list argptr;`
`   char text[1024];`

`   va_start(argptr, error);`
`   Q_vsnprintf(text, sizeof(text), error, argptr);`
`   va_end(argptr);`

`   cgi->Sys_Error("%s", text);`
`}`

`void Com_Printf (const char *msg, ...)`
`{`
`   va_list argptr;`
`   char text[1024];`

`   va_start(argptr, msg);`
`   Q_vsnprintf(text, sizeof(text), msg, argptr);`
`   va_end(argptr);`

`   cgi->Com_Printf("%s", text);`
`}`

`void Com_DPrintf (int level, const char *msg, ...)`
`{`
`   va_list argptr;`
`   char text[1024];`

`   va_start(argptr, msg);`
`   Q_vsnprintf(text, sizeof(text), msg, argptr);`
`   va_end(argptr);`

`   cgi->Com_DPrintf(level, "%s", text);`
`}`
`#endif`

`static void GAME_EX_InitStartup (void)`
`{`
`   [...]`
`}`

`static void GAME_EX_Shutdown (void)`
`{`
`   [...]`
`}`

`static const mapDef_t* GAME_EX_MapInfo (int step)`
`{`
`   [...]`
`}`

`static void GAME_EX_Results (struct dbuffer *msg, int winner, int *numSpawned, int *numAlive, int numKilled[][MAX_TEAMS], int numStunned[][MAX_TEAMS])`
`{`
`   [...]`
`}`

`#ifndef HARD_LINKED_CGAME`
`const cgame_export_t *GetCGameAPI (const cgame_import_t *import)`
`#else`
`const cgame_export_t *GetCGameExampleAPI (const cgame_import_t *import)`
`#endif`
`{`
`   static cgame_export_t e;`

`   OBJZERO(e);`

`   e.name ="Example mode";`
`   e.menu ="exampleWindow"; // this is only for hard linked cgames - and will be removed later`
`   e.Init = GAME_EX_InitStartup;`
`   e.Shutdown = GAME_EX_Shutdown;`
`   e.MapInfo = GAME_EX_MapInfo;`
`   e.Results = GAME_EX_Results;`

`   cgi = import;`

`   return &e;`
`}`

## Example Script

`cgame example {`
`   window  "exampleWindow"`
`   name "_ExampleText"`
`}`

`window exampleWindow`
`{`
`   [...]`
`}`

[Category:Coding](Category:Coding "wikilink")
[Category:Contribute](Category:Contribute "wikilink")
[Category:Modding](Category:Modding "wikilink")