## Actor generation

This is describing a scripting structure that governs the random
generation of all actors in the game, from PHALANX soldiers to aliens to
civilians to workers.

The general idea is to define an actor "class", with each class
containing the parameters the game uses to generate actors that belong
to that class. This allows for specialist recruits, i.e. actors who are
good in a single field and mediocre in all the others, as well as
allround recruits. It also allows to tweak actor generation rather
precisely.

The definitions are used when a character is generated. For soldiers and
employees this means when they show up in the hire screen. For civilians
and aliens this means at the start of a mission. Information about what
classes to be used for the aliens should be provided by the campaign
framework (this also means aliens can grow stronger as the campaign
progresses, as the framework will gradually call higher classes).

Here is an example of how the definitions look.

    chrtemplate soldier_common {
        rate    74
        strength    "15 25"
        speed   "15 25"
        accuracy    "20 30"
        mind    "20 35"
        close   "15 25"
        heavy   "15 25"
        assault "15 25"
        sniper  "15 25"
        explosive   "15 25"
        health  "80 110"
    }

    chrtemplate soldier_close {
        rate    5
        strength    "15 25"
        speed   "15 25"
        accuracy    "20 30"
        mind    "20 35"
        close   "25 40"
        heavy   "13 23"
        assault "13 23"
        sniper  "13 23"
        explosive   "13 23"
        health  "80 110"
    }

    chrtemplate soldier_heavy {
        rate    5
        strength    "15 25"
        speed   "15 25"
        accuracy    "2 30"
        mind    "20 35"
        close   "13 23"
        heavy   "25 40"
        assault "13 23"
        sniper  "13 23"
        explosive   "13 23"
        health  "80 110"
    }