## General

Particles are used for weapon and map effects. The particle engine is
fully scriptable and already has some nice looking particles. To create
new particles you should read throught the datatypes part.

They are small, short lived entities which are controlled by a script.
UFO:AI uses particles to depict bullets, rockets, explosions, smoke,
laser beams, and so on. Some effects are a combination of several
particles – in fact a particle can spawn more particles.

Particle are local entities, like actors and aliens. Like other entities
the particle has an origin, a think function, etc.

### Units of Measurement

#### Time

- The **Quake 2 engine** measures time in **milliseconds**. For
  instance, the **`cl.time`** variable is defined as **`int time`** in
  the `client_state_t` struct, which means that its size varies
  depending on the size of an int on the local system.
  Specifically, if the local system defines integers as 16 bits, then
  **`cl.time`** has a maximum value of 32767, which means it overflows
  after about 33 seconds.
  The gnu-linux-386 architecture defines 32 bit integers, which means
  the **`cl.time`** value is good for about 24 days.
  We shall assume 32 bit integers and therefore a non-overflowing
  **`cl.time`** value.
- The **UFO:AI particle system** measures time in **seconds**. Time
  values are stored in **float** type variables. Basically, the particle
  functions multiply the quake2 time by a scaling factor of 0.001.

#### Distance

Distance is measured in **texels** (See also at Wikipedia.).
A typical male actor is 56 texels tall and 24 texels wide. If the height
of an average white man is about 180 cm then a texel is about 3.2 cm, or
5/4 inches.

A UFO:AI *cell* is 32x32x72 texels which is about 1x1x2.3 meters.

### Particle Definitions

Every particle in the UFO:AI game is an instantiation of a particle
definition. Particle definitions are declared by scripts in the
directory. A particle definition consists of three functions: a
mandatory init function and optional think and run functions. Each
function contains commands. A command may or may not have a reference
(ie an argument). Here is an example of a particle definition (taken
from ).

    // ==================
    // flamethrower
    // ==================

    particle fireBall
    {
      init
      {
        image  sfx/fireball
        blend  add
        style  facing
        tps    2.5
      }
      run
      {
        push   pos "80 80"
        mul    *t
        add    pos "10 10"
        pop    *size
      }
      think { tfade  out }
    }

## The Language

### Particle References

A command may include a target of the operation. This is called the
**reference**. The reference may take several forms: a constant, a
stack, or a variable. If the reference is a constant and the command
accepts more than one type of reference, then the constant will be
preceded by a string specifying the type (float, pos, vector, or color).
The octalthorpe (#) reference means that the command operates on the top
element on the stack. Variables are more complicated ...

### Particle Variables

UFO:AI defines twenty-two variables. Each variable has a specific type.
Each variable corresponds to a property of the particle (ie a value in
its local entity or particle type structure). Most commands can take a
variable as an argument. When used as an argument, variables are
prefixed with an asterisk “\*”. For instance `pop *v` moves a value from
the stack to variable **v**.

### Datatypes

- **image**: [V_STRING](V_STRING "wikilink") path to model - relative
  from *base/pics*. This is mostly used for particles which do not have
  models, ie impact particles. Supported are all image types the engine
  supports (see [Artwork](Artwork "wikilink")).
- **model**: [V_STRING](V_STRING "wikilink") path to model - relative
  from *base/models*. Models are only rendered if the particle is an
  entity, which only happens for projectiles. Supported are all model
  types the engine supports (see [Modelling](Modelling "wikilink")).
- **skin**: [V_INT](V_INT "wikilink") skin number that should be use for
  the *model*
- **blend**: [V_STRING](V_STRING "wikilink") The blending function for
  the particle image.
  - **replace**
  - **blend**
  - **one**
  - **add**
  - **filter**
  - **invfilter**
- **style**: [V_STRING](V_STRING "wikilink") Defines the basic
  type&shape of the particle.
  - **facing** The particle will always face the camera/viewer.
  - **rotated** Fixed rotation in the world (given by angles)
  - **beam** (Guess: The particle will be stretched from a first
    point (s) to a second one \[defined by velocity (v)?\])
  - **line** Will draw a line from a first point defined by *s* to a
    second one defined by velocity *v*
  - **axis**
  - **circle** Internal style - don't use this
- **thinkfade**: [V_STRING](V_STRING "wikilink") think fade
  - **none** Default - tps value does not change over time.
  - **in** (Guess: Increase the tps value linearly over time \[starting
    with 0\])
  - **out** Decrease the tps value linearly over time \[starting with
    the original tps value and reducing to 0\]
  - **sin** Alter the tps value over time in a sinus function \[between
    the 0 and tps value\]
  - **saw** (Guess: Alter the tps value over time linearly \[between the
    0 and tps value\].)
  - **blend**
- **scroll_s**: [V_FLOAT](V_FLOAT "wikilink") Scrolls texture
  coordinates in S direction
- **scroll_t**: [V_FLOAT](V_FLOAT "wikilink") Scrolls texture
  coordinates in T direction
- **framefade**: [V_STRING](V_STRING "wikilink") frame fade


**none**, **in**, **out**, **sin**, **saw**, **blend**

- **size**: [V_POS](V_POS "wikilink") typically **size\[0\]** is the
  length of the weapon in the direction in which it is fired.


Some particle represent beams from beams weapons – these beams are
considered to travel infinitely fast ie they are instantaneous. For
these instantaneous particles, the size is equal to the distance between
the origin and the target.

- **scale**: [V_VECTOR](V_VECTOR "wikilink") scaling in x, y and z
  direction
- **color**: [V_COLOR](V_COLOR "wikilink") color vector of RGBA
- **a**: [V_VECTOR](V_VECTOR "wikilink") acceleration vector
- **v**: [V_VECTOR](V_VECTOR "wikilink") velocity vector
- **s**: [V_VECTOR](V_VECTOR "wikilink") location vector
- **angles**: [V_VECTOR](V_VECTOR "wikilink") \<pitch, yaw, roll\>.
  Typically this is used for projectiles; it points from the muzzle
  coordinate towards the impact coordinate.


(see omega, below)

- **omega**: [V_VECTOR](V_VECTOR "wikilink") the rotation vector for the
  particle


(newAngles = oldAngles + frametime \* omega)

- **life**: [V_FLOAT](V_FLOAT "wikilink") specifies how long a particle
  will be active (seconds)
- **rounds**: [V_INT](V_INT "wikilink") specifies how many rounds a
  particle will be active
- **tps**: [V_FLOAT](V_FLOAT "wikilink") think per second - call the
  think function tps times each second, the first call at 1/tps seconds
- **lastthink**: [V_FLOAT](V_FLOAT "wikilink")
- **frame**: [V_INT](V_INT "wikilink") see endframe
- **endframe**: [V_INT](V_INT "wikilink") frame and endframe specifies
  the frame count for an animated particle

`init`
`{`
` [..]`
` frame 1`
` endframe 10`
` image +sfx/uexp_`
` [..]`
`}`

This example will use the images  - for the particles in the correct
order to simulate something like an explosion.

- **fps**: [V_FLOAT](V_FLOAT "wikilink") how many frames per second
  (animate)
- **levelflags**: [V_INT](V_INT "wikilink") display this particle only
  in specific [levels](Mapping/Levelflags "wikilink")
- **lastframe**: [V_FLOAT](V_FLOAT "wikilink") time (in seconds) when
  the think function was last executed (perhaps this can be used to
  delay or speed up particle actions).
- **dt**: [V_FLOAT](V_FLOAT "wikilink") time increment for rendering
  this particle (delta time)
- **t**: [V_FLOAT](V_FLOAT "wikilink") time that the particle has been
  active already
- **offset**: [V_VECTOR](V_VECTOR "wikilink") determines whether the
  particles image is 'shifted' along the long and lat of the particle.
  The x coord specifies shift perpendicular to the direction the
  particle moves and the y coord specifies shift parallel to the
  direction of motion.
- **light**: [V_INT](V_INT "wikilink") specifies light intensity of
  dlight (dynamic light) (see also the color vector to define the light
  color)
- **physics**: [V_BOOL](V_BOOL "wikilink") don't let the particles go
  through a wall
  - **stick**: [V_BOOL](V_BOOL "wikilink") this will make the particle
    stick to the brush that was hit
  - **bounce**: [V_BOOL](V_BOOL "wikilink") this will make the particle
    bounce away from the brush it hit
  - **stayalive**: [V_BOOL](V_BOOL "wikilink") only works in combination
    with **physics** - let the particles die 'naturally' when they hit
    something solid
- **autohide**: [V_BOOL](V_BOOL "wikilink") autohide the particle if the
  current position is higher than the current selected worldlevel
  (useful for weather particles)

### Stack functions and particle commands

In the init and run functions each command is written on a separate
line, but that is not required. In fact, the whole script could be
written without any line feeds or carriage returns. Line feeds/carriage
returns are not required – but whitespace must appear around every
token. Brace brackets, function names, commands and arguments are
tokens. The fireBall particle only uses nine commands. In fact, there
are nineteen particle commands. Commands have an argument data type in
the same way that variables have a data type. Commands may be given a
reference as an argument. The type of the argument (e.g. a reference)
and the command must be the same. Here is a list of all the particle
commands, with data types of their arguments and descriptions.

- **end** ([V_NULL](V_NULL "wikilink"))


Marks the end of a function. Takes no arguments. This command is not
usually seen in script code --– it is automatically added to the end of
the function by the parser

- **push** (any type)


Put reference on the stack. The reference may be of any type

- **pop** (any type)


Pop value from the stack to the indicated variable

- **kpop** (any type)


Pop value from the stack to the indicated variable, push the value back
to the stack

- **add** ([V_FLOAT](V_FLOAT "wikilink"), [V_POS](V_POS "wikilink"),
  [V_VECTOR](V_VECTOR "wikilink") or [V_COLOR](V_COLOR "wikilink"))


Pop value from the stack, add it to reference value, push the sum to the
stack

- **sub** ([V_FLOAT](V_FLOAT "wikilink"), [V_POS](V_POS "wikilink"),
  [V_VECTOR](V_VECTOR "wikilink") or [V_COLOR](V_COLOR "wikilink"))


Pop value from the stack, subtract reference, push the result to the
stack

- **mul** ([V_FLOAT](V_FLOAT "wikilink"), [V_POS](V_POS "wikilink"),
  [V_VECTOR](V_VECTOR "wikilink") or [V_COLOR](V_COLOR "wikilink"))


Pop value from the stack, multiply it by reference, push the result to
the stack

- **div** ([V_FLOAT](V_FLOAT "wikilink"), [V_POS](V_POS "wikilink"),
  [V_VECTOR](V_VECTOR "wikilink") or [V_COLOR](V_COLOR "wikilink"))


Pop value from the stack, divide it by reference, push the result to the
stack

- **sin** ([V_FLOAT](V_FLOAT "wikilink"))


Calculate sine of reference, push result to the stack

- **cos** ([V_FLOAT](V_FLOAT "wikilink"))


Calculate cosine of reference, push result to the stack

- **tan** ([V_FLOAT](V_FLOAT "wikilink"))


Calculate tangent of reference, push result to the stack

- **rand** ([V_FLOAT](V_FLOAT "wikilink"), [V_POS](V_POS "wikilink"),
  [V_VECTOR](V_VECTOR "wikilink") or [V_COLOR](V_COLOR "wikilink"))


Push a random value between 0 and the argument onto the stack. Cannot
produce [V_INT](V_INT "wikilink") values to, e.g., spawn a random number
of particles

Multiplies each entry of the given parameter from stack with a random
value from 0 to 1

newvalue(s) = \[parameter_1\*(0...1), parameter_2\*(0...1), etc...\]

See also `frand()` in and `PC_RAND` in cl_particle.c:CL_ParticleFunction

- **crand** ([V_FLOAT](V_FLOAT "wikilink"), [V_POS](V_POS "wikilink"),
  [V_VECTOR](V_VECTOR "wikilink") or [V_COLOR](V_COLOR "wikilink"))


Push a random value between -argument and +argument onto the stack

Multiplies each entry of the given parameter from stack with a random
value from -1 to 1

newvalue(s) = \[parameter_1\*(-1...1), parameter_2\*(-1...1), etc...\]

See also `cfrand()` in and `PC_CRAND` in
cl_particle.c:CL_ParticleFunction

- **v2** ([V_NULL](V_NULL "wikilink"))


Pop the last two values from the stack, use these values to create a pos
type value, and push the pos value onto the stack. Takes no arguments

- **v3** ([V_NULL](V_NULL "wikilink"))


Pop the last three values from the stack, use these values to create a
vector type value, and push this vector value onto the stack

- **v4** ([V_NULL](V_NULL "wikilink"))


Pop the last four values from the stack, use these values to create a
color type value, and push this color value onto the stack

- **kill** ([V_NULL](V_NULL "wikilink"))


set inuse flag to false (deacticate the particle)

- **spawn** ([V_STRING](V_STRING "wikilink"))


Instantiates a new particle. The argument must be a defined particle
name. The spawned particle inherits the parent's s, v and a values

- **nspawn** ([V_STRING](V_STRING "wikilink"))


Instantiates one or more new particles. The argument must be a defined
particle name. The number of particles to create is taken from the
stack. The spawned particles inherit the parent's s, v and a values

- **child** ([V_STRING](V_STRING "wikilink"))


child particles are always rendered relative to their parents. Combined
with the use of offset (see above) this allows complex particles to be
made that behave as single entities.

### Basic Datatypes

- If you are a coder you should already know float
  ([V_FLOAT](V_FLOAT "wikilink")), integer ([V_INT](V_INT "wikilink"))
  and string ([V_STRING](V_STRING "wikilink")) types.
- A position type ([V_POS](V_POS "wikilink")) is a set of two positive
  integers.
- A vector type ([V_VECTOR](V_VECTOR "wikilink")) is a set of three
  floats.
- A color type ([V_COLOR](V_COLOR "wikilink")) is a set of four floats,
  each float having a value between 0 and 1 inclusive (normalized red
  green blue and alpha channels).
- style, fade and blend have specific allowed values (actually strings)
  defined in as shown below:
  - **blend**

    `glTexEnvf( GL_TEXTURE_ENV, GL_TEXTURE_ENV_MODE, GL_MODULATE )`

    `glBlendFunc( GL_SRC_ALPHA, GL_ONE_MINUS_SRC_ALPHA )`
  - **replace**

    `glTexEnvf( GL_TEXTURE_ENV, GL_TEXTURE_ENV_MODE, GL_REPLACE )`
  - **add**

    `glTexEnvf( GL_TEXTURE_ENV, GL_TEXTURE_ENV_MODE, GL_MODULATE )`

    `glBlendFunc( GL_ONE, GL_ONE )`
  - **filter**

    `glTexEnvf( GL_TEXTURE_ENV, GL_TEXTURE_ENV_MODE, GL_MODULATE )`

    `glBlendFunc( GL_ZERO, GL_SRC_COLOR )`
  - **invfilter**

    `glTexEnvf( GL_TEXTURE_ENV, GL_TEXTURE_ENV_MODE, GL_MODULATE )`

    `glBlendFunc( GL_ZERO, GL_ONE_MINUS_SRC_COLOR )`

### Assignment Command

The assignment command is simply the name of the variable followed by
the value. In the **fireBall** example **image ** assigns the string
value **sfx/fireball** to the **image** variable. Note that strings to
not require quotation marks. Also, remember that the data types of
variable and its value must match.

### Vector Components

It is possible to specify the individual components of a vector or
color. This is done by adding a suffix to the argument. The suffix
consists of a period “.” followed by the index of the desired component.
For instance, in the particle laserPulse definition:

    push float 2.2
    pop *size.2

Moves the value **2.2** to **size\[1\]**.

## Projectile Particles

Weapons fire projectiles: beams, bullets, rockets, etc. When a weapons
fires, the `LE_AddProjectile` function creates an entity, sets the `s`
variable to the location of the muzzle of the gun and spawns particles
representing the projectiles. The init function runs as soon as the
particle spawns. The `le->ptl` element points to the particle, so
projectiles are both entities and particles.

Next, the `LE_AddProjectile` function sets the particle's angle
attribute to point toward the target. As far as I can tell, this does
two things: it rotates the particle image so that the particle (eg a
beam) is pointed the right way, and similarly for finite speed particle
models. AFAIK the angles element has nothing to do with motion because
that is accomplished using `le->mins` and/or the `v` and `a` variables.

### Infinite speed projectiles

If the speed of a projectile is set to zero, then it is an infinite
speed projectile: eg laser beam, bullet, SMG. In this case,
`LE_AddProjectile` sets the length of the projectile (`size[0]`) to the
distance between the muzzle and the target and sets the `s` variable to
the midpoint between the muzzle and the target. If the weapons has
impact effects, then `LE_AddProjectile` spawns the impact particles.
Then `LE_AddProjectile` returns. `LE_AddProjectile` does not kill the
particle – all infinite speed projectiles contain a kill command in the
think function, so the particle will disappear when the particle entity
performs its first think routine (**don't forget to put such a kill
command in your definition!**). The lifetime of such a particle can be
controlled in the init function by manipulating the `tps` and
`lastthink` variables.

### Finite speed projectiles

If the speed of a projectile is not zero, then it is a finite speed
projectile: a rocket, napalm (from the
[flamethrower](Equipment/Primary_Weapons/Flamethrower "wikilink")), or
tachyon burst. These projectiles fly from target to impact.
`LE_AddProjectile` does the following:

- sets the s variable to the muzzle coordinate
- spawns the particle (which also runs the particle's init function)
- sets the particle's angles to point towards the impact coordinate
- sets the `le->maxs` coordinate to the impact location
- converts the speed to a velocity vector pointing in the direction of
  the target, and stores this vector in le-\>mins
- offsets the particle's origin (`le->origin`) slightly towards the
  target, half the length (`size[0]`) away from the muzzle
- sets the particle entity's endtime (`le->endtime`) to be equal to the
  time required for the projectile to travel to the impact coordinate
- if the fire definition includes an impact, then set some references
  for the impact definition
- set and execute the particle's think function

The `LET_Projectile` function implements motion for finite speed
projectiles. Remember that the velocity of a projectile is stored in the
`le->mins` vector. Each time the local entity does a think function
`LET_Projectile` which moves the projectile allow the mins vector
towards its target. For this reason, the particle definitions for finite
speed projectiles never use the `v` or `a` variables. They also do not
need the **kill** command.

## Impact Particles

Impact particles are a little different from projectile particles – most
importantly, impact particles are not entities. Since they are not
entities, they do not receive an entity think function. Instead, once
per frame the `CL_Frame` function calls the `CL_ParticleRun` function.
For each active particle `CL_ParticleRun`:

- advances the time
- updates the location of the particle using the (`s, v, a` and `dt`
  particle variables)
- executes the particles' run function
- if it is the right time, executes the particle's think function
- if it is the right time, shows a frame of the particle's animation
- fades the particle (if fading is enabled)

If you want an impact particle to move then you must set the `v` or `a`
variables in its particle definition. **Don't forget to kill an impact
particle with an explicit kill command, either in the think section or
elsewhere!**

## Links

- [UFO-Scripts](UFO-Scripts "wikilink")
- [Datatypes](UFO-Scripts/Datatypes "wikilink")
- [Mapping](Mapping "wikilink")

1.  [misc_particle](misc_particle "wikilink")
2.  [Levelflags](Mapping/Levelflags "wikilink")

[Category:UFO-Scripts](Category:UFO-Scripts "wikilink")
[Category:Mapping](Category:Mapping "wikilink")
[Category:Contribute](Category:Contribute "wikilink")