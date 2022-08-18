Correct at 2.2_Jan_11_2008

Compares direct fire weapons (excludes grenade launcher, for example).
All point-blank damage : assumes no shots miss.
<b>mean damage rate (MDR)</b>
MDR=(damage×shots×num_discharges)/(reload+fd_time×num_discharges)
damage is damage from firedef in HP.
shots is the number of shots from firedef.
num_discharges = weap_ammo/fd_ammo.
fd_ammo is number of ammo units used per discharge using the firemode.
weap_ammo is number of ammo units the weapon can store.
reload is the time required to reload in TU.
fd_time is the time required to use a firemode in TU.I acknowledge
Surrealistik, who has done similar calculations (forum). blondandy
<b>firemode damage (FD)</b>
FD=damage×shots
Summary of [weapon tables](Weapon_tables "wikilink").

<table cellspacing="1" border="0" style="background:#404040; color:white ">
<tr style="background:#262626" align=center>
<td>

<b>gun</b>

</td>
<td>

<b>reload
(TU)</b>

</td>
<td>

<b>ammo type</b>

</td>
<td>

<b>fire mode</b>

</td>
<td>

<b>time
(TU)</b>

</td>
<td>

<b>damage</b>

</td>
<td>

<b>shots</b>

</td>
<td>

<b>MDR
(HP/TU)</b>

</td>
<td>

<b>FD
(HP)</b>

</td>
</tr>
<tr style="background:#101010" align=center>
<td>

Assault Rifle

</td>
<td>

12

</td>
<td>

Assault Rifle Magazine

</td>
<td>

Snap Shot

</td>
<td>

8

</td>
<td>

42 5

</td>
<td>

1

</td>
<td>

5.0

</td>
<td>

42.0

</td>
</tr>
<tr style="background:#101010" align=center>
<td>
</td>
<td>
</td>
<td>
</td>
<td>

3-Round Burst

</td>
<td>

12

</td>
<td>

42 5

</td>
<td>

3

</td>
<td>

9.5

</td>
<td>

126.0

</td>
</tr>
<tr style="background:#101010" align=center>
<td>
</td>
<td>
</td>
<td>
</td>
<td>

Full-Auto

</td>
<td>

18

</td>
<td>

42 5

</td>
<td>

8

</td>
<td>

15.8

</td>
<td>

336.0

</td>
</tr>
<tr style="background:#101010" align=center>
<td>
</td>
<td>
</td>
<td>
</td>
<td>

Aimed shot

</td>
<td>

16

</td>
<td>

42 5

</td>
<td>

1

</td>
<td>

2.6

</td>
<td>

42.0

</td>
</tr>
<tr style="background:#262626" align=center>
<td>

Minigun

</td>
<td>

20

</td>
<td>

Minigun Magazine

</td>
<td>

5-Round Burst

</td>
<td>

15

</td>
<td>

20 3

</td>
<td>

5

</td>
<td>

6.5

</td>
<td>

100.0

</td>
</tr>
<tr style="background:#262626" align=center>
<td>
</td>
<td>
</td>
<td>
</td>
<td>

Full-Auto

</td>
<td>

30

</td>
<td>

20 3

</td>
<td>

40

</td>
<td>

23.5

</td>
<td>

800.0

</td>
</tr>
<tr style="background:#262626" align=center>
<td>
</td>
<td>
</td>
<td>
</td>
<td>

Full-Auto Sweep

</td>
<td>

30

</td>
<td>

20 3

</td>
<td>

40

</td>
<td>

23.5

</td>
<td>

800.0

</td>
</tr>
<tr style="background:#101010" align=center>
<td>

Machine Gun

</td>
<td>

12

</td>
<td>

Machine Gun Magazine

</td>
<td>

Short Burst

</td>
<td>

12

</td>
<td>

25 5

</td>
<td>

6

</td>
<td>

11.4

</td>
<td>

150.0

</td>
</tr>
<tr style="background:#101010" align=center>
<td>
</td>
<td>
</td>
<td>
</td>
<td>

Full-Auto

</td>
<td>

18

</td>
<td>

25 5

</td>
<td>

14

</td>
<td>

16.8

</td>
<td>

350.0

</td>
</tr>
<tr style="background:#262626" align=center>
<td>

Sniper Rifle

</td>
<td>

10

</td>
<td>

Sniper Rifle Magazine

</td>
<td>

Snap Shot

</td>
<td>

12

</td>
<td>

105 0

</td>
<td>

1

</td>
<td>

7.5

</td>
<td>

105.0

</td>
</tr>
<tr style="background:#262626" align=center>
<td>
</td>
<td>
</td>
<td>
</td>
<td>

Aimed Shot

</td>
<td>

18

</td>
<td>

105 0

</td>
<td>

1

</td>
<td>

5.3

</td>
<td>

105.0

</td>
</tr>
<tr style="background:#262626" align=center>
<td>
</td>
<td>
</td>
<td>
</td>
<td>

Headshot

</td>
<td>

24

</td>
<td>

150 0

</td>
<td>

1

</td>
<td>

5.8

</td>
<td>

150.0

</td>
</tr>
<tr style="background:#101010" align=center>
<td>

7.62mm Pistol

</td>
<td>

12

</td>
<td>

7.62mm Pistol Magazine

</td>
<td>

Snap Shot

</td>
<td>

6

</td>
<td>

35 5

</td>
<td>

1

</td>
<td>

5.0

</td>
<td>

35.0

</td>
</tr>
<tr style="background:#101010" align=center>
<td>
</td>
<td>
</td>
<td>
</td>
<td>

3-Round Burst

</td>
<td>

8

</td>
<td>

35 5

</td>
<td>

3

</td>
<td>

9.5

</td>
<td>

105.0

</td>
</tr>
<tr style="background:#101010" align=center>
<td>
</td>
<td>
</td>
<td>
</td>
<td>

Aimed Shot

</td>
<td>

8

</td>
<td>

35 5

</td>
<td>

1

</td>
<td>

3.9

</td>
<td>

35.0

</td>
</tr>
<tr style="background:#262626" align=center>
<td>

Machine Pistol

</td>
<td>

12

</td>
<td>

4.2mm MP Magazine

</td>
<td>

Snap Shot

</td>
<td>

5

</td>
<td>

20 5

</td>
<td>

1

</td>
<td>

3.7

</td>
<td>

20.0

</td>
</tr>
<tr style="background:#262626" align=center>
<td>
</td>
<td>
</td>
<td>
</td>
<td>

3-Round Burst

</td>
<td>

7

</td>
<td>

20 5

</td>
<td>

3

</td>
<td>

7.3

</td>
<td>

60.0

</td>
</tr>
<tr style="background:#262626" align=center>
<td>
</td>
<td>
</td>
<td>
</td>
<td>

Full-Auto

</td>
<td>

14

</td>
<td>

20 5

</td>
<td>

8

</td>
<td>

9.3

</td>
<td>

160.0

</td>
</tr>
<tr style="background:#101010" align=center>
<td>

Submachine Gun

</td>
<td>

12

</td>
<td>

SMG Magazine

</td>
<td>

5-Round Burst

</td>
<td>

7

</td>
<td>

20 3

</td>
<td>

5

</td>
<td>

12.2

</td>
<td>

100.0

</td>
</tr>
<tr style="background:#101010" align=center>
<td>
</td>
<td>
</td>
<td>
</td>
<td>

Full-Auto

</td>
<td>

12

</td>
<td>

20 3

</td>
<td>

15

</td>
<td>

19.2

</td>
<td>

300.0

</td>
</tr>
<tr style="background:#262626" align=center>
<td>

Riot Shotgun

</td>
<td>

20

</td>
<td>

Saboted Slugs

</td>
<td>

Single Shot

</td>
<td>

8

</td>
<td>

50 10

</td>
<td>

1

</td>
<td>

4.6

</td>
<td>

50.0

</td>
</tr>
<tr style="background:#262626" align=center>
<td>
</td>
<td>
</td>
<td>
</td>
<td>

3-Round Burst

</td>
<td>

12

</td>
<td>

50 10

</td>
<td>

3

</td>
<td>

7.3

</td>
<td>

150.0

</td>
</tr>
<tr style="background:#262626" align=center>
<td>
</td>
<td>
</td>
<td>

Flechette Shells

</td>
<td>

Single Shot

</td>
<td>

8

</td>
<td>

15 5

</td>
<td>

8

</td>
<td>

11.1

</td>
<td>

120.0

</td>
</tr>
<tr style="background:#262626" align=center>
<td>
</td>
<td>
</td>
<td>
</td>
<td>

3-Round Burst

</td>
<td>

12

</td>
<td>

15 5

</td>
<td>

24

</td>
<td>

17.5

</td>
<td>

360.0

</td>
</tr>
<tr style="background:#262626" align=center>
<td>
</td>
<td>
</td>
<td>
</td>
<td>

Full-Auto

</td>
<td>

20

</td>
<td>

15 5

</td>
<td>

56

</td>
<td>

21.0

</td>
<td>

840.0

</td>
</tr>
<tr style="background:#101010" align=center>
<td>

Shotgun

</td>
<td>

20

</td>
<td>

Flechette Shells

</td>
<td>

Single Shot

</td>
<td>

8

</td>
<td>

11 0

</td>
<td>

10

</td>
<td>

10.1

</td>
<td>

110.0

</td>
</tr>
<tr style="background:#101010" align=center>
<td>
</td>
<td>
</td>
<td>
</td>
<td>

Double Shot

</td>
<td>

12

</td>
<td>

11 0

</td>
<td>

20

</td>
<td>

12.4

</td>
<td>

220.0

</td>
</tr>
<tr style="background:#262626" align=center>
<td>

Micro Shotgun

</td>
<td>

20

</td>
<td>

Flechette Shells

</td>
<td>

Single Shot

</td>
<td>

6

</td>
<td>

15 5

</td>
<td>

7

</td>
<td>

11.9

</td>
<td>

105.0

</td>
</tr>
<tr style="background:#262626" align=center>
<td>
</td>
<td>
</td>
<td>
</td>
<td>

3-Round Burst

</td>
<td>

10

</td>
<td>

15 5

</td>
<td>

21

</td>
<td>

17.0

</td>
<td>

315.0

</td>
</tr>
<tr style="background:#101010" align=center>
<td>

Flamethrower

</td>
<td>

14

</td>
<td>

C90 Canister

</td>
<td>

Candlelight

</td>
<td>

8

</td>
<td>

6 2

</td>
<td>

30

</td>
<td>

17.4

</td>
<td>

180.0

</td>
</tr>
<tr style="background:#101010" align=center>
<td>
</td>
<td>
</td>
<td>
</td>
<td>

Inferno

</td>
<td>

12

</td>
<td>

6 2

</td>
<td>

60

</td>
<td>

21.6

</td>
<td>

360.0

</td>
</tr>
<tr style="background:#101010" align=center>
<td>
</td>
<td>
</td>
<td>
</td>
<td>

Inferno Sweep

</td>
<td>

12

</td>
<td>

6 2

</td>
<td>

60

</td>
<td>

21.6

</td>
<td>

360.0

</td>
</tr>
<tr style="background:#262626" align=center>
<td>

Rocket Launcher

</td>
<td>

12

</td>
<td>

HE Rocket

</td>
<td>

Aimed Shot

</td>
<td>

14

</td>
<td>

0 0

</td>
<td>

1

</td>
<td>

0.0

</td>
<td>

0.0

</td>
</tr>
<tr style="background:#262626" align=center>
<td>
</td>
<td>
</td>
<td>

IC Rocket

</td>
<td>

Aimed Shot

</td>
<td>

14

</td>
<td>

0 0

</td>
<td>

1

</td>
<td>

0.0

</td>
<td>

0.0

</td>
</tr>
<tr style="background:#101010" align=center>
<td>

Grenade Launcher

</td>
<td>

14

</td>
<td>

25mm Flechette Grenades

</td>
<td>

Single Shot

</td>
<td>

8

</td>
<td>

6 2

</td>
<td>

24

</td>
<td>

15.1

</td>
<td>

144.0

</td>
</tr>
<tr style="background:#101010" align=center>
<td>
</td>
<td>
</td>
<td>
</td>
<td>

3-Round Burst

</td>
<td>

14

</td>
<td>

6 2

</td>
<td>

72

</td>
<td>

23.1

</td>
<td>

432.0

</td>
</tr>
<tr style="background:#262626" align=center>
<td>

Bolter Rifle

</td>
<td>

15

</td>
<td>

Bolter Rifle Magazine

</td>
<td>

Snap Shot

</td>
<td>

8

</td>
<td>

80 5

</td>
<td>

1

</td>
<td>

8.6

</td>
<td>

80.0

</td>
</tr>
<tr style="background:#262626" align=center>
<td>
</td>
<td>
</td>
<td>
</td>
<td>

Cannonade

</td>
<td>

13

</td>
<td>

80 5

</td>
<td>

3

</td>
<td>

14.3

</td>
<td>

240.0

</td>
</tr>
<tr style="background:#262626" align=center>
<td>
</td>
<td>
</td>
<td>
</td>
<td>

Precision Shot

</td>
<td>

16

</td>
<td>

100 5

</td>
<td>

1

</td>
<td>

5.8

</td>
<td>

100.0

</td>
</tr>
<tr style="background:#101010" align=center>
<td>

Laser Pistol

</td>
<td>

8

</td>
<td>

D-F Cartridge

</td>
<td>

Wave Fire

</td>
<td>

7

</td>
<td>

60 20

</td>
<td>

1

</td>
<td>

7.9

</td>
<td>

60.0

</td>
</tr>
<tr style="background:#101010" align=center>
<td>
</td>
<td>
</td>
<td>
</td>
<td>

Pulsed Fire

</td>
<td>

10

</td>
<td>

35 10

</td>
<td>

3

</td>
<td>

9.6

</td>
<td>

105.0

</td>
</tr>
<tr style="background:#262626" align=center>
<td>

Laser Rifle

</td>
<td>

12

</td>
<td>

D-F Cartridge

</td>
<td>

Wave Fire

</td>
<td>

9

</td>
<td>

75 20

</td>
<td>

1

</td>
<td>

7.1

</td>
<td>

75.0

</td>
</tr>
<tr style="background:#262626" align=center>
<td>
</td>
<td>
</td>
<td>
</td>
<td>

Pulsed Fire

</td>
<td>

13

</td>
<td>

40 10

</td>
<td>

3

</td>
<td>

7.9

</td>
<td>

120.0

</td>
</tr>
<tr style="background:#101010" align=center>
<td>

Heavy Laser

</td>
<td>

16

</td>
<td>

D-F Cartridge

</td>
<td>

Wave Fire

</td>
<td>

12

</td>
<td>

90 25

</td>
<td>

1

</td>
<td>

5.2

</td>
<td>

90.0

</td>
</tr>
<tr style="background:#101010" align=center>
<td>
</td>
<td>
</td>
<td>
</td>
<td>

Pulsed Fire

</td>
<td>

18

</td>
<td>

50 15

</td>
<td>

3

</td>
<td>

5.8

</td>
<td>

150.0

</td>
</tr>
<tr style="background:#262626" align=center>
<td>

Particle Beam Pistol

</td>
<td>

14

</td>
<td>

Pistol Particle Accelerator

</td>
<td>

Snap Shot

</td>
<td>

7

</td>
<td>

60 10

</td>
<td>

1

</td>
<td>

7.6

</td>
<td>

60.0

</td>
</tr>
<tr style="background:#262626" align=center>
<td>
</td>
<td>
</td>
<td>
</td>
<td>

Rapid Shots

</td>
<td>

11

</td>
<td>

60 10

</td>
<td>

3

</td>
<td>

13.2

</td>
<td>

180.0

</td>
</tr>
<tr style="background:#101010" align=center>
<td>

Particle Beam Rifle

</td>
<td>

14

</td>
<td>

Rifle Particle Accelerator

</td>
<td>

Snap Shot

</td>
<td>

10

</td>
<td>

90 15

</td>
<td>

1

</td>
<td>

8.1

</td>
<td>

90.0

</td>
</tr>
<tr style="background:#101010" align=center>
<td>
</td>
<td>
</td>
<td>
</td>
<td>

Aimed Shot

</td>
<td>

15

</td>
<td>

90 15

</td>
<td>

1

</td>
<td>

5.6

</td>
<td>

90.0

</td>
</tr>
<tr style="background:#101010" align=center>
<td>
</td>
<td>
</td>
<td>
</td>
<td>

Repeat Fire

</td>
<td>

16

</td>
<td>

90 15

</td>
<td>

3

</td>
<td>

13.8

</td>
<td>

270.0

</td>
</tr>
<tr style="background:#262626" align=center>
<td>

Particle Beam Cannon

</td>
<td>

16

</td>
<td>

Cannon Particle Accelerator

</td>
<td>

Snap Shot

</td>
<td>

17

</td>
<td>

150 20

</td>
<td>

1

</td>
<td>

7.9

</td>
<td>

150.0

</td>
</tr>
<tr style="background:#262626" align=center>
<td>
</td>
<td>
</td>
<td>
</td>
<td>

Rapid Shots

</td>
<td>

24

</td>
<td>

150 20

</td>
<td>

4

</td>
<td>

18.8

</td>
<td>

600.0

</td>
</tr>
<tr style="background:#262626" align=center>
<td>
</td>
<td>
</td>
<td>
</td>
<td>

Unrestricted Blast

</td>
<td>

28

</td>
<td>

0 0

</td>
<td>

1

</td>
<td>

0.0

</td>
<td>

0.0

</td>
</tr>
<tr style="background:#101010" align=center>
<td>

Plasma Pistol

</td>
<td>

12

</td>
<td>

Plasma Pistol Charger

</td>
<td>

Snap Shot

</td>
<td>

6

</td>
<td>

45 7

</td>
<td>

1

</td>
<td>

6.0

</td>
<td>

45.0

</td>
</tr>
<tr style="background:#101010" align=center>
<td>
</td>
<td>
</td>
<td>
</td>
<td>

Burst

</td>
<td>

10

</td>
<td>

45 7

</td>
<td>

3

</td>
<td>

9.3

</td>
<td>

135.0

</td>
</tr>
<tr style="background:#262626" align=center>
<td>

Plasma Rifle

</td>
<td>

14

</td>
<td>

Plasma Rifle Charger

</td>
<td>

Snap Shot

</td>
<td>

9

</td>
<td>

60 10

</td>
<td>

1

</td>
<td>

5.1

</td>
<td>

60.0

</td>
</tr>
<tr style="background:#262626" align=center>
<td>
</td>
<td>
</td>
<td>
</td>
<td>

Aimed Shot

</td>
<td>

15

</td>
<td>

60 10

</td>
<td>

1

</td>
<td>

3.4

</td>
<td>

60.0

</td>
</tr>
<tr style="background:#262626" align=center>
<td>
</td>
<td>
</td>
<td>
</td>
<td>

Burst

</td>
<td>

16

</td>
<td>

60 10

</td>
<td>

3

</td>
<td>

7.8

</td>
<td>

180.0

</td>
</tr>
<tr style="background:#101010" align=center>
<td>

Plasma Blaster

</td>
<td>

18

</td>
<td>

Plasma Blaster Charge

</td>
<td>

Snap Shot

</td>
<td>

13

</td>
<td>

80 15

</td>
<td>

1

</td>
<td>

6.0

</td>
<td>

80.0

</td>
</tr>
<tr style="background:#101010" align=center>
<td>
</td>
<td>
</td>
<td>
</td>
<td>

Ball

</td>
<td>

17

</td>
<td>

0 0

</td>
<td>

1

</td>
<td>

0.0

</td>
<td>

0.0

</td>
</tr>
<tr style="background:#101010" align=center>
<td>
</td>
<td>
</td>
<td>
</td>
<td>

Burst

</td>
<td>

24

</td>
<td>

80 15

</td>
<td>

5

</td>
<td>

15.5

</td>
<td>

400.0

</td>
</tr>
</table>