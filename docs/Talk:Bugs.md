Bugs Page not yet revised.

hi, sorry newbee, but maybe I fund a bug in one Map of the single player
compain. The Map is called Rzeszow, if you kill all aliens you still
can´t proceed, I tried about six times to find the missing "alien", same
result

I have a macbook Pro Intel 10.5, my game version is downloaded form your
page, verNr: 2.2.1 everything else works fine for me, it´s a great game
I would realy like to continue

Greetz Akira

## Priorities

<table>
<thead>
<tr class="header">
<th><p>Priority</p></th>
<th><p>Description</p></th>
<th><p>User perception</p></th>
<th><p>Examples</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>9</p></td>
<td><p>Catastrophic bug.</p></td>
<td><p>the application is completely unusable</p></td>
<td><p>* app can't be compiled</p>
<ul>
<li>app doesn't even start</li>
</ul></td>
</tr>
<tr class="even">
<td><p>8</p></td>
<td></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

### Priority 8:

Description: A vital feature doesn't work

User perception: the app is partiallly unusable (for testing), but it
doesn't make sense

Examples:

- can't start battlescape
- can't build a required base building
- no loot at the end of battle (thus no way to advance campaign)

### Priority 7:

Description: An important feature doesn't work

User perception: the app is usable, but its not enough fun

Examples:

- can't build a certain base building
- frag grenades don't work

### Priority 6:

Description: A minor feature doesn't work

User perception: the app is usable, but it's less fun

Examples:

- soldiers don't gain experience at all
- flashbangs don't work

### Priority 5:

Description: The default priority when the item is created.

### Priority 4:

Description: Any other minor misbehaviour the user might notice

User perception: the app is fully usable

Examples:

- soldiers don't gain experience at the speed defined in the specs/docs
- a wooden texture on a concrete wall

### Priority 3:

Description: Any other minor misbehaviour only a dev can notice

User perception: the app is fully usable

Examples:

- strange results for some extreme testcases
- some code wastes some resources

### Modifiers

The above applies to bugs that happen reproducibly on all platforms and
have no workaround. If one or more of these criteria are missing,
priority suffers a penalty of 0.6 for each, rounded. So a bug in a vital
feature (Prio 8) that only occurs on Macs and is not reproducible (1.2)
will have Prio 7. If there is even a workaround (1.8) it will be Prio 6.

### Dev's action

In a professional environment, prioritys are closely connected to a
certain behaviour of the devs eg. working overtime.

In an OSS environment, a prio 9 or 8 bug still means "all hands on
deck". For priorities \< 8, devs are 'supposed' or 'asked' to fix them
according to priority. They are of course still allowed to fix even the
least important bug if they are in the mood to do so.