![](Entities_settings.jpg "Entities_settings.jpg") Creates a
[particle](UFO-Scripts/ptl_*.ufo "wikilink") effect.

## Keys

- **particle**: name of the particle definition


Particle properties can be set here with a preceding '-' or '+'.

'-' property is set before calling the particle init function

'+' do it afterwards

- **wait**: wait time


Wait times are of the format "a b".

It spawns particles in random intervals ranging from (a) to (a+b)
seconds.

If no wait time is specified one particle is created at map start.

Don't forget to set the [levelflags](Mapping/Levelflags "wikilink") as
needed.

## Links

- [Entitylist](Mapping/Entities "wikilink")

[Category:Contribute](Category:Contribute "wikilink")
[Category:Mapping](Category:Mapping "wikilink")
[Category:Entity](Category:Entity "wikilink")