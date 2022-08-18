suggestion for type definition in entities.ufo

    entity misc_model {
        description "Displays a model. Set the level flags correctly! Use angles [pitch yaw roll] to rotate the model. pitch (up/down [-90 up to 90]), yaw (left/right [0 up to 360]) and roll (fall over)"
        color       "1 1 0"
        size        "-16 -16 -16 16 16 16"
        flags       "level1 level2 level3 level4 level5 level6 level7 level8 server_solid pulse"

        mandatory {
            model       "Arbitrary model file to display"
        }

        optional {
            angles      "Direction of the model [pitch yaw roll]"
            angle       "Direction of the model [yaw]"
            modelscale_vec  "Scale of the model (vector of 3 values)"
            skin        "Skin number"
            frame       "Frame number - use frame or anim - but not both"
            anim        "If this is this an animated model you can set the animation name from the *.anm file here"
        }

        default {
            skin        "0"
            frame       "0"
            modelscale_vec  "1.0 1.0 1.0"
        }

        type {
            color   V_VEC
            size    V_VEC6
            angles  V_VEC
            anim    V_STRING
        }

    }