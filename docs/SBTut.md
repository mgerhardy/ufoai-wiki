## Making RoQ video cutscences with SwitchBlade version 4.x

(Please note that these instructions apply primarily to making a RoQ
video on the *Windows* platform. If you plan to make such a video using
a different operating system, only some of this will apply.)

There are a number of steps necessary to make a video in the RoQ format
via SwitchBlade version 4 that will play back properly during gameplay
with the game's engine, although the final step is only necessary if an
audio track is to be included. For playback of RoQ videos *outside* of
the game (for testing purposes), the VLC Media Player, (another
open-source project) is capable of playing RoQ videos, although *please
note* that the video typically *will not* play back in VLC the exact
same way as it would appear in the game, although it might help
determine if the RoQ was built properly or not.

## Input Format

Because of limitations of the RoQ file format and the game engine, the
input file rendered *before* SwitchBlade transcodes it into a RoQ video
must obey the following limitations:

- The video must be in AVI Format.
- Frame rate must be 30 frames per second.
- Both dimensions, width and height, *must* be a multiple of 2, up to a
  maximum of 32768.
- The input video codec must be fully AVI compatible and *not*
  Directshow-Only (More about this in a moment).
- The audio will always come out to 22KHz frequency, although it can be
  mono or stereo, as well as 8 or 16 bits.

The RoQ will automatically be scaled inside the game to play back within
the dimensions and aspect ratio (relation of width to height) given by
the game. For example: If the RoQ video is encoded at 512x512, and
played back in an area in the game that is 640x480, the RoQ should
display in-game at 640x480 automatically stretched and re-sized for the
640x480 area. This also means that if you plan to create a video
cutscene that plays full-screen at a standard 4:3 ratio, the input file
can be stretched and scaled ahead of time (before SwitchBlade works with
it) to fill a 512 by 512 area, or a 512 by 256 area, etc., and the game
should re-scale and re-stretch the RoQ back to the proper aspect ratio
automatically when the RoQ is played.

*Note from Destructavator March 21 2008: I intend to finish this page
sometime soon by uploading screenshots to clarify - In the meantime,
please excuse the mess this page is in right now until I finish it.*

Regarding the codec the AVI is rendered in, it absolutely *must* be a
standard fully-AVI-compatible codec that is *not* based entirely on
DirectShow. This means that the Xvid codec, for example, will not allow
a proper RoQ to be made. Some video codecs known to work are Indeo and
Cinepack, as well as others listed in the documentation for SwitchBlade.
Indeo is recommended as it provides better quality compared to Cinepack
in the end result (the RoQ file).

As far as audio goes, if you want the RoQ video to play back with an
included audio track, it is recommended to pre-render the audio at
22KHz. Switchblade can convert from other audio formats, although the
quality of such conversion is not guaranteed to be the best. The audio
can be either 8 or 16 bits, and can be mono or stereo.

## Creating CodeBooks

Once the pre-rendered video is created, the first step is to run the
*sbcodebooks4.exe* file, which will prepare the video for the next
stage. The program will ask for an input AVI file, (which it will *not*
modify, the input source file will still be there afterwards) and then
generate codebooks, which will take a while. If all goes well so far,
you should see the individual frames from the input file being displayed
one by one on-screen as the program works on it. Much like any other
rendering, it can take time.

## Building the RoQ visual content

Once the previous step is completed, run *sbvideo4.exe* to generate an
actual RoQ. This is the step where you can specify quality in bits per
second to control filesize. If the resulting RoQ needs to be re-rendered
at a different quality setting, you do *not* have to re-generate the
CodeBooks file created in the last step, you only need to go back to
this stage (that you are reading right now).

## Adding a Soundtrack

This last step is optional, depending on whether or not an included
soundtrack is desired. If sound is to be in the video, run *sbmux4.exe*
and follow the prompts to combine a video-only RoQ with either a WAV or
AVI file that has a soundtrack. (If an AVI is used in this step, it
should be at 16 bits, according to the SwitchBlade documentation.)

## Testing the finished RoQ video clip

If all goes well, and everything was done properly, you may test the RoQ
by using the console in-game (the preferred method), or play it back
outside the game with the VLC Media Player (which isn't suggested as it
does not play it back exactly the same way).

[Category:Contribute](Category:Contribute "wikilink")
[Category:Artwork](Category:Artwork "wikilink")