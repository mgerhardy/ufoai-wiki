Correct at 2.2_Jan_11_2008

Compares direct fire weapons (excludes grenade launcher, for example).
MDRx,y is the mean damage rate for an accuracy of x at a distance of y
map squares
calc uses the spread modified by firedef.crouch (<i>ie</i> assumes the
actor is crouching).
standard deviation in distance units, sigma
=(pi/180)×(range)×0.5×{spread+(1-accuracy/max_skill)}×crouch
see G_ShootSingle() from g_combat.c
modelling target as 24×56 rectangle (see modelling article), this will
be a slight overestimate.
hit probability,
p=erf(recx×sqrt(2)/(4×sigmax))×erf(recy×sqrt(2)/(4×sigmay))
where erf() is the error function (integral of a gaussian).
Summary of [weapon tables](Weapon_tables "wikilink").

<table cellspacing="1" border="0" style="background:#404040; color:white ">
<tr style="background:#262626" align=center>
<td>

<b>gun</b>

</td>
<td>

<b>ammo type</b>

</td>
<td>

<b>fire mode</b>

</td>
<td>

<b>MDR50,8
(HP/TU)</b>

</td>
<td>

<b>MDR50,16
(HP/TU)</b>

</td>
<td>

<b>MDR50,32
(HP/TU)</b>

</td>
<td>

<b>MDR50,64
(HP/TU)</b>

</td>
<td>

<b>MDR50,128
(HP/TU)</b>

</td>
</tr>
<tr style="background:#101010" align=center>
<td>

Assault Rifle

</td>
<td>

Assault Rifle Magazine

</td>
<td>

Snap Shot

</td>
<td>

5.0

</td>
<td>

4.5

</td>
<td>

2.8

</td>
<td>

1.1

</td>
<td>

\-

</td>
</tr>
<tr style="background:#101010" align=center>
<td>
</td>
<td>
</td>
<td>

3-Round Burst

</td>
<td>

9.5

</td>
<td>

8.6

</td>
<td>

5.4

</td>
<td>

2.1

</td>
<td>

\-

</td>
</tr>
<tr style="background:#101010" align=center>
<td>
</td>
<td>
</td>
<td>

Full-Auto

</td>
<td>

15.8

</td>
<td>

13.7

</td>
<td>

7.9

</td>
<td>

2.8

</td>
<td>

\-

</td>
</tr>
<tr style="background:#101010" align=center>
<td>
</td>
<td>
</td>
<td>

Aimed shot

</td>
<td>

2.6

</td>
<td>

2.5

</td>
<td>

2.0

</td>
<td>

1.1

</td>
<td>

\-

</td>
</tr>
<tr style="background:#262626" align=center>
<td>

Minigun

</td>
<td>

Minigun Magazine

</td>
<td>

5-Round Burst

</td>
<td>

5.8

</td>
<td>

3.8

</td>
<td>

2.0

</td>
<td>

\-

</td>
<td>

\-

</td>
</tr>
<tr style="background:#262626" align=center>
<td>
</td>
<td>
</td>
<td>

Full-Auto

</td>
<td>

17.9

</td>
<td>

10.3

</td>
<td>

4.2

</td>
<td>

\-

</td>
<td>

\-

</td>
</tr>
<tr style="background:#262626" align=center>
<td>
</td>
<td>
</td>
<td>

Full-Auto Sweep

</td>
<td>

9.3

</td>
<td>

4.7

</td>
<td>

1.9

</td>
<td>

\-

</td>
<td>

\-

</td>
</tr>
<tr style="background:#101010" align=center>
<td>

Machine Gun

</td>
<td>

Machine Gun Magazine

</td>
<td>

Short Burst

</td>
<td>

11.2

</td>
<td>

8.7

</td>
<td>

4.3

</td>
<td>

1.4

</td>
<td>

\-

</td>
</tr>
<tr style="background:#101010" align=center>
<td>
</td>
<td>
</td>
<td>

Full-Auto

</td>
<td>

16.5

</td>
<td>

12.8

</td>
<td>

6.3

</td>
<td>

2.0

</td>
<td>

\-

</td>
</tr>
<tr style="background:#262626" align=center>
<td>

Sniper Rifle

</td>
<td>

Sniper Rifle Magazine

</td>
<td>

Snap Shot

</td>
<td>

7.5

</td>
<td>

7.5

</td>
<td>

7.3

</td>
<td>

5.5

</td>
<td>

2.6

</td>
</tr>
<tr style="background:#262626" align=center>
<td>
</td>
<td>
</td>
<td>

Aimed Shot

</td>
<td>

5.3

</td>
<td>

5.3

</td>
<td>

5.2

</td>
<td>

4.7

</td>
<td>

2.8

</td>
</tr>
<tr style="background:#262626" align=center>
<td>
</td>
<td>
</td>
<td>

Headshot

</td>
<td>

5.8

</td>
<td>

5.8

</td>
<td>

5.8

</td>
<td>

5.1

</td>
<td>

3.1

</td>
</tr>
<tr style="background:#101010" align=center>
<td>

7.62mm Pistol

</td>
<td>

7.62mm Pistol Magazine

</td>
<td>

Snap Shot

</td>
<td>

5.0

</td>
<td>

4.7

</td>
<td>

3.1

</td>
<td>

\-

</td>
<td>

\-

</td>
</tr>
<tr style="background:#101010" align=center>
<td>
</td>
<td>
</td>
<td>

3-Round Burst

</td>
<td>

9.5

</td>
<td>

8.6

</td>
<td>

5.4

</td>
<td>

\-

</td>
<td>

\-

</td>
</tr>
<tr style="background:#101010" align=center>
<td>
</td>
<td>
</td>
<td>

Aimed Shot

</td>
<td>

3.9

</td>
<td>

3.7

</td>
<td>

2.6

</td>
<td>

\-

</td>
<td>

\-

</td>
</tr>
<tr style="background:#262626" align=center>
<td>

Machine Pistol

</td>
<td>

4.2mm MP Magazine

</td>
<td>

Snap Shot

</td>
<td>

3.7

</td>
<td>

3.2

</td>
<td>

1.9

</td>
<td>

\-

</td>
<td>

\-

</td>
</tr>
<tr style="background:#262626" align=center>
<td>
</td>
<td>
</td>
<td>

3-Round Burst

</td>
<td>

7.3

</td>
<td>

6.2

</td>
<td>

3.5

</td>
<td>

\-

</td>
<td>

\-

</td>
</tr>
<tr style="background:#262626" align=center>
<td>
</td>
<td>
</td>
<td>

Full-Auto

</td>
<td>

9.2

</td>
<td>

7.7

</td>
<td>

4.1

</td>
<td>

\-

</td>
<td>

\-

</td>
</tr>
<tr style="background:#101010" align=center>
<td>

Submachine Gun

</td>
<td>

SMG Magazine

</td>
<td>

5-Round Burst

</td>
<td>

12.2

</td>
<td>

11.2

</td>
<td>

7.2

</td>
<td>

\-

</td>
<td>

\-

</td>
</tr>
<tr style="background:#101010" align=center>
<td>
</td>
<td>
</td>
<td>

Full-Auto

</td>
<td>

19.2

</td>
<td>

17.4

</td>
<td>

10.9

</td>
<td>

\-

</td>
<td>

\-

</td>
</tr>
<tr style="background:#262626" align=center>
<td>

Riot Shotgun

</td>
<td>

Saboted Slugs

</td>
<td>

Single Shot

</td>
<td>

4.6

</td>
<td>

4.2

</td>
<td>

\-

</td>
<td>

\-

</td>
<td>

\-

</td>
</tr>
<tr style="background:#262626" align=center>
<td>
</td>
<td>
</td>
<td>

3-Round Burst

</td>
<td>

7.1

</td>
<td>

5.3

</td>
<td>

\-

</td>
<td>

\-

</td>
<td>

\-

</td>
</tr>
<tr style="background:#262626" align=center>
<td>
</td>
<td>

Flechette Shells

</td>
<td>

Single Shot

</td>
<td>

10.8

</td>
<td>

\-

</td>
<td>

\-

</td>
<td>

\-

</td>
<td>

\-

</td>
</tr>
<tr style="background:#262626" align=center>
<td>
</td>
<td>
</td>
<td>

3-Round Burst

</td>
<td>

15.7

</td>
<td>

\-

</td>
<td>

\-

</td>
<td>

\-

</td>
<td>

\-

</td>
</tr>
<tr style="background:#262626" align=center>
<td>
</td>
<td>
</td>
<td>

Full-Auto

</td>
<td>

18.4

</td>
<td>

\-

</td>
<td>

\-

</td>
<td>

\-

</td>
<td>

\-

</td>
</tr>
<tr style="background:#101010" align=center>
<td>

Shotgun

</td>
<td>

Flechette Shells

</td>
<td>

Single Shot

</td>
<td>

9.9

</td>
<td>

7.6

</td>
<td>

3.7

</td>
<td>

\-

</td>
<td>

\-

</td>
</tr>
<tr style="background:#101010" align=center>
<td>
</td>
<td>
</td>
<td>

Double Shot

</td>
<td>

11.1

</td>
<td>

6.8

</td>
<td>

2.6

</td>
<td>

\-

</td>
<td>

\-

</td>
</tr>
<tr style="background:#262626" align=center>
<td>

Micro Shotgun

</td>
<td>

Flechette Shells

</td>
<td>

Single Shot

</td>
<td>

11.8

</td>
<td>

\-

</td>
<td>

\-

</td>
<td>

\-

</td>
<td>

\-

</td>
</tr>
<tr style="background:#262626" align=center>
<td>
</td>
<td>
</td>
<td>

3-Round Burst

</td>
<td>

15.8

</td>
<td>

\-

</td>
<td>

\-

</td>
<td>

\-

</td>
<td>

\-

</td>
</tr>
<tr style="background:#101010" align=center>
<td>

Flamethrower

</td>
<td>

C90 Canister

</td>
<td>

Candlelight

</td>
<td>

17.4

</td>
<td>

\-

</td>
<td>

\-

</td>
<td>

\-

</td>
<td>

\-

</td>
</tr>
<tr style="background:#101010" align=center>
<td>
</td>
<td>
</td>
<td>

Inferno

</td>
<td>

21.6

</td>
<td>

\-

</td>
<td>

\-

</td>
<td>

\-

</td>
<td>

\-

</td>
</tr>
<tr style="background:#101010" align=center>
<td>
</td>
<td>
</td>
<td>

Inferno Sweep

</td>
<td>

8.4

</td>
<td>

\-

</td>
<td>

\-

</td>
<td>

\-

</td>
<td>

\-

</td>
</tr>
<tr style="background:#262626" align=center>
<td>

Rocket Launcher

</td>
<td>

HE Rocket

</td>
<td>

Aimed Shot

</td>
<td>

\-

</td>
<td>

\-

</td>
<td>

\-

</td>
<td>

\-

</td>
<td>

\-

</td>
</tr>
<tr style="background:#262626" align=center>
<td>
</td>
<td>

IC Rocket

</td>
<td>
</td>
<td>

\-

</td>
<td>

\-

</td>
<td>

\-

</td>
<td>

\-

</td>
<td>

\-

</td>
</tr>
<tr style="background:#101010" align=center>
<td>

Grenade Launcher

</td>
<td>

25mm Flechette Grenades

</td>
<td>

Single Shot

</td>
<td>

10.8

</td>
<td>

\-

</td>
<td>

\-

</td>
<td>

\-

</td>
<td>

\-

</td>
</tr>
<tr style="background:#101010" align=center>
<td>
</td>
<td>
</td>
<td>

3-Round Burst

</td>
<td>

14.2

</td>
<td>

\-

</td>
<td>

\-

</td>
<td>

\-

</td>
<td>

\-

</td>
</tr>
<tr style="background:#262626" align=center>
<td>

Bolter Rifle

</td>
<td>

Bolter Rifle Magazine

</td>
<td>

Snap Shot

</td>
<td>

8.6

</td>
<td>

7.5

</td>
<td>

4.4

</td>
<td>

1.6

</td>
<td>

0.4

</td>
</tr>
<tr style="background:#262626" align=center>
<td>
</td>
<td>
</td>
<td>

Cannonade

</td>
<td>

14.2

</td>
<td>

11.5

</td>
<td>

6.0

</td>
<td>

2.0

</td>
<td>

0.5

</td>
</tr>
<tr style="background:#262626" align=center>
<td>
</td>
<td>
</td>
<td>

Precision Shot

</td>
<td>

5.8

</td>
<td>

5.8

</td>
<td>

5.1

</td>
<td>

3.1

</td>
<td>

1.1

</td>
</tr>
<tr style="background:#101010" align=center>
<td>

Laser Pistol

</td>
<td>

D-F Cartridge

</td>
<td>

Wave Fire

</td>
<td>

7.9

</td>
<td>

7.9

</td>
<td>

7.1

</td>
<td>

\-

</td>
<td>

\-

</td>
</tr>
<tr style="background:#101010" align=center>
<td>
</td>
<td>
</td>
<td>

Pulsed Fire

</td>
<td>

9.6

</td>
<td>

9.6

</td>
<td>

8.7

</td>
<td>

\-

</td>
<td>

\-

</td>
</tr>
<tr style="background:#262626" align=center>
<td>

Laser Rifle

</td>
<td>

D-F Cartridge

</td>
<td>

Wave Fire

</td>
<td>

7.1

</td>
<td>

7.1

</td>
<td>

6.7

</td>
<td>

4.6

</td>
<td>

\-

</td>
</tr>
<tr style="background:#262626" align=center>
<td>
</td>
<td>
</td>
<td>

Pulsed Fire

</td>
<td>

7.9

</td>
<td>

7.9

</td>
<td>

7.4

</td>
<td>

5.1

</td>
<td>

\-

</td>
</tr>
<tr style="background:#101010" align=center>
<td>

Heavy Laser

</td>
<td>

D-F Cartridge

</td>
<td>

Wave Fire

</td>
<td>

5.2

</td>
<td>

5.2

</td>
<td>

4.8

</td>
<td>

3.1

</td>
<td>

\-

</td>
</tr>
<tr style="background:#101010" align=center>
<td>
</td>
<td>
</td>
<td>

Pulsed Fire

</td>
<td>

5.8

</td>
<td>

5.8

</td>
<td>

5.3

</td>
<td>

3.5

</td>
<td>

\-

</td>
</tr>
<tr style="background:#262626" align=center>
<td>

Particle Beam Pistol

</td>
<td>

Pistol Particle Accelerator

</td>
<td>

Snap Shot

</td>
<td>

7.6

</td>
<td>

7.3

</td>
<td>

\-

</td>
<td>

\-

</td>
<td>

\-

</td>
</tr>
<tr style="background:#262626" align=center>
<td>
</td>
<td>
</td>
<td>

Rapid Shots

</td>
<td>

13.1

</td>
<td>

10.6

</td>
<td>

\-

</td>
<td>

\-

</td>
<td>

\-

</td>
</tr>
<tr style="background:#101010" align=center>
<td>

Particle Beam Rifle

</td>
<td>

Rifle Particle Accelerator

</td>
<td>

Snap Shot

</td>
<td>

8.1

</td>
<td>

7.6

</td>
<td>

5.2

</td>
<td>

2.2

</td>
<td>

0.6

</td>
</tr>
<tr style="background:#101010" align=center>
<td>
</td>
<td>
</td>
<td>

Aimed Shot

</td>
<td>

5.6

</td>
<td>

5.5

</td>
<td>

4.4

</td>
<td>

2.3

</td>
<td>

0.8

</td>
</tr>
<tr style="background:#101010" align=center>
<td>
</td>
<td>
</td>
<td>

Repeat Fire

</td>
<td>

13.8

</td>
<td>

12.1

</td>
<td>

7.1

</td>
<td>

2.6

</td>
<td>

\-

</td>
</tr>
<tr style="background:#262626" align=center>
<td>

Particle Beam Cannon

</td>
<td>

Cannon Particle Accelerator

</td>
<td>

Snap Shot

</td>
<td>

7.9

</td>
<td>

7.5

</td>
<td>

5.2

</td>
<td>

\-

</td>
<td>

\-

</td>
</tr>
<tr style="background:#262626" align=center>
<td>
</td>
<td>
</td>
<td>

Rapid Shots

</td>
<td>

18.7

</td>
<td>

16.2

</td>
<td>

9.4

</td>
<td>

\-

</td>
<td>

\-

</td>
</tr>
<tr style="background:#262626" align=center>
<td>
</td>
<td>
</td>
<td>

Unrestricted Blast

</td>
<td>

\-

</td>
<td>

\-

</td>
<td>

\-

</td>
<td>

\-

</td>
<td>

\-

</td>
</tr>
<tr style="background:#101010" align=center>
<td>

Plasma Pistol

</td>
<td>

Plasma Pistol Charger

</td>
<td>

Snap Shot

</td>
<td>

6.0

</td>
<td>

\-

</td>
<td>

\-

</td>
<td>

\-

</td>
<td>

\-

</td>
</tr>
<tr style="background:#101010" align=center>
<td>
</td>
<td>
</td>
<td>

Burst

</td>
<td>

9.3

</td>
<td>

\-

</td>
<td>

\-

</td>
<td>

\-

</td>
<td>

\-

</td>
</tr>
<tr style="background:#262626" align=center>
<td>

Plasma Rifle

</td>
<td>

Plasma Rifle Charger

</td>
<td>

Snap Shot

</td>
<td>

5.1

</td>
<td>

4.7

</td>
<td>

\-

</td>
<td>

\-

</td>
<td>

\-

</td>
</tr>
<tr style="background:#262626" align=center>
<td>
</td>
<td>
</td>
<td>

Aimed Shot

</td>
<td>

3.4

</td>
<td>

3.3

</td>
<td>

\-

</td>
<td>

\-

</td>
<td>

\-

</td>
</tr>
<tr style="background:#262626" align=center>
<td>
</td>
<td>
</td>
<td>

Burst

</td>
<td>

7.8

</td>
<td>

7.2

</td>
<td>

\-

</td>
<td>

\-

</td>
<td>

\-

</td>
</tr>
<tr style="background:#101010" align=center>
<td>

Plasma Blaster

</td>
<td>

Plasma Blaster Charge

</td>
<td>

Snap Shot

</td>
<td>

6.0

</td>
<td>

5.4

</td>
<td>

3.4

</td>
<td>

\-

</td>
<td>

\-

</td>
</tr>
<tr style="background:#101010" align=center>
<td>
</td>
<td>
</td>
<td>

Ball

</td>
<td>

\-

</td>
<td>

\-

</td>
<td>

\-

</td>
<td>

\-

</td>
<td>

\-

</td>
</tr>
<tr style="background:#101010" align=center>
<td>
</td>
<td>
</td>
<td>

Burst

</td>
<td>

15.3

</td>
<td>

12.4

</td>
<td>

\-

</td>
<td>

\-

</td>
<td>

\-

</td>
</tr>
</table>