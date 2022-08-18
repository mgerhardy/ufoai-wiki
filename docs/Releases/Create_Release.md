## Release guidelines

This is a **guideline for release maintainer and main-developers** how
to create a [release](Releases "wikilink") from [git](git "wikilink").

***This is still TODO and needs major cleanup.***

### Main developers

- Decide what version number the release needs. See [\#Version number
  system](#Version_number_system "wikilink") below.
- Check if all locations that contain the version number are up to date.
  If not, update the files so they reflect the current version number.
- Create tag with current version-number.
- Update [Changelog](Changelog "wikilink")
- Update News section on the homepage with the release information and
  available release-files.
- Create new tags for the bug tracker.

### Others

- Post/email news announcements as described here:
  [Releases/Announcements](Releases/Announcements "wikilink")

## Version number system

|                       |                    |                      |
|-----------------------|--------------------|----------------------|
| Releases/Branch-names | Release Candidates | Development Releases |
| **`x.y`**             | **`x.y-RCz`**      | **`x.y-devz`**       |

### Development releases (unstable)

This version numbers are used for unstable (pre-RC) releases for
beta-testing.

<table style="width:10%;">
<colgroup>
<col style="width: 3%" />
<col style="width: 7%" />
</colgroup>
<tbody>
<tr class="odd">
<td><ul>
<li><strong><code>2.1-devz</code></strong> <small>development release
for 2.1</small></li>
<li><strong><code>2.2-devz</code></strong> <small>development release
for 2.2</small></li>
<li><strong><code>3.0-devz</code></strong> <small>development release
for 3.0</small></li>
<li>etc...</li>
</ul></td>
<td><dl>
<dt></dt>
<dd>
<code>x</code> - Is the major version number of the release.
</dd>
<dd>
<code>y</code> - Is the minor version number of the release.
</dd>
<dd>
<code>z</code> - Is the number of the dev-release candidate starting
with 1.
</dd>
</dl></td>
</tr>
</tbody>
</table>

### Release candidates (mostly stable)

This version numbers are used for pre-stable releases of the code. i.e
the code should be feature-frozen.

**Note:** do not use uppercase letters when using this in filenames &
[git](git "wikilink").

<table style="width:10%;">
<colgroup>
<col style="width: 3%" />
<col style="width: 7%" />
</colgroup>
<tbody>
<tr class="odd">
<td><ul>
<li><strong><code>2.0-RCz</code></strong> <small>release candidate for
2.0</small></li>
<li><strong><code>2.1-RCz</code></strong> <small>release candidate for
2.1</small></li>
<li><strong><code>3.0-RCz</code></strong> <small>release candidate for
3.0</small></li>
<li>etc...</li>
</ul></td>
<td><dl>
<dt></dt>
<dd>
<code>x</code> - Is the major version number of the release.
</dd>
<dd>
<code>y</code> - Is the minor version number of the release.
</dd>
<dd>
<code>z</code> - Is the number of the Release Candidate starting with 1.
</dd>
</dl></td>
</tr>
</tbody>
</table>

### Release versions (stable)

This version numbers are used for stable releases in the branches.

<table style="width:10%;">
<colgroup>
<col style="width: 3%" />
<col style="width: 7%" />
</colgroup>
<tbody>
<tr class="odd">
<td><ul>
<li><strong><code>2.0</code></strong></li>
<li><strong><code>2.1</code></strong></li>
<li><strong><code>2.2</code></strong></li>
<li><strong><code>3.0</code></strong></li>
<li><strong><code>3.1</code></strong></li>
<li>etc...</li>
</ul></td>
<td><dl>
<dt></dt>
<dd>
<code>x</code> - Is the same as in the <a
href="#Release_candidates_(mostly_stable)" title="wikilink">Release
candidates</a>. This number will most probably only changed if some
major refractory of the code is made.
</dd>
<dd>
<code>y</code> - Starts with 0 for the first stable release and is
incremented for each following release.
</dd>
<dd>
<code>z</code> - unused
</dd>
</dl></td>
</tr>
</tbody>
</table>

### Version tree

For each Release and Release Candidate we'll create a 'tag' in the
repository so it can be accessed again later on.

[Category:Packaging](Category:Packaging "wikilink")
[Category:Contribute](Category:Contribute "wikilink")