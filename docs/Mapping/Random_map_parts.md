This tutorials explains how map parts have to be designed, so they can
be used for automatic map assembly.

The **most important rule**: The map part can have different shapes, but
it must fit onto a **256x256** grid. The pictures below illustrate this
rule:

<table>
<thead>
<tr class="header">
<th><p>Screenshot</p></th>
<th><p>UMP definition</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><figure>
<img src="Mapparts1.jpg" title="Image:Mapparts1.jpg"
alt="Image:Mapparts1.jpg" />
<figcaption aria-hidden="true">Image:Mapparts1.jpg</figcaption>
</figure></td>
<td><pre><code>tile +s01
{
    4 4

    0  a  a  0
    a +a +a  a
    a +a +a  a
    0  a  a  0
}</code></pre></td>
</tr>
<tr class="even">
<td><figure>
<img src="Mapparts2.jpg" title="Image:Mapparts2.jpg"
alt="Image:Mapparts2.jpg" />
<figcaption aria-hidden="true">Image:Mapparts2.jpg</figcaption>
</figure></td>
<td><pre><code>tile +s02
{
    4 4

    0  0  c  0
    a +a +a  a
    a +a  a  a
    0  a  a  0
}</code></pre></td>
</tr>
</tbody>
</table>

Another point is, that the map should be shifted such that the lower
left corner is at 0,0 position. Make sure you have the same
[lighting](Mapping/Lights "wikilink") settings for ambient and sun light
on all individual map parts. Choose the light angle such that the
shadows are not too long so they are casted over the edge of a map
piece.

You can also have a look at the [random map
assembly](Mapping:Random_map_assembly "wikilink") article to get your
map included in assembly.

## Links

- [Mapping](Mapping "wikilink")
- [Map assembly
  themes](Mapping/List_of_Maps#Mapassembly_Themes "wikilink")

[Category:Mapping](Category:Mapping "wikilink")
[Category:Contribute](Category:Contribute "wikilink")