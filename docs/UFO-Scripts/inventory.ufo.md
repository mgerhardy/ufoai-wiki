## General

- **out** [V_INT](V_INT "wikilink")


time units for moving something out

- **in** [V_INT](V_INT "wikilink")


time units for moving something in

- **shape** [V_SHAPE_BIG](V_SHAPE_BIG "wikilink")


this value defines a grid given by the upper left corner and dimensions

values: column1, row1, column2, row2

column1 is starting column of grid(0 based)

row1 is starting row of grid(0 based)

column2 is number of columns to display(ie. number of squares left to
right)

row2 is number of rows to display(ie. number of squares top to bottom)

a container can have several shapes that are added to the final
container form

\- a primary example of a container with several shapes and which shows
the use of the column1 and row1 values is the belt(see below)

- **single** [V_BOOL](V_BOOL "wikilink")


only a single item

- **armor** [V_BOOL](V_BOOL "wikilink")


this is the armor container

- **all** [V_BOOL](V_BOOL "wikilink")


allow everything to be stored in this container (e.g armor and weapons)

- **temp** [V_BOOL](V_BOOL "wikilink")


a temporary container - such a container is not cleared - it's just a
pointer to another one

make sure that the temporary containers are the last ones

- **headgear** [V_BOOL](V_BOOL "wikilink")


headgear slot - only useable for headgear

- **extension** [V_BOOL](V_BOOL "wikilink")


the extension slot - only weapon or item extension can be places here

## Example

    inventory belt
    {
        shape   "0 0 3 1"  //create grid at starting point 3 squares wide by 1 square high
        shape   "0 1 1 1"  //create grid 1 row down for 1 square wide by 1 square high
        in      2  //costs 2 tus to put in
        out     1  //costs 1 tu to take out
    }

    inventory holster
    {
        shape   "0 0 3 2"  //create grid at starting point 3 squares wide by 2 squares high
        in      2  //costs 2 tus to put in
        out     1  //costs 1 tu to take out
    }

    inventory armor
    {
        shape   "0 0 5 6"  //create grid at starting point 5 squares wide by 6 squares high
        single  true
        armor   true
        in      200
        out     200
    }

    // Make sure that the temp containers are the last ones

    // Base equipment place
    inventory equip
    {
        shape   "0 0 24 13"  //create grid at starting point 24 squares wide by 13 squares high
        shape   "0 13 20 2"  //create grid 13 rows down 20 squares wide by 2 squares high
        temp    true         //set as temporary container
        all     true //allow for storing armour and equipment
        scroll  true
    }

## Links

- [UFO-Scripts](UFO-Scripts "wikilink")

[Category:UFO-Scripts](Category:UFO-Scripts "wikilink")
[Category:Contribute](Category:Contribute "wikilink")