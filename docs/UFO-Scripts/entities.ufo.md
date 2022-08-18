defines keys and values for use in map files. It is used by
[UFORadiant](UFORadiant "wikilink") and ufo2map. The basic layout of an
entity is like this.

    entity entity_name {
        key1    "value1"
        key2    "value2"

        mandatory {
            key3    "description3"
        }

        optional {
            key4    "description4"
        }

        default {
            key5    "defualt5"
        }

        type {
            key6    V_type6
        }
    }

- keys not in a sub-block (key1, key2) are used in UFORadiant
  exclusively
- entities are not valid without mandatory keys (and will be deleted by
  ufo2map -fix unless a defualt is available)
- optional keys, are erm, optional
- key5 should be a repeat of key3 or key4, and a default value provided.
- key6 must be a repeat of key1-4 (though the blocks may be in any
  order)
- if no type is given, the default in V_STRING

### types

an example showing all the features of types. 3 and 6 are the number of
elements in the vectors.

    type {
        key1    "V_FLOAT"
        key2    "V_INT"
        key3    "V_INT 3"
        key4    "V_FLOAT 6"
        key5    "V_STRING"
    }

[Category:UFO-Scripts](Category:UFO-Scripts "wikilink")
[Category:Contribute](Category:Contribute "wikilink")