If you're encountering problems, try reviewing this list of known
issues.

## Windows

| Problem                             | Symptoms                                                                                                          | Solution                                                                                                                                                                                      |
|-------------------------------------|-------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Missing DLLs                        | You might come into trouble when you try to start . The binary won't be able to load some DLLs that are needed.   | Put them in the root directory of your UFO:AI checkout - they are located in the dir.                                                                                                         |
| Can't Register Window Class         | You get the error "Couldn't register window class".                                                               | Install your 3D Graphic card drivers - or update to the latest version                                                                                                                        |
| Vista Graphics Problems             | The game doesn't even start on a Vista system.                                                                    | Deactivate Aero (right click on desktop/personalize(sic)/theme/windows classic). Make sure you don't use the Microsoft drivers for your gfx-card. Install the latest official vendor drivers. |
| Vista Full Screen Problems          | The game quits unexpectedly when you switch to full screen under Vista.                                           | Try setting full screen in : set "1".                                                                                                                                                         |
| Vista Resolution Switching Problems | The game quits unexpectedly when you switch screen resolutions under Vista (and doesn't save the new resolution). | No known solution. Setting the resolution in the doesn't work. It still loads at the default 1024x768. This probably will require a bug fix.                                                  |
| Slow with NVIDIA                    | The game runs very slow on PCI-E NVIDIA based Windows XP Computers                                                | Try to turn off "Threaded optimization" in the NVIDIA control panel. You can find the option on the "Manage 3D Settings" page.                                                                |
| Fancy Graphics Don't Work           | You can't use fancy graphic settings, even though you have the latest hardware.                                   | NVIDIA Control Panel might apply Quake2 or UFO Afterlight profiles to UFO:AI, too - deactivate this. Maybe there is something like that for ATI/AMD users, too.                               |

## Linux

<table>
<thead>
<tr class="header">
<th><p>Problem</p></th>
<th><p>Symptoms</p></th>
<th><p>Solution</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>(get)text issues in the GUI</p></td>
<td><p>You see a lot of the text in the GUI that looks like
"b_radar_txt".</p></td>
<td><p>Try running the game with the option "+set s_language en_US".
This issue and work-around was reported on a Gentoo Linux with LINGUAS
stripped down.</p></td>
</tr>
<tr class="even">
<td><p>Slow Performance</p></td>
<td><p>The game runs slowly.</p></td>
<td><p>Make sure to use the latest drivers for your graphic card - for
ATI and NVIDIA only the closed source drivers may work.</p>
<p>Intel cards maybe need texture compression enabled. Also try to
reduce the texture resolution in the video options menu. If you get an
error like "[driAllocateTexture:636] unable to allocate texture" try
deactivating the option Multitexturing in the Video-configs of the game.
It seems you need to restart the game to make these changes take
effect.</p>
<p>Intel card owners should install the package libgl1-mesa-dri to get
higher framerates.</p></td>
</tr>
<tr class="odd">
<td><p>Black Screen/Textures</p></td>
<td><p>You use an Intel card and see black textures or a black
screen.</p></td>
<td><p>Ensure that "Enable ST3C texture compression even if software
support is not available" is set to NO in driconf (driconf -&gt; image
quality).</p></td>
</tr>
</tbody>
</table>

## Mac OS X

| Problem          | Symptoms                                                               | Solution                                                                                                                                                                                                                                                     |
|------------------|------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| No Text          | There is no text when starting new missions, development screens, etc. | Your language hasn't been set. Go to the main menu / Options / Game and set a language.                                                                                                                                                                      |
| Broken Scrolling | You can't scroll in all directions.                                    | You cannot have the game resolution the same as the screen resolution in windowed mode. This causes the window to be slightly larger than the screen size. Go to the main menu, Video and either decrease the screen resolution or tick the full screen box. |

## System Independent

| Problem                           | Symptoms                                                                                                    | Solution                                                                |
|-----------------------------------|-------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------|
| Out-of-Date Graphics Card Drivers | The game crashes.                                                                                           | Make sure that you have your latest 3D graphics card drivers installed. |
| ATI Card Issues                   | You are using an ATI video card and the geoscape is not visible and/or the battlescape rendering is broken. | Deactivate the GLSL shaders.                                            |