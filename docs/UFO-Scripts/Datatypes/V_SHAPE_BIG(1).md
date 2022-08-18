## V_SHAPE_BIG

The V_SHAPE_BIG value defines a rectangle given by the upper left corner
and dimensions. A container can have several shapes that are added to
the final container form.

i.e. several entries of a *V_SHAPE_BIG* datatype can be grouped together
to create more complex masks.

    shape "x y w h"
    shape "x y w h"
    ...

To position the various shapes (**w**idth x **h**eight) you need to use
the first two values (**x** and **y** position).

Currently the maximum size of a container is 32 width x 16 height,
please keep that in mind when assembling shapes. This means that **(x+w
\< 32) and (y+h \< 16)**.

## Examples

<table>
<tbody>
<tr class="odd">
<td><pre><code>shape   &quot;0 0 3 1&quot;
shape   &quot;0 1 1 1&quot;</code></pre></td>
<td><ul>
<li>shape 3x1 positioned in the first row (0) first place (0)</li>
<li>shape 1x1 positioned in the second row (1) first place (0)</li>
</ul></td>
<td><pre><code>111
2..</code></pre></td>
</tr>
<tr class="even">
<td><pre><code>shape   &quot;1 0 3 1&quot;
shape   &quot;0 1 5 2&quot;</code></pre></td>
<td><ul>
<li>shape 3x1 positioned in the first row (0) second place (1)</li>
<li>shape 5x2 positioned in the second row (1) first place (0)</li>
</ul></td>
<td><pre><code>.111.
22222
22222</code></pre></td>
</tr>
<tr class="odd">
<td><pre><code>shape   &quot;0 0 3 1&quot;
shape   &quot;0 1 1 1&quot;
shape   &quot;2 1 1 1&quot;</code></pre></td>
<td><ul>
<li>shape 3x1 positioned in the first row (0) first place (0)</li>
<li>shape 1x1 positioned in the second row (1) first place (0)</li>
<li>shape 1x1 positioned in the second row (1) third place (2)</li>
</ul></td>
<td><pre><code>111
2.3</code></pre></td>
</tr>
</tbody>
</table>

You can find examples of shapes with no position (x=0, y=0) here:
[V_SHAPE_SMALL](V_SHAPE_SMALL "wikilink")

## Links

- [V_SHAPE_SMALL](V_SHAPE_SMALL "wikilink")
- [UFO-Scripts](UFO-Scripts "wikilink")

[Category:UFO-Scripts](Category:UFO-Scripts "wikilink")