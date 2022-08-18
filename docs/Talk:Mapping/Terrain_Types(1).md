- Is there need for more terrain types?
  --[Tecturon](User:Tecturon "wikilink") 21:49, 21 August 2007 (CEST)
  - jungle?
  - farmland?
- I don't believe urban or village should count as terrain types. I
  believe these should be part of a different layer. The Campaign
  proposal mentions the use of different layers to determine what maps
  and missions are suitable for a given spawned event, and I consider
  the following three layers to be relevant so far:
  - Terrain. This only deals with climatological features (deserts, ice,
    jungles, mountains).
  - Culture. This deals with things like building styles and languages
    used on signs.
  - Population density. This mask would influence how likely it is that
    a city or village map is used as opposed to a rural or unpopulated
    one.

To illustrate, both the "drug" tropic assembly and the "village"
assembly would count as a village map, but the former is set in a jungle
region while the latter is set in a temperate region. In other words,
they would be in a different type of area on the first layer yet be
chosen because they are both in a reasonably populated area on the third
layer.
A rough idea of how I imagine the population density layer is [this
image](http://earthtrends.wri.org/images/maps/4_m_Globalpopdens_lg.gif).
--[BTAxis](User:BTAxis "wikilink") 22:23, 21 August 2007 (CEST)

- Theoretically I share your point of view. But practically, this
  implies a highly flexible and dynamic map generation algorithm. As far
  as I understood, the map tiles being connected to each other when
  building a random map are completely predefined. Three different
  layers inadvertably lead to a multiplication of the amount of tiles
  needed. Where you needed 8 tile sets in my first draft, you will need
  16 tile sets if you subdivide each terrain type into only two culture
  types. Imagine you have 4 culture types, 4 types of population density
  and 8 terrain types. This results in an amount of 128 different tile
  sets. For each tile set, you will have to set buildings, ufos, trees,
  streets... --[Tecturon](User:Tecturon "wikilink") 12:25, 22 August
  2007 (CEST)
  - Ah, no. The layers don't *generate* a mission, they *eliminate* the
    ones that are unsuitable. To take your example of the 8-tile mapset,
    this mapset will have a descriptor file that describes what terrain
    types it can appear on, what cultural regions it can appear on and
    what the population threshhold is. If one or more of these factors
    are incompatible with the location that the mission takes place at,
    the map can not be used. --[BTAxis](User:BTAxis "wikilink") 12:44,
    22 August 2007 (CEST)
    - ok, that is an idea. It implies that all map tiles have a ufo
      descriptor defining the inclusion criteria. "I can only be used in
      urban regions, with high population and an north-american culture.
      Terrain types might be grass, jungle, desert. (That's because of
      the big Planet-Hollywood I represent)". But how would you ensure
      that all tiles have the same ground? The ufo descriptors would
      have to be very restrictive to ensure that, possibly negating the
      positive effect. Otherwise, the system could generate a map with
      snow on the eastern end and desert on the western end, because
      that Planet Hollywood was defined to be suitable for cold and warm
      regions. Nonetheless I'm eager to build a prototype-patch.
      --[Tecturon](User:Tecturon "wikilink") 13:14, 22 August 2007
      (CEST)
      - Again, the map layers nor the map descriptors don't determine
        what the map looks like, they only determine if the map is
        suitable. The maps are fixed - the ground does not change
        depending on what terrain it's on (PHALANX bases are an
        exception to this). Example: map industrial06. This is a snowy
        map with heavy machinery on it. Let's assume for the sake of the
        argument that the parameters for this map are: terrain: arctic
        only. culture: any. population density: any. Now supposing a
        mission was generated in northern Russia, then the conditions
        for this map would be met. Note that terrain is the ONLY
        requirement for this map. It could technically spawn on the
        south pole. However, it could NOT spawn in any non-arctic
        region. Another example: map village07. This is a suburban map
        with grass and trees. Suppose for the sake of the argument that
        the parameters for this map are: terrain: grass. culture:
        western, eastern. population density: 30% or higher. This map
        could spawn anywhere in Europe, North America or Asia as long as
        the terrain type is right, but NOT in the Middle-East or Africa
        because the culture isn't right. It also couldn't spawn in areas
        that had too little population.
        --[BTAxis](User:BTAxis "wikilink") 13:44, 22 August 2007 (CEST)