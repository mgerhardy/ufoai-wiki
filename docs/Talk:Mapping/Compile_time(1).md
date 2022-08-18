## Linux time

for "time make clean maps" do i have to add up the times?

    real    8m23.553s
    user    15m39.927s
    sys     0m2.248s

means 24min? --[Blondandy](User:Blondandy "wikilink")

To be sure I roughly stopped my time with a clock as well and the first
value "real" seems to be the correct time. Haven't studied the manual
for the time command yet though :) In your example you either have a
**very** fast computer (unless you have very good compile-time
optimizations I guess) or not all of the maps were compiled. I think
none of these is the correct value. To be sure all my maps were compiled
I actually manually removed all .bsp files and simply ran "time make
maps" (at the time I didn't know one could do "clean maps" as well).
--[Hoehrer](User:Hoehrer "wikilink") 07:00, 20 August 2008 (UTC)

it does seem insanely fast. I will double check. i am not 100% that make
clean maps does compile all maps regardless.
--[Blondandy](User:Blondandy "wikilink") 11:47, 20 August 2008 (UTC)

Also to make _really_ sure how long it took you could do something
like this I guess:

    date >> time.txt;time make clean maps;date >> time.txt

Then check time.txt for start&end time :D
--[Hoehrer](User:Hoehrer "wikilink") 15:36, 20 August 2008 (UTC)

## Threads

How do I activate threads for map compiling? Also, if it is active, how
is the number of threads determined?
--[Hoehrer](User:Hoehrer "wikilink") 07:07, 20 August 2008 (UTC)

between us a mac user (can't recall who) Richlv and I modified the
makefile. make maps detects number of cores and uses them all. you can
verify this by looking at output. the Threads:#2 lines are from ufo2map.
--[Blondandy](User:Blondandy "wikilink") 11:42, 20 August 2008 (UTC)

Nice, never noticed that :) On a related note: I always hear/read that
one should always use one more thread than available cores/CPUs for
multi-threading stuff. I'm no expert on that matter so is that an urban
legend, only true in certain cases or a general good idea?
--[Hoehrer](User:Hoehrer "wikilink") 15:40, 20 August 2008 (UTC)

why not tweak your makefile, to use cores+1 threads, and see if it is
faster?--[Blondandy](User:Blondandy "wikilink") 16:54, 20 August 2008
(UTC)

## Compiling bunker.map

hoehrer (r18463 / Intel Core2 Quad 2.66GHz / 64bit Ubuntu 8.04
<small>Linux 2.6.24-19-generic</small>)

- time ./ufo2map -t 1 base/maps/bunker.map -\> 2m25.677s
- time ./ufo2map -t 2 base/maps/bunker.map -\> 1m3.230s
- time ./ufo2map -t 4 base/maps/bunker.map -\> 0m28.762s
- time ./ufo2map -t 5 base/maps/bunker.map -\> 0m28.406s
- time ./ufo2map -t 8 base/maps/bunker.map -\> 0m28.870s
- time ./ufo2map -extra -t 1 base/maps/bunker.map -\> 12m5.027s
- time ./ufo2map -extra -t 2 base/maps/bunker.map -\> 4m50.602s
- time ./ufo2map -extra -t 4 base/maps/bunker.map -\> 2m0.922s
- time ./ufo2map -extra -t 5 base/maps/bunker.map -\> 2m4.148s
- time ./ufo2map -extra -t 8 base/maps/bunker.map -\> 2m1.766s

btaxis (r18467 / Intel Core2 Duo 2.13GHz \[E6400\] / Windows XP Pro
Corporate 32bit SP3)

- ufo2map -t 1 base/maps/bunker.map: sum: 149 seconds elapsed
- ufo2map -t 2 base/maps/bunker.map: sum: 172 seconds elapsed
- make -j2 using Makefile.win, -extra enabled, all bsps deleted
  beforehand
  - starttime = 14:00:24.06
  - endtime = 15:41:32.12