## General

Place a [misc_mission](Mapping/Entities/misc_mission "wikilink")
[entity](Mapping/Entities "wikilink") at the bomb spot and set the item
property to the item that must be placed there (this can also be used to
deliver something). This item id comes from the ufo script files and
must be a valid item-definition id. (use e.g. the existing bomb types,
**bomb1** or **bomb2**.

Setting the time of the
[misc_mission](Mapping/Entities/misc_mission "wikilink") entity defines
the amount of rounds the item will wait for the explosion. Once this
time is due the mission target is won, if no other mission is in the
map, the map is won for the team that had to place the item.

If you need an item, you should be aware that it's not enough for
skirmish or multiplayer to have this item in a campaign-only game. You
should either be aware that you are building a campaign-only-map or
place the item somewhere into the map by placing a
[misc_item](Mapping/Entities/misc_item "wikilink") entity.

[Category:Mapping](Category:Mapping "wikilink")
[Category:GameTypes](Category:GameTypes "wikilink")