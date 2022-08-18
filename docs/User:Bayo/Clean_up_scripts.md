Idea is to clean up some part of the script. As a result, we can use an
only one grammar for all our main scripts (ATM we only use the same
tokenizer). It also can help later to convert script to XML if we decide
to.

## Problem with lists

Some part of the script use list inside blocks. It makes problems if we
considere blocks a set of name-value (cause most of our script consider
that).

For examples team_humans.ufo, music.ufo... and many more

        names {
            female {
                Aakriti
                Abeba
                Adina
                Afra
                Afua
            }
        }

We can introduce a new keyword for lists. For example:

        names {
            female [
                "Aakriti"
                "Abeba"
                "Adina"
                "Afra"
                "Afua"
            ]
        }

Or still use the "default" way. For example:

        names {
            female {
                name "Aakriti"
                name "Abeba"
                name "Adina"
                name "Afra"
                name "Afua"
            }
        }

Or another way?

## Problem with element containing more than one value

Some part of the script a property is defined by a name and many values
in a list way.

research.ufo (request_OR alien), or components.ufo are good examples.

    components craft_ufo_scout {
        time    300
        item    alienmaterials          300 %
        item    antimatter              200 0
        item    craft_alien_propulsion  2   %
        item    craft_alien_astrogation 1   %
        item    craft_alien_detection   1   %
    }

We can rework it in a "default" way (BTW i dont introduce "random"
names, i dont know all this things mean):

    components craft_ufo_scout {
        time    300
        item {
            type alienmaterials
            value 300
            unit "%"
        }
        item    { type antimatter       amount  200 unit "0" }
        item    { type craft_alien_propulsion   amount 2    unit "%" }
        item    { type craft_alien_astrogation  amount 1    unit "%" }
        item    { type craft_alien_detection    amount 1    unit "%" }
    }

## Embedded languages

Some of our script embed sub languages. For example the particule system
contain a very special language, and the sequence script too. It is not
the same language and i dont think it is nice to parse it with the same
code.

Other languages like XML use escaping . *Battle for Wesnoth*, witch
embed Lua scripts inside there own script language use `<< ... >>`. We
should use a marker like that, to avoid our default parser to parse our
sub languages.

It can looks like something like that:

    particle explosionGrenExpl
    {
        init {<<
            push   int 18
            nspawn explosionSmoke

            push   int 18
            nspawn explosionSmoke2

            push   int 18
            nspawn explosionSmoke3
        >>}
    }

Or Python use that kind of syntax for multiline strings, it can works
too, and became usefull if we merge english .po file to our scripts:

    particle explosionGrenExpl
    {
        init """
            push   int 18
            nspawn explosionSmoke

            push   int 18
            nspawn explosionSmoke2

            push   int 18
            nspawn explosionSmoke3
        """
    }

BTW this way bellow can do the trick with Eclipse, and we dont need to
fix the game parser, then maybe it is the better idea for a fast fix
relative to Eclipse.

    particle explosionGrenExpl
    {
        init {//
            push   int 18
            nspawn explosionSmoke

            push   int 18
            nspawn explosionSmoke2

            push   int 18
            nspawn explosionSmoke3
        }//
    }

## V_RELABS

As a side comment. While we are reworking script, I think the way this
type is implemented is quite strange and dangerous. We should rework the
parsing code and the way we store the value in the game code.

And at least quote the values on scripts. Or we can introduce some units
(that's more something relative to Eclipse) the "%" as part of the
language.

BTW the `components` use something which looks like that too. Maybe we
can merge some code.

    components craft_ufo_scout {
        time    300
        item    alienmaterials          300 %
        item    antimatter              200 0

Maybe "300 %" means relative, and "200 0" means absolute. But i am not
sure about it.