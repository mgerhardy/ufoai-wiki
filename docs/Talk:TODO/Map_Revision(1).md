## Getting Started

I propose that we do two things to get started. First, let's try and
brainstorm the various problems that we'd like to solve with this map
revision and form a list. Second, let's list all of our map themes and
maps, along with which problems need to be solved in each of these maps
and whether or not these maps should be rolled into another theme.

Eventually, I'd like to us to come up with a "target list" -- a list of
which map themes we want to consolidate into, which maps should stay
independent and static, etc, which we can turn into a TODO on the Page
(not Talk) section of this page.

## Map Problems

- **Exposed insertion**: The player is forced to throw smoke to provide
  cover right at the start of the mission and in some cases never
  reaches cover before killing all the aliens. This leads to repetitive
  missions even if the map is different.
  - I know this will be controversial, but I think the Raptor needs to
    be scrapped or redesigned. We need dropship tiles to be as small as
    possible (2x1, IMHO). Otherwise, the player spends half the battle
    fighting on the same tile. With +village2 I will simply not show the
    Raptor in the dropship tile because it would ruin everything about
    the RMA. I can work on an alternative, but I'm not a great modeller.
    --[H-Hour](User:H-Hour "wikilink")
    ([talk](User_talk:H-Hour "wikilink")) 16:33, 4 September 2013 (CEST)
    - I agree with the Raptor needing a redesign/replacement. But I am
      against using 2x1 tiles for the Dropships. This will result in
      actors beeing unable to walk around the dropship very often, not
      to speak of 2x2 units. --[ShipIt](User:ShipIt "wikilink")
      ([talk](User_talk:ShipIt "wikilink")) 17:58, 4 September 2013
      (CEST)
      - Hmm, I'm not sure that's true. In almost all cases, regular RMA
        tiles include at least a 1-grid perimeter that is walkable
        (partly to account for shadows), so adjacent tiles will almost
        always allow players to walk around the dropship. However, even
        the Firebird does not quite fit onto 2 tiles wide, creating a
        shadow cut-off effect. I thought about this some and decided to
        play around with the model scale. I was able to come up with the
        following scales which I think can fit the necessary spawn
        points, but also allow a 1 grid perimeter around the dropship --
        all on a 2x1 tile.
        [:<File:dropship_scale.jpg>](:File:dropship_scale.jpg "wikilink")
        What do you think about this? Obviously, not every tile has to
        be 2x1, and I suspect we'll maintain 3-4 shared dropship tiles
        at the end of the day (street version, no-street version, maybe
        an RMA can't easily accomodate a 2x1 tile, etc).
        --[H-Hour](User:H-Hour "wikilink")
        ([talk](User_talk:H-Hour "wikilink")) 00:28, 5 September 2013
        (CEST)
- **No cover in map**: There needs to be enough cover not just to hide
  behind, but also to be able to move from cover-to-cover in a single
  turn.
  - Of course, some places, like a Desert, make sense to be open. We
    just need to make these the exception rather than the rule.
    --[H-Hour](User:H-Hour "wikilink")
    ([talk](User_talk:H-Hour "wikilink")) 16:33, 4 September 2013 (CEST)
  - I vote for having a good mixture. There should be maps with lots of
    cover for close quarter combat (+oriental), maps with lots of open
    battlefield (+farm, +desert) and some in between. Without this, the
    maps will look different, but play the same.
    --[ShipIt](User:ShipIt "wikilink")
    ([talk](User_talk:ShipIt "wikilink")) 18:08, 4 September 2013 (CEST)
    - I agree, but I would like the balance to lean towards more
      tactical density. Even in a very dense map, like +oriental, all
      weapons have their uses (even snipers). However, very open maps
      have only one useful tactic (sniping). I think we probably agree
      on this, I just want to emphasise that both extremes (open +desert
      or super-tight bunker) should be exceptions rather than the norm.
      I'd like most of them to be somewhere in the middle, and ideally
      all maps should mix tactical density scales within them (long
      streets and the 4x4 park in +village2, for instance, provide big
      open lines broken up by dense structures).
- **Bad assemblies**: Some maps assemble in a way that makes no sense
  or, worse, leaves lots of big open spaces in the map.
  - IMHO, we should look carefully at each RMA theme and determine
    whether the algorithm is able to build good assemblies or whether a
    large number of fixed assemblies is a better strategy. Random
    assemblies in which lots of similar tiles can match up with each
    other easily (+oriental, +forest) work fine. But as soon as streets
    or any kind of overall design comes into play, it just doesn't work
    and we end up with lots of filler tiles to get them to build.
    --[H-Hour](User:H-Hour "wikilink")
    ([talk](User_talk:H-Hour "wikilink")) 16:33, 4 September 2013 (CEST)
- **Inefficient Texture Usage**: Many tiles will use 10 slight
  variations of the same basic concrete texture in a single RMA.
  - Although it's not a priority with this revision, we should try to
    streamline this where it is spotted and easily fixed. It will
    improve map loading times. --[H-Hour](User:H-Hour "wikilink")
    ([talk](User_talk:H-Hour "wikilink")) 16:33, 4 September 2013 (CEST)
- **Static Assets**: Some of our static maps are little more than a
  building or asset which ought to be incorporated into an existing
  tileset.
  - Beside from some special maps, all static and semiRMA maps schould
    be moved into an appropriate map theme.
    --[ShipIt](User:ShipIt "wikilink")
    ([talk](User_talk:ShipIt "wikilink")) 10:12, 5 September 2013 (CEST)
    - Agreed. --[H-Hour](User:H-Hour "wikilink")
      ([talk](User_talk:H-Hour "wikilink")) 10:22, 5 September 2013
      (CEST)
- **Map Selection**: Though not a problem of the maps, its still
  something thats needs to be improved. Crawling through the Mansion map
  fighting three aliens is a pain, as is fighting hordes of aliens on a
  small map. --[ShipIt](User:ShipIt "wikilink")
  ([talk](User_talk:ShipIt "wikilink")) 11:04, 5 September 2013 (CEST)
  - Agreed. Let's bother mattn during 2.6 dev until he gives up and
    [does what we
    want](Proposals/Temporary_Options_for_Large_Alien_Teams_on_Small_Maps "wikilink").
    --[H-Hour](User:H-Hour "wikilink")
    ([talk](User_talk:H-Hour "wikilink")) 11:11, 5 September 2013 (CEST)

## Terrain/Culture/Population Distribution

Should we think about what kind of RMAs we need? Although urban and
suburban maps are more interesting, the bulk of the game involves
players shooting down UFOs, which means players typically play a lot
more rural maps. I did some analysis of this a while ago. I'll see if I
can dig out my results, but maybe we should think of what RMAs can be
our workhorses for common terrain, culture or populations.
--[H-Hour](User:H-Hour "wikilink") ([talk](User_talk:H-Hour "wikilink"))
13:21, 13 September 2013 (CEST)

## Existing Map List

- +africa

- +alienb

  - special

- +b

  - special

- +beach

- +bomber_city

  - already moved to +urban

- +bridge

  - I think the player spawn points need to be moved closer to the
    building or something. Most of the gameplay plays out right around
    the house. It's not bad for a semi-static build (ie - just the
    dropship tiles changing). I'm not sure how we could extend it
    though, as the UFO tiles are very large.
    --[H-Hour](User:H-Hour "wikilink")
    ([talk](User_talk:H-Hour "wikilink")) 16:46, 4 September 2013 (CEST)

- +cemetery

  - Maybe a piece or two from this might be usable elsewhere. Beside
    that, this is not worth keeping it imo.
    --[ShipIt](User:ShipIt "wikilink")
    ([talk](User_talk:ShipIt "wikilink")) 10:50, 5 September 2013 (CEST)
    - I will take a closer look. Maybe some of the assets can form a
      cemetary in +village2. But if memory serves, I agree it can
      probably be scrapped. --[H-Hour](User:H-Hour "wikilink")
      ([talk](User_talk:H-Hour "wikilink")) 10:58, 5 September 2013
      (CEST)

- +city

- +city_disco

  - already moved to +urban

- +city2

  - remains static, I'd think. --[H-Hour](User:H-Hour "wikilink")
    ([talk](User_talk:H-Hour "wikilink")) 10:47, 5 September 2013 (CEST)

- +city3

  - remains as-is

- +clinic

  - This should be integrated into +urban, which is somewhat hard to do
    because of the underground level. But the +tower map is a similiar
    one, so maybe thats the way to go?
    --[ShipIt](User:ShipIt "wikilink")
    ([talk](User_talk:ShipIt "wikilink")) 10:20, 23 December 2013 (CET)
  - moved to +urban --[ShipIt](User:ShipIt "wikilink")
    ([talk](User_talk:ShipIt "wikilink")) 22:01, 6 August 2014 (CEST)

- +community_centre

  - already moved to +urban

- +construction

  - apartment building could probably go to +village2 or a future urban
    RMA.
  - building under construction could go to +industrial, a future urban
    RMA, or even +village2. Maybe it could even be a shared tile, used
    in a few different RMAs? --[H-Hour](User:H-Hour "wikilink")
    ([talk](User_talk:H-Hour "wikilink")) 10:47, 5 September 2013 (CEST)

- +country

  - The map uses the same buildings as the farm map. There are some
    rocks and road tiles. It had an assembly with a landed Scout/Fighter
    in 2.4, so it could be labeled "unused". In 2.5 I used the map to
    toy around with the Shared-Map-Tiles feature. I think, if we can get
    the texture replacement, we can safely dismiss this map.
    --[ShipIt](User:ShipIt "wikilink")
    ([talk](User_talk:ShipIt "wikilink")) 14:06, 26 September 2013
    (CEST)

- +desert

- +druglord

  - I think this can already be assembled fom the tiles of the +tropic
    map theme. --[ShipIt](User:ShipIt "wikilink")
    ([talk](User_talk:ShipIt "wikilink")) 22:01, 6 August 2014 (CEST)
    - Sounds good. Do any changes need to be made for +tropic or can we
      just remove this? --[H-Hour](User:H-Hour "wikilink")
      ([talk](User_talk:H-Hour "wikilink")) 15:11, 17 August 2014 (CEST)

- +eaglenest

  - Will go into +forest. --21:21, 4 February 2015 (CET)\~\~
  - Moved to +forest map theme. --[ShipIt](User:ShipIt "wikilink")
    ([talk](User_talk:ShipIt "wikilink")) 07:01, 28 July 2015 (CEST)

- +farm

- +farm2

  - The farm maps are great, but the assemblies are always terrible. I
    think with a few more assets and more consideration of the assembly
    (either fixed, or figure out better random builds) it could be very
    good. --[H-Hour](User:H-Hour "wikilink")
    ([talk](User_talk:H-Hour "wikilink")) 16:46, 4 September 2013 (CEST)
    - Possibly, we can trick RMA to make some more logical layouts. Or
      even code weights for preferred tile-to-tile combnations, like
      house to house, field to field, etc.
      [Sandro](User:Sandro "wikilink")
      ([talk](User_talk:Sandro "wikilink")) 11:03, 23 December 2013
      (CET)

- +forest

  - This tileset could be improved significantly by using fewer, but
    larger tiles, on which we could tailor the look of the forest a bit
    more. Maybe minimum 2x2, but it could even use mostly 4x4 tiles. The
    trees and foliage at the moment are too evenly-spaced, which I think
    is forced by the very small tile size (only a little space in the
    center of a tile for trees). They need to be clumped together more,
    and we could play with Sandro's new foliage feature to improve the
    look and feel. --[H-Hour](User:H-Hour "wikilink")
    ([talk](User_talk:H-Hour "wikilink")) 10:34, 5 September 2013 (CEST)
  - I rebuilt this from scratch. --[ShipIt](User:ShipIt "wikilink")
    ([talk](User_talk:ShipIt "wikilink")) 07:01, 28 July 2015 (CEST)

- +frozen

- +gasstation

- Should be integrated into +desert. --[ShipIt](User:ShipIt "wikilink")
  ([talk](User_talk:ShipIt "wikilink")) 21:21, 4 February 2015 (CET)

- +harbour2

- +hills

  - I'm planning to incorporate these buildings into +village2.
    --[H-Hour](User:H-Hour "wikilink")
    ([talk](User_talk:H-Hour "wikilink")) 16:46, 4 September 2013 (CEST)

- +ice

- +industrial

  - Right now, this is the new "+ufocrash" map. The theme is very
    versatile, it can be used for almost all locations.
    --[ShipIt](User:ShipIt "wikilink")
    ([talk](User_talk:ShipIt "wikilink")) 18:19, 4 September 2013 (CEST)
    - Cool, this is a very promising theme, I think. Every time I play
      it, I end up with just a bit too much open space, so I never
      really have to get into the buildings much -- just find a bit of
      cover and snipe any movement. This is especially true around the
      UFOs. Maybe we can tighten the tiles up a bit, improve the areas
      around UFOs, and produce slightly better assemblies. It could also
      use more buildings to diversify builds. But I definitely see this
      as a workhorse theme. --[H-Hour](User:H-Hour "wikilink")
      ([talk](User_talk:H-Hour "wikilink")) 00:37, 5 September 2013
      (CEST)

- +italy

- +japan

  - I can see this theme being similar to +village (suburban homes in an
    east asian style -- more wood, etc). Perhaps the assemblies could be
    low houses broken up by tall apartment buildings for good vantage
    points. It would distinguish the gameplay from +village a bit.
    --[H-Hour](User:H-Hour "wikilink")
    ([talk](User_talk:H-Hour "wikilink")) 11:03, 16 September 2013
    (CEST)

- +laboratory

  - already moved to +urban

- +mansion

- +mansion1

- +mart

  - already moved to +urban

- +military_convoy

  - I think we can integrate this into +forest.
    --[ShipIt](User:ShipIt "wikilink")
    ([talk](User_talk:ShipIt "wikilink")) 07:01, 28 July 2015 (CEST)

- +oriental

- +oriental_mosque

  - Should probably just be a part of +oriental.
    --[H-Hour](User:H-Hour "wikilink")
    ([talk](User_talk:H-Hour "wikilink")) 10:47, 5 September 2013 (CEST)
  - Every single asset of this map was already taken to +oriental. I
    removed this and rebuilt a similar map as an assembly in +oriental.
    --[ShipIt](User:ShipIt "wikilink")
    ([talk](User_talk:ShipIt "wikilink")) 18:24, 28 July 2015 (CEST)

- +rescue

- +scout_crash

  - Assets should be incorporated into +village2, then map should be
    removed. --[H-Hour](User:H-Hour "wikilink")
    ([talk](User_talk:H-Hour "wikilink")) 10:47, 5 September 2013 (CEST)
  - Moved to +village. --[ShipIt](User:ShipIt "wikilink")
    ([talk](User_talk:ShipIt "wikilink")) 07:01, 28 July 2015 (CEST)

- +shared

  - special

- +shelter

  - Keep as is? --[ShipIt](User:ShipIt "wikilink")
    ([talk](User_talk:ShipIt "wikilink")) 07:01, 28 July 2015 (CEST)

- +solarplant

- +spedition

  - moved to +industrial --[ShipIt](User:ShipIt "wikilink")
    ([talk](User_talk:ShipIt "wikilink")) 21:21, 4 February 2015 (CET)

- +stadium

  - already moved to +urban

- +tower

  - already moved to +urban --[ShipIt](User:ShipIt "wikilink")
    ([talk](User_talk:ShipIt "wikilink")) 22:01, 6 August 2014 (CEST)

- +transport

  - I moved the Warehouses to +industrial. The office building just
    doesn´t fit there. Need to find a new home for this one, too.
    --[ShipIt](User:ShipIt "wikilink")
    ([talk](User_talk:ShipIt "wikilink")) 22:01, 6 August 2014 (CEST)
    - Cool, can the office building go into +urban or is it not really
      worth it? --[H-Hour](User:H-Hour "wikilink")
      ([talk](User_talk:H-Hour "wikilink")) 15:11, 17 August 2014 (CEST)

- +tropic

- +ufocrash

  - special

- +urban

  - When I started this, it was only meant to be a collection of
    otherwise stand alone/semiRMA maps.
    --[ShipIt](User:ShipIt "wikilink")
    ([talk](User_talk:ShipIt "wikilink")) 09:57, 5 September 2013 (CEST)
    - Ahh ok. Yeah that's not a bad idea. Maybe farther down the road we
      can look at whether or not some of the assets can be flexible
      enough to be put together into large RMAs. I could foresee this
      beeing a good few-but-large-tiles RMA. Like putting two 4x4 tiles
      together and a dropship in the middle. If we have 4-5 of these
      tiles, it would provide some random replayability.
      --[H-Hour](User:H-Hour "wikilink")
      ([talk](User_talk:H-Hour "wikilink")) 10:29, 5 September 2013
      (CEST)

- +village

  - There are just a few assets that I have not ported over to +village2
    (garages, a rock). The garages and rock should be backed up
    somewhere (perhaps prefabs?), because they could be useful. But then
    this RMA can be removed once +village2 has several assemblies.
    --[H-Hour](User:H-Hour "wikilink")
    ([talk](User_talk:H-Hour "wikilink")) 10:57, 5 September 2013 (CEST)

- +village2

- bunker

- city_industry

  - This can probably be merged into an improved +industrial theme.
    --[H-Hour](User:H-Hour "wikilink")
    ([talk](User_talk:H-Hour "wikilink")) 10:47, 5 September 2013 (CEST)
  - moved to +industrial --[ShipIt](User:ShipIt "wikilink")
    ([talk](User_talk:ShipIt "wikilink")) 21:21, 4 February 2015 (CET)

- city_train

  - I've taken one of the houses already for +village2. The other
    doesn't look like it will port well (assumes a raised ground
    behind). I'll bet the train could be used somehow, though.
    --[H-Hour](User:H-Hour "wikilink")
    ([talk](User_talk:H-Hour "wikilink")) 16:46, 4 September 2013 (CEST)

- corrupter_crash

- dam

- england

  - This is a cool map, but the player start position is a real pain.
    Never get out of the bowl. --[H-Hour](User:H-Hour "wikilink")
    ([talk](User_talk:H-Hour "wikilink")) 16:46, 4 September 2013 (CEST)
  - Moved to +village. --[ShipIt](User:ShipIt "wikilink")
    ([talk](User_talk:ShipIt "wikilink")) 16:02, 16 December 2014 (CET)

- estate

  - already moved to +urban --[ShipIt](User:ShipIt "wikilink")
    ([talk](User_talk:ShipIt "wikilink")) 22:01, 6 August 2014 (CEST)

- excavation

  - Could be moved to +desert. --[ShipIt](User:ShipIt "wikilink")
    ([talk](User_talk:ShipIt "wikilink")) 21:21, 4 February 2015 (CET)

- ferry

  - Coudl be part of one of the harbour maps.
    --[ShipIt](User:ShipIt "wikilink")
    ([talk](User_talk:ShipIt "wikilink")) 21:21, 4 February 2015 (CET)

- fighter_crash

  - I have an idea for a semi-static RMA for this, similar to what I did
    with +bridge. The map has lots of good cover and interesting
    terrain, but the player starts in a horrible position. I will maybe
    try and make it so the player can start on any side of the map and
    maybe has a better chance to get into the heart of it (or better
    cover on the edges) to improve the gameplay.
    --[H-Hour](User:H-Hour "wikilink")
    ([talk](User_talk:H-Hour "wikilink")) 16:50, 4 September 2013 (CEST)

- gate

  - I could imagine this as a part of +forest.
    --[ShipIt](User:ShipIt "wikilink")
    ([talk](User_talk:ShipIt "wikilink"))21:21, 4 February 2015 (CET)
  - Moved to +forest map theme. --[ShipIt](User:ShipIt "wikilink")
    ([talk](User_talk:ShipIt "wikilink")) 09:57, 15 March 2015 (CET)

- harbour

- mine

- neighbourhood

  - Scope for an up-scale neighborhood RMA?
    --[H-Hour](User:H-Hour "wikilink")
    ([talk](User_talk:H-Hour "wikilink")) 16:46, 4 September 2013 (CEST)

- office

- oriental

  - Assets should be checked to ensure they're already in +oriental,
    then this can be removed. --[H-Hour](User:H-Hour "wikilink")
    ([talk](User_talk:H-Hour "wikilink")) 10:47, 5 September 2013 (CEST)

- pipes_const

- resort

  - My best idea was to integrate this into the +tropic theme. But this
    requires a lot of work. --[ShipIt](User:ShipIt "wikilink")
    ([talk](User_talk:ShipIt "wikilink")) 22:01, 6 August 2014 (CEST)
    - I like that idea. --[H-Hour](User:H-Hour "wikilink")
      ([talk](User_talk:H-Hour "wikilink")) 15:11, 17 August 2014 (CEST)

- rivertown

- small_house

  - Moved to +forest map theme. --[ShipIt](User:ShipIt "wikilink")
    ([talk](User_talk:ShipIt "wikilink")) 09:57, 15 March 2015 (CET)
  - Added to +village2 already, just needs to be removed.
    --[H-Hour](User:H-Hour "wikilink")
    ([talk](User_talk:H-Hour "wikilink")) 10:36, 5 September 2013 (CEST)

- small_street

  - Nice assets, but the buildings are connected in one long row, so it
    will be hard to integrate with other RMAs. Maybe we can convert it
    to be a special fixed assembly within the +village2 tileset?
    --[H-Hour](User:H-Hour "wikilink")
    ([talk](User_talk:H-Hour "wikilink")) 16:46, 4 September 2013 (CEST)
    - Could make a quite good tileset by itself. Just cut it, add 90
      degrees rotated versions of tiles, T and cross junctions -- and
      you will have a nice suburb map tileset.
  - moved to +village --[ShipIt](User:ShipIt "wikilink")
    ([talk](User_talk:ShipIt "wikilink")) 22:01, 6 August 2014 (CEST)

- subway

- training_a

  - mp-only

- training_b

  - mp-only

- village

  - I've taken the house from it for +village2, the other assets are
    already part of +village (and +village2), except for the apartment
    building. I'm not sure how well it fits, to be honest. Maybe it can
    just be scrapped. --[H-Hour](User:H-Hour "wikilink")
    ([talk](User_talk:H-Hour "wikilink")) 16:46, 4 September 2013 (CEST)

- wilderness

## Target Map List

### Super RMAs

RMA themes which accommodate lots of tiles, all UFOs, etc. Let's decide
on which ones we want to target to be our heavy lifters.

### RMAs

RMA themes with significant randomness and tiles.

- +forest
- +frozen
- +industrial
- +oriental
- +tropic
  - One idea I had was to incorporate +beach and the resort map into
    this theme. But this would require to raise the ground up to level 3
    at least. --[ShipIt](User:ShipIt "wikilink")
    ([talk](User_talk:ShipIt "wikilink")) 14:14, 26 September 2013
    (CEST)
- +village2
  - Add a few more buildings

  - Add all dropship tiles

  - Add all UFOs, landed and crashed

  - Create assemblies

### Semi-static RMAs

RMA themes which can support multiple dropships but may not have other
randomness (+bridge?).

- +urban
  - Collect all static maps into a +urban tile

### Static Maps

Which static maps should stick around because they're really good and
can't be integrated well into an RMA? (Bunker, Shelter)

- +city2
- +shelter
- bunker
  - Extend to support four insertion areas.
    [:<File:bunker_spawn.jpg>](:File:bunker_spawn.jpg "wikilink")
- subway