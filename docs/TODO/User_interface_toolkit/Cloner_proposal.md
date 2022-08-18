A cloner is a panel containing nodes it can clone when we load a script.

|           |       |                                           |
|-----------|-------|-------------------------------------------|
| rows      | V_INT | Number of rows; number of clone generated |
| rowHeight | V_INT | Y position variation between two rows     |
|           |       |                                           |

Cloner properties

The cloner only clone the first level of child (one deep); and a child
is cloned if his name contain <num>.

    cloner foo {
        {
            ...
        }

        button button_<num> { ... }

        checkbox checkbox_<num> { ... }

        button dont_clone_me { ... }
    }

"num" is an abstractnode property. The cloner update some clone
properties. The "num" properties of a clone is updated using the number
of the clone (first clone is 0, second clone is 1...) Name of a clone is
updated with <num> substitution. Properties using cvar name with <num>
are also substitut. All over properties dont change anymore. Events are
shared by all clone from the same node, but with can use the runtime
substitution using <num>.

Node position of clones are also updated, according to the cloner
properties and the initial position of the cloned node.

    cloner foo {
        {
            rows
        }

        checkbox checkbox_<num> {   //< substitut at loadtime
            min *cvar foo<num>  //< substitut at loadtime
            current 1
            delta *cvar foo<num>    //< substitut at loadtime
            max 10
        }

        checkbox reset_<num> {  //< substitut at loadtime
            click {
                *path:parent.checkbox_<num> 0   //< substitut at runtime
            }
            num 10  //< no effect, cloner will update the value
        }
    }

## Example with messageoptions

This example will generate 12 x 3 checkbox into a panel, with the right
positions. The same change event action is shared by 12 checkbox, but
the <num> is used to generate the right command. This code should work
like the old one.

    menu messageoptions {

        ...

        cloner check {
            {
                pos         ...
                size        ...
                rows        12
                rowHeight   25
            }

            checkbox bt_pause<num> {
                tooltip     "_enable or disable game stopping"
                pos         "360 0"
                size        "20 18"
                image       "menu/checkbox_blue"
                current     0
                invis       true
                change      { cmd "msgoptions_toggle <num> pause;" }
            }

            checkbox bt_notify<num> {
                tooltip     "_enable or disable displaying a notification message"
                pos         "30 0"
                size        "20 18"
                image       "menu/checkbox_blue"
                current     0
                invis       true
                change      { cmd "msgoptions_toggle <num> notify;" }
            }

            checkbox bt_sound<num> {
                tooltip     "_enable or disable playing sound"
                pos         "60 0"
                size        "20 18"
                image       "menu/checkbox_blue"
                current     0
                invis       true
                change      { cmd "msgoptions_toggle <num> sound;" }
            }
        }

        ...

    }