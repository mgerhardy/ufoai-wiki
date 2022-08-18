## V_SHAPE_SMALL

V_SHAPE_SMALL is the shape in equipment menu, that is how much space do
we need to place this weapon (this value defines a rectangle given by
the upper left corner (**x**, **y**) and dimensions (**w**, **h**))

    shape "x y w h"

Several entries of a *V_SHAPE_SMALL* datatype can be grouped together to
create more complex masks.

    shape "x y w h"
    shape "x y w h"
    ...

To position the various shapes (**w**idth x **h**eight) you need to use
the first two values (**x** and **y** position).

Currently the maximum size of a container is 8 width x 4 height, please
keep that in mind when assembling shapes. This means that **(x+w \< 8)
and (y+h \< 4)**.

## Examples

<table>
<tbody>
<tr class="odd">
<td><pre><code>shape &quot;0 0 2 1&quot;</code></pre></td>
<td><p>2 wide and 1 high</p></td>
<td><pre><code>11</code></pre></td>
</tr>
<tr class="even">
<td><pre><code>shape &quot;0 0 1 2&quot;</code></pre></td>
<td><p>1 wide and 2 high</p></td>
<td><pre><code>1
1</code></pre></td>
</tr>
<tr class="odd">
<td><pre><code>shape &quot;0 0 5 2&quot;</code></pre></td>
<td><p>5 wide and 2 high</p></td>
<td><pre><code>11111
11111</code></pre></td>
</tr>
<tr class="even">
<td><pre><code>shape       &quot;0 0 5 1&quot;
shape       &quot;0 1 3 1&quot;</code></pre></td>
<td><ul>
<li>5 wide and 1 high (starting at first row (0) first place (0))</li>
<li>3 wide and 1 high (starting at second row (1) first place (0))</li>
</ul></td>
<td><pre><code>11111
111..</code></pre></td>
</tr>
</tbody>
</table>

## Links

- [V_SHAPE_BIG](V_SHAPE_BIG "wikilink")
- [UFO-Scripts](UFO-Scripts "wikilink")

[Category:UFO-Scripts](Category:UFO-Scripts "wikilink")