## Compare times

- Use latest Git: git pull --rebase
  - Please always give the (first 7 characters of) Git revision hash you
    compiled ufo2map with (and ensure your maps are from the same
    revision).
- Compile ufo2map
- Compile the maps and stop the time.
  - Windows: "cd contrib\scripts", "compile_maps.bat /clean". it reports
    start and finish times on completion. repeat with "/-t" to enforce
    -t 1.
  - Linux: to delete \*.bsp "make clean-maps", then "time make maps".
    the real time is the one you want
    - You can force a specific number of threads with e.g. "time make
      maps NUMTHREADS=2"
    - The number of jobs that make executes at the same time can be
      changed with something like "time make maps -j4"
    - Combine if you like :)

## Results

<table>
<thead>
<tr class="header">
<th><p>Time<br />
hh:mm</p></th>
<th><p>Processor</p></th>
<th><p>Cores</p></th>
<th><p>ufo2map -t<br />
make -j</p></th>
<th><p>RAM</p></th>
<th><p>OS and Bit</p></th>
<th><p>Revision</p></th>
<th><p>Nick</p></th>
<th><p>Remarks</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>01:02</p></td>
<td><p>i7-3630QM<br />
2.4 GHz</p></td>
<td><p>4/8</p></td>
<td><p>-t 1 -j 12</p></td>
<td><p>6 GB</p></td>
<td><p>Win 8 / 64</p></td>
<td><p>15.11.2012</p></td>
<td><p>Duke</p></td>
<td><p>1) 6)</p></td>
</tr>
</tbody>
</table>

## Old results

<table>
<thead>
<tr class="header">
<th><p>Time<br />
hh:mm</p></th>
<th><p>Processor</p></th>
<th><p>Cores</p></th>
<th><p>ufo2map -t<br />
make -j</p></th>
<th><p>RAM</p></th>
<th><p>OS and Bit</p></th>
<th><p>Revision</p></th>
<th><p>Nick</p></th>
<th><p>Remarks</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>00:27</p></td>
<td><p>Intel Core(TM)i7 920 2.67 GHz</p></td>
<td><p>4/8</p></td>
<td><p>-j 5 -t 8</p></td>
<td><p>3GB</p></td>
<td><p>64bit Vista</p></td>
<td><p>31971</p></td>
<td><p>Duke</p></td>
<td><p>1) 2) now with lighting threshold</p></td>
</tr>
<tr class="even">
<td><p>01:06</p></td>
<td><p>Intel Core(TM)i7 920 2.67 GHz</p></td>
<td><p>4/8</p></td>
<td><p>-j 5 -t 8</p></td>
<td><p>3GB</p></td>
<td><p>64bit Vista</p></td>
<td><p>31955</p></td>
<td><p>Duke</p></td>
<td><p>1) 2) now with +city</p></td>
</tr>
<tr class="odd">
<td><p>00:16</p></td>
<td><p>Intel Xeon(TM) w3520 2.67 GHz</p></td>
<td><p>4/8</p></td>
<td><hr /></td>
<td><p>4GB</p></td>
<td><p>32bit XP</p></td>
<td><p>27548</p></td>
<td><p>Muton</p></td>
<td><p>1) 4) 5)</p></td>
</tr>
<tr class="even">
<td><p>00:49</p></td>
<td><p>Intel Xeon(TM) w3520 2.67 GHz</p></td>
<td><p>4/8</p></td>
<td><p>-t 8</p></td>
<td><p>4GB</p></td>
<td><p>32bit XP</p></td>
<td><p>27548</p></td>
<td><p>Muton</p></td>
<td><p>3)</p></td>
</tr>
<tr class="odd">
<td><p>00:34</p></td>
<td><p>Intel Xeon(TM) w3520 2.67 GHz</p></td>
<td><p>4/8</p></td>
<td><p>-t 8</p></td>
<td><p>4GB</p></td>
<td><p>32bit XP</p></td>
<td><p>27548</p></td>
<td><p>Muton</p></td>
<td><p>1) 3)</p></td>
</tr>
<tr class="even">
<td><p>00:26</p></td>
<td><p>Intel Core(TM)i7 920 2.67 GHz</p></td>
<td><p>4/8</p></td>
<td><p>-j 5 -t 4</p></td>
<td><p>3GB</p></td>
<td><p>64bit Vista</p></td>
<td><p>27334</p></td>
<td><p>Duke</p></td>
<td><p>1) 2)</p></td>
</tr>
<tr class="odd">
<td><p>00:37</p></td>
<td><p>Intel Core(TM)i7 920 2.67 GHz</p></td>
<td><p>4/8</p></td>
<td><p>-j 1 -t 8</p></td>
<td><p>3GB</p></td>
<td><p>64bit Vista</p></td>
<td><p>27334</p></td>
<td><p>Duke</p></td>
<td><p>1) 3)</p></td>
</tr>
<tr class="even">
<td><p>00:40</p></td>
<td><p>Phenom X4 940 3.0 GHz</p></td>
<td><p>4</p></td>
<td><p>-j 5</p></td>
<td><p>4GB</p></td>
<td><p>64bit Kubuntu 9.04</p></td>
<td><p>24705</p></td>
<td><p>Catty Nebulart</p></td>
<td></td>
</tr>
<tr class="odd">
<td><p>00:35</p></td>
<td><p>Intel Core(TM)2 Quad Q8200 2.33GHz</p></td>
<td><p>4</p></td>
<td><p>-j 5</p></td>
<td><p>4GB</p></td>
<td><p>64bit Ubuntu 9.04</p></td>
<td><p>25142</p></td>
<td><p>mattn</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>01:57</p></td>
<td><p>Intel Core(TM)2 Duo E6550 2.33GHz</p></td>
<td><p>2</p></td>
<td><p>-j 4</p></td>
<td><p>2GB</p></td>
<td><p>64bit Ubuntu 8.04</p></td>
<td><p>25277</p></td>
<td><p>geever</p></td>
<td></td>
</tr>
<tr class="odd">
<td><p>00:54</p></td>
<td><p>Intel Pentium® Dual CPU T2390 1.86GHz</p></td>
<td><p>2</p></td>
<td><p>-j 2</p></td>
<td><p>2GB</p></td>
<td><p>32bit Ubuntu 9.04<br />
<small>Linux 2.6.28-13-generic</small></p></td>
<td><p>25295</p></td>
<td><p>ulidtko</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>08:24</p></td>
<td><p>AMD AthlonXP 2000+ 1667MHz</p></td>
<td><p>1</p></td>
<td><p>-j 4</p></td>
<td><p>1GB</p></td>
<td><p>32bit Debian Etch</p></td>
<td><p>25527</p></td>
<td><p>geever</p></td>
<td></td>
</tr>
<tr class="odd">
<td><p>01:51</p></td>
<td><p>AMD x86 64 2.0GHz</p></td>
<td><p>2</p></td>
<td><p>-t 2</p></td>
<td><p>2GB</p></td>
<td><p>32bit Vista</p></td>
<td><p>18441</p></td>
<td><p>blondandy</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>03:56</p></td>
<td><p>AMD x86 64 2.0GHz</p></td>
<td><p>2</p></td>
<td><p>-t 1</p></td>
<td><p>2GB</p></td>
<td><p>32bit Vista</p></td>
<td><p>18441</p></td>
<td><p>blondandy</p></td>
<td></td>
</tr>
<tr class="odd">
<td><p>04:06</p></td>
<td><p>AMD x86 64 2.2GHz</p></td>
<td><p>1</p></td>
<td><p>-t 1</p></td>
<td><p>3.3GB</p></td>
<td><p>32bit XP</p></td>
<td><p>18441</p></td>
<td><p>blondandy</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>02:29</p></td>
<td><p>AMD x86 64 2.0GHz</p></td>
<td><p>2</p></td>
<td><p>-t 2</p></td>
<td><p>2GB</p></td>
<td><p>64bit openSuSE 11.0</p></td>
<td><p>18441</p></td>
<td><p>blondandy</p></td>
<td></td>
</tr>
<tr class="odd">
<td><p>01:11</p></td>
<td><p>Intel Core2 Quad 2.66GHz</p></td>
<td><p>4</p></td>
<td><p>-t 4<br />
-j5</p></td>
<td><p>8GB <small>(7.8 Gib)</small></p></td>
<td><p>64bit Ubuntu 8.04<br />
<small>Linux 2.6.24-19-generic</small></p></td>
<td><p>18441</p></td>
<td><p>hoehrer</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>01:21</p></td>
<td><p>Intel Core2 Quad 2.66GHz</p></td>
<td><p>4</p></td>
<td><p>-t 4</p></td>
<td><p>8GB <small>(7.8 Gib)</small></p></td>
<td><p>64bit Ubuntu 8.04<br />
<small>Linux 2.6.24-19-generic</small></p></td>
<td><p>18441</p></td>
<td><p>hoehrer</p></td>
<td></td>
</tr>
<tr class="odd">
<td><p><s>00:40</s><br />
01:19</p></td>
<td><p>Intel Core2 Quad 2.66GHz</p></td>
<td><p>4</p></td>
<td><p>-t 1<br />
-j4 NUMTHREADS=1</p></td>
<td><p>8GB <small>(7.8 Gib)</small></p></td>
<td><p>64bit Ubuntu 8.04<br />
<small>Linux 2.6.24-19-generic</small></p></td>
<td><p>18463</p></td>
<td><p>hoehrer</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>06:53</p></td>
<td><p>Intel Pentium III 733MHz</p></td>
<td><p>1</p></td>
<td><p>-t 1</p></td>
<td><p>512MB</p></td>
<td><p>32bit Slackware-current</p></td>
<td><p>18601</p></td>
<td><p>richlv</p></td>
<td></td>
</tr>
</tbody>
</table>

1\) compiled ufo2map with -O3 and -march=core2
2) used msys to start make under Vista as described above for linux
3) using compile_maps.bat
4) using make_UfoAI_win32.exe
5) gcc option -msse4.2 -mfpmath=sse 6) used msys to start make under
Windows 8 as described above for linux

[Category:Mapping](Category:Mapping "wikilink")