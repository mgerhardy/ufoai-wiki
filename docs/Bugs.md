## General

You can submit bugs to the . But please first have a look if this bug is
already mentioned somewhere. If it's already on the list, add your bug
message as a comment.

<div style="border:2px solid red; padding:1em; margin-left:2em; margin-right:2em;">

<font style="color:red;">

### Useful bug reports

</font> When you report a bug please provide us with the following
information, because otherwise it's often impossible to quickly check
what is going on.

#### Version

- Where did you download the version of the game and what
  version(-number) is it. Please be as verbose as possible here.

#### System

- What operating system do you run UFO:AI on?
- What computer and graphics card do you have? (graphic driver version
  if you know)
- What architecture does your system use (e.g. like *i386*, *x86_64*)

This is especially useful for everything from graphics bugs, setup
problems, performance issues, os dependent errors, etc...

#### What happened before the bug occurred? Is the bug reproducible?

The bug itself is often just a symptom of things that happened right
before (or often even a long time ago).

Some things to check:

- The first thing we ask you is to check **if you can reproduce the
  bug**. The **simpler** the reproduction-steps are, the better.
- Does the bug also happen when starting a new game or only after
  loading a saved game (most likely a bug in the load/save system)
- Please attach the output console file . See
  [FAQ](FAQ#General "wikilink") to get the path were this file is stored
  on your harddisk.

#### Mapbugs

If you encounter bugs in a map - like unreachable places, not working
stairs or soldiers inside of objects, please create a
[screenshot](Screenshots "wikilink") () and open a bugtracker item with
a name like

    [map] <mapname> <shortdescription>

Make sure to read [additional information](Mapping/Testing "wikilink")
regarding map testing and reporting on that.

#### Additional information

- Make a [screenshot](Screenshots "wikilink") of the problem ( key; see
  game [console](console "wikilink")) to see where it is saved)
- Game logs (see above)
- Attching files: You have to create the ticket first on the bugtracker
  to add files/screenshots.
- Whenever possible, attach relevant files to the report.

##### Transferring information

When communicating over IRC, it might be necessary to quickly exchange
larger amounts of information. You can use the following services for
various types of data:

- For text files you could use a service like to paste&link the messages
- For graphic files you can use a service like or
- For various other files like savegames you can use or

</div>

## Bug Priorities

The priority settings we use for the bugtracker are described here.
Please note that this system is rather new, so by far not all tracker
items have their priority set correctly.

### Base Priorities

<table>
<thead>
<tr class="header">
<th><p>Priority (SF/Genie)</p></th>
<th><p>Description</p></th>
<th><p>User perception</p></th>
<th><p>Examples</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>9 / critical</p></td>
<td><p>Catastrophic bug</p></td>
<td><p>the application is completely unusable</p></td>
<td><ul>
<li>application can't be compiled</li>
<li>application doesn't even start</li>
</ul></td>
</tr>
<tr class="even">
<td><p>8 / vital</p></td>
<td><p>A vital feature doesn't work</p></td>
<td><p>the application is partially usable (for testing), but it doesn't
make sense</p></td>
<td><ul>
<li>can't start battlescape</li>
<li>can't build a required base building</li>
<li>no loot at the end of battle (thus no way to advance campaign)</li>
</ul></td>
</tr>
<tr class="odd">
<td><p>7 / important</p></td>
<td><p>An important feature doesn't work</p></td>
<td><p>the application is usable, but its not enough fun</p></td>
<td><ul>
<li>can't build a certain base building</li>
<li>frag grenades don't work</li>
</ul></td>
</tr>
<tr class="even">
<td><p>6 / normal</p></td>
<td><p>A minor feature doesn't work</p></td>
<td><p>the application is usable, but it's less fun</p></td>
<td><ul>
<li>soldiers don't gain experience at all</li>
<li>flashbangs don't work</li>
</ul></td>
</tr>
<tr class="odd">
<td><p>5 / not set</p></td>
<td><p>The default priority when the item is created.</p></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p>4 / low</p></td>
<td><p>Any other minor misbehaviour the user might notice</p></td>
<td><p>the application is fully usable</p></td>
<td><ul>
<li>soldiers don't gain experience at the speed defined in the
specs/docs</li>
<li>a wooden texture on a concrete wall</li>
</ul></td>
</tr>
<tr class="odd">
<td><p>3 / very low</p></td>
<td><p>Any other minor misbehaviour only a dev can notice</p></td>
<td><p>the application is fully usable</p></td>
<td><ul>
<li>strange results for some extreme testcases</li>
<li>some code wastes some resources</li>
</ul></td>
</tr>
</tbody>
</table>

### Modifiers

The above applies to bugs that happen reproducibly (on a dev's machine
!) on all platforms and have no workaround. If one or more of these
criteria are missing, priority suffers a penalty of 0.6 for each,
rounded. So a bug in a vital feature (Prio 8) that only occurs on Macs
and is not reproducible (1.2) will have Prio 7. If there is even a
workaround (1.8) it will be Prio 6.

Or, if you don't like to calculate: if one or two of the criteria are
present, it's priority minus 1. If all the three are present, it's minus
2.

### Dev's action

In a professional environment, priorities are closely connected to a
certain behaviour of the devs eg. working overtime.

In an OSS environment, a prio 9 or 8 bug still means "all hands on
deck". For priorities \< 8, devs are 'supposed' or 'asked' to fix them
according to priority. They are of course still allowed to fix even the
least important bug if they are in the mood to do so.

## Debugging

See our [debugging](Debugging "wikilink") site for more information on
how to handle segfaults and crash bugs.

## Bug-links inside the wiki

You can use the code

    {{bug|1234567}}

to link to an existing bug in the tracker. The above example will
produce "" (bogus number)

For request use the code

    {{request|1502802}}

( as result)

[Category:Contribute](Category:Contribute "wikilink")
[Category:Bugs](Category:Bugs "wikilink")