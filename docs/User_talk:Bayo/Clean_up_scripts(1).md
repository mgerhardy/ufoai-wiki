## Comma-separation in lists

Just a thought. What about support for comma-separation in lists?
--[H-hour](User:H-hour "wikilink") 23:00, 29 May 2012 (SAST)

`   names {`
`       female Aakriti,Abeba,Adina,Afra,Afua`
`       male "Aakriti Abeba,Adina Afra,Afua"`
`   }`

Quotes required when a space exists within an item on the list? Or
always required is fine too.


This way is not really a list, but it can works too. But if you check
the script there is many more names, then i dont think it is very good
idea.

Quotes is IMO needed to identify values witch are not a reference.

BTW we also can write it like that:

`   names {`
`       female "Aakriti"`
`       female "Abeba"`
`       male "Aakriti"`
`       male "Abeba"`
`   }`


[Bayo](User:Bayo "wikilink") 13:54, 30 May 2012 (SAST)

I agree with the components example. It's a good thing to change this to
a more standard script syntax. I dislike the first approach to add a
"name" in front of each list entry: *a)* it would a lot of useless
content *b)* it's not always "name". But instead of using *\[* and *\]*
we should maybe do

`list names { ... }`

I have not yet a good idea about the embedded languages (particles)


--[Mattn](User:Mattn "wikilink") 12:27, 2 June 2012 (SAST)

The *list* token on the front can do job, but to me it is not the same
level of meaning. I can write some XML code to another page to show the
difference but here it will be ugly.

Then to write something as short as possible, here only the result
feeling. If you really want something with the "list" token, i think we
should put it after the property type.

    foo list { ... }
    // witch mean
    foo // i define foo
    list { // which is a list

    // BTW maybe you can more agree something like
    foo list( ... )


    // like
    foo // i define foo
    "bar" // which is a string

We can compare both

    fooo a {
        name  ""
        amount 30
        list types { ortnok taman spider }
    }

    // or

    fooo a {
        name ""
        amount 30
        types list { ortnok taman spider }
    }

But both looks a little strange, that why i think using another token
like *\[* (or what ever) is better... `list(` is not so bad too...
[Bayo](User:Bayo "wikilink") 15:09, 2 June 2012 (SAST)

## Changing mdl to model

some script entries like the techs have mdl, others have model - that
should be unified imo