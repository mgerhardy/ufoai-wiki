Correct at 2.2_Jan_11_2008

Compares direct fire weapons (excludes grenade launcher, for example).
weapon spread is intrinsic to the gun. it is the minimum spread, the
limit which cannot be improved with better actor statistics (it is
improved by crouching).
spread50 is the spread modified by firedef.crouch (<i>ie</i> assumes the
actor is crouching), using an accuracy of 50. spread100 is similar, but
assumes the actor's accuracy has maxed out.
{spread+\[1-accuracy/max_skill\]}×crouch
see ufo scripts page for spread calculation
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

<b>crouch</b>

</td>
<td>

<b>weapon
spread
(degrees)</b>

</td>
<td>

<b>spread50
(degrees)</b>

</td>
<td>

<b>spread100
(degrees)</b>

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

0.7

</td>
<td>

1.8 1.8

</td>
<td>

1.6 1.6

</td>
<td>

1.3 1.3

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

0.7

</td>
<td>

1.8 1.8

</td>
<td>

1.6 1.6

</td>
<td>

1.3 1.3

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

0.6

</td>
<td>

2.5 2.5

</td>
<td>

1.8 1.8

</td>
<td>

1.5 1.5

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

0.7

</td>
<td>

1.0 1.0

</td>
<td>

1.0 1.0

</td>
<td>

0.7 0.7

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

1.3

</td>
<td>

0.5 2.0

</td>
<td>

1.3 3.3

</td>
<td>

0.6 2.6

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

1.3

</td>
<td>

1.5 3.0

</td>
<td>

2.6 4.5

</td>
<td>

1.9 3.9

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

1.3

</td>
<td>

1.5 7.5

</td>
<td>

2.6 10.4

</td>
<td>

1.9 9.8

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

0.9

</td>
<td>

2.0 2.0

</td>
<td>

2.3 2.3

</td>
<td>

1.8 1.8

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

0.9

</td>
<td>

2.0 2.0

</td>
<td>

2.3 2.3

</td>
<td>

1.8 1.8

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

0.3

</td>
<td>

1.5 1.5

</td>
<td>

0.6 0.6

</td>
<td>

0.5 0.5

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

0.3

</td>
<td>

0.9 0.9

</td>
<td>

0.4 0.4

</td>
<td>

0.3 0.3

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

0.3

</td>
<td>

0.9 0.9

</td>
<td>

0.4 0.4

</td>
<td>

0.3 0.3

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

0.9

</td>
<td>

1.1 1.1

</td>
<td>

1.4 1.4

</td>
<td>

1.0 1.0

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

0.9

</td>
<td>

1.3 1.3

</td>
<td>

1.6 1.6

</td>
<td>

1.2 1.2

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

0.9

</td>
<td>

1.0 1.0

</td>
<td>

1.3 1.3

</td>
<td>

0.9 0.9

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

0.9

</td>
<td>

1.5 1.5

</td>
<td>

1.8 1.8

</td>
<td>

1.3 1.3

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

0.9

</td>
<td>

1.6 1.6

</td>
<td>

1.9 1.9

</td>
<td>

1.4 1.4

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

0.9

</td>
<td>

1.7 1.7

</td>
<td>

2.0 2.0

</td>
<td>

1.5 1.5

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

0.7

</td>
<td>

1.7 1.7

</td>
<td>

1.5 1.5

</td>
<td>

1.2 1.2

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

0.7

</td>
<td>

1.8 1.8

</td>
<td>

1.6 1.6

</td>
<td>

1.3 1.3

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

0.8

</td>
<td>

1.5 1.5

</td>
<td>

1.6 1.6

</td>
<td>

1.2 1.2

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

0.8

</td>
<td>

2.5 2.5

</td>
<td>

2.4 2.4

</td>
<td>

2.0 2.0

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

1.0

</td>
<td>

1.8 1.8

</td>
<td>

2.3 2.3

</td>
<td>

1.8 1.8

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

1.0

</td>
<td>

2.8 2.8

</td>
<td>

3.3 3.3

</td>
<td>

2.8 2.8

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

1.0

</td>
<td>

3.0 3.0

</td>
<td>

3.5 3.5

</td>
<td>

3.0 3.0

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

1.0

</td>
<td>

1.8 1.8

</td>
<td>

2.3 2.3

</td>
<td>

1.8 1.8

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

1.0

</td>
<td>

2.8 2.8

</td>
<td>

3.3 3.3

</td>
<td>

2.8 2.8

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

0.9

</td>
<td>

1.3 1.3

</td>
<td>

1.6 1.6

</td>
<td>

1.2 1.2

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

0.9

</td>
<td>

2.8 2.8

</td>
<td>

3.0 3.0

</td>
<td>

2.5 2.5

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

1.0

</td>
<td>

1.5 0.5

</td>
<td>

2.0 1.0

</td>
<td>

1.5 0.5

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

1.0

</td>
<td>

2.0 0.5

</td>
<td>

2.5 1.0

</td>
<td>

2.0 0.5

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

1.0

</td>
<td>

1.0 10.0

</td>
<td>

1.5 10.5

</td>
<td>

1.0 10.0

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

0.6

</td>
<td>

0.2 0.6

</td>
<td>

0.4 0.7

</td>
<td>

0.1 0.4

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

0.6

</td>
<td>

0.2 0.6

</td>
<td>

0.4 0.7

</td>
<td>

0.1 0.4

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
</td>
<td>

4.0 4.5

</td>
<td>

4.5 5.0

</td>
<td>

4.0 4.5

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
</td>
<td>

5.0 5.5

</td>
<td>

5.5 6.0

</td>
<td>

5.0 5.5

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

0.8

</td>
<td>

1.7 1.7

</td>
<td>

1.8 1.8

</td>
<td>

1.4 1.4

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

0.8

</td>
<td>

2.1 2.1

</td>
<td>

2.1 2.1

</td>
<td>

1.7 1.7

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

0.5

</td>
<td>

1.2 1.2

</td>
<td>

0.9 0.9

</td>
<td>

0.6 0.6

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

0.9

</td>
<td>

0.4 0.4

</td>
<td>

0.8 0.8

</td>
<td>

0.4 0.4

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

0.9

</td>
<td>

0.4 0.4

</td>
<td>

0.8 0.8

</td>
<td>

0.4 0.4

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

0.7

</td>
<td>

0.5 0.5

</td>
<td>

0.7 0.7

</td>
<td>

0.3 0.3

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

0.7

</td>
<td>

0.5 0.5

</td>
<td>

0.7 0.7

</td>
<td>

0.3 0.3

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

0.5

</td>
<td>

1.0 1.0

</td>
<td>

0.8 0.8

</td>
<td>

0.5 0.5

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

0.5

</td>
<td>

1.0 1.0

</td>
<td>

0.8 0.8

</td>
<td>

0.5 0.5

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

0.9

</td>
<td>

1.0 1.0

</td>
<td>

1.3 1.3

</td>
<td>

0.9 0.9

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

0.9

</td>
<td>

1.8 1.8

</td>
<td>

2.1 2.1

</td>
<td>

1.6 1.6

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

0.7

</td>
<td>

1.5 1.5

</td>
<td>

1.4 1.4

</td>
<td>

1.0 1.0

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

0.7

</td>
<td>

1.0 1.0

</td>
<td>

1.0 1.0

</td>
<td>

0.7 0.7

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

0.7

</td>
<td>

2.0 2.0

</td>
<td>

1.8 1.8

</td>
<td>

1.4 1.4

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

0.6

</td>
<td>

1.8 1.8

</td>
<td>

1.4 1.4

</td>
<td>

1.1 1.1

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

0.6

</td>
<td>

2.5 2.5

</td>
<td>

1.8 1.8

</td>
<td>

1.5 1.5

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

0.8

</td>
<td>

1.5 1.5

</td>
<td>

1.6 1.6

</td>
<td>

1.2 1.2

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

0.8

</td>
<td>

1.1 1.1

</td>
<td>

1.3 1.3

</td>
<td>

0.9 0.9

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

0.8

</td>
<td>

1.4 1.4

</td>
<td>

1.5 1.5

</td>
<td>

1.1 1.1

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

0.7

</td>
<td>

1.7 1.7

</td>
<td>

1.5 1.5

</td>
<td>

1.2 1.2

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

0.7

</td>
<td>

1.0 1.0

</td>
<td>

1.0 1.0

</td>
<td>

0.7 0.7

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

0.7

</td>
<td>

1.7 1.7

</td>
<td>

1.5 1.5

</td>
<td>

1.2 1.2

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

0.6

</td>
<td>

2.2 2.2

</td>
<td>

1.6 1.6

</td>
<td>

1.3 1.3

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

0.6

</td>
<td>

2.0 2.0

</td>
<td>

1.5 1.5

</td>
<td>

1.2 1.2

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

0.6

</td>
<td>

3.0 3.0

</td>
<td>

2.1 2.1

</td>
<td>

1.8 1.8

</td>
</tr>
</table>