Ok, a couple more questions about testing. You say to set
sv_rmadisplaythemap to 1, but there are two 0s in the line. Is this the
correct setup?

`sv_rmadisplaythemap = Cvar_Get("sv_rmadisplaythemap", "1", 1, "Activate rma problem output");`

Second, I'm not sure what to do with this stage:

`run testall with the param --only-RandomMapAssemblyTests `

I tried loading the game and entering the following into the console,
but it didn't work:

`testall --only-RandomMapAssemblyTests`

How do I run testall? What does this mean?

------------------------------------------------------------------------

Also, see this discussion between MCR1 and me.
colabti.org/irclogger/irclogger_log/ufoai?date=2011-12-24#l25

`--`[`H-hour`](User:H-hour "wikilink")` 11:39, 24 December 2011 (CET)`

Would it be possible to make the map test running for one map / assembly
only ? Something like . Maybe even with an output of the error codes
mentioned above? [ShipIt](User:ShipIt "wikilink")


You can specify the map/asssmebly with:
<b>`testall --log --only-MapDefTests -Dmapdef-id=mm_harbour`</b>

--[DarkRain](User:DarkRain "wikilink")


Unfortunately this seems not to work. [ShipIt](User:ShipIt "wikilink")


It does work (try it with mansion), but as you found, it works only with
RMAs that have both dropships and UFOs defined it will not work with
RMAs that lack either, the same applies to running the test normally it
will only actually assemble RMAs with both dropships and UFOs.

This should be fixed for 2.4 - so we know which assemblies are broken.

\~\~