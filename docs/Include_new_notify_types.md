This HowTo explains, how new notify types can be added to code to make
them configureable.

Message options allow you to configure, whether you want to receive
notification messages for each type, whether a notification sound should
be played (if associated) and whether game should stop on that event.
These settings are stored in game data, so you could change settings as
you wish depending on actual game advance.

## Step by Step

1.  add new enumeration values to `nt_strings` () and `notify_t` ()
    - do not include any whitespaces in `nt_strings` - these codes are
      used to store settings and have to be read by `MSG_ReadString` as
      one string
    - feel free to rearrange defined types to group them (in the
      definitions) - as long as order is same for both definitions
    - see [msgcategory
      definition](UFO-Scripts/msgcategories.ufo "wikilink") to see how
      types can be grouped for options
    - don't forget to surround `nt_strings` value with `N_()` to get
      them found for translation
2.  replace call of `MN_AddNewMessage` with `MSO_CheckAddNewMessage`
    with defined `notify_t` type
3.  check whether to add default settings for new category to
    - each line contains one "positive" setting - negative ones are not
      stored
4.  check whether to add newly defined type to either existing
    msgcategory or define a new one (in )

[Category:Contribute](Category:Contribute "wikilink")