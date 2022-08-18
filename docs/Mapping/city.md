***This map has been discontinued, but may be restarted at some point in
the future.***

## Introduction

The +city RMA is designed for urban maps and will most commonly be used
for terror missions. A city street grid can be assembled with the tiles,
including a rail line and an underground passageway.

Currently, it is missing the corruptor and bomber UFO tiles, and it only
has one building tile. To make it properly random it will need several
building tiles.

Large buildings fit on four RMA tiles (1024x1024 in Radiant) and
depending on how it fits, it would be nice if some made use of the
underground tunnel (see citybldl_4x4_1a). The buildings must be large,
but keep in mind that if the building is too large and maze-like, the
missions could become tedious. Eventually, there will be 3 building
tiles and a UFO, which could mean an excessively long mission if all the
buildings are very big.

## Design/Tactical Considerations

So far, I've been going for a city with sharp colors, but only
moderately futuristic design. While 2084 may seem a long way off, the
look of many cities today still bears the imprint of design choices from
50+ years ago (even more in many places).

I've also had a habit of making the first floor two levels high, to
reflect the often higher ceiings of commercial buildings.

Tactically, try to think of how the buildings will work together rather
than just the building you're working on. Urban environments should
provide many opportunities for sniping down streets, ambushing from
windows and high vantage points, etc. The city should not be a
collection of closed boxes on a street grid.

## Naming Schema

All tiles have the city prefix. All tiles also have a suffix of
something like 1a. The number (1 in this example) will represent one
general "thing", like the same building or the same street tile. The
letter (a in this example) will represent a variation, like the same
street but with different vehicles or different signs. The only
implementation of this so far is **citystr_rail_top2a** and
**citystr_rail_top2b**. The 2a tile has a large billboard contraption,
but 2b does not.

**citybld\*** -- The "bld" stands for building. After bld, there should
be an "l" or "r" denoting whether the building should be on the left or
right side of a main street.

**citystr** -- The "str" stands for street. If there is a "v", this
street runs vertically. If there's a "h", it runs horizontally. It can
also have "cw", which stands for a crosswalk.

**rail** -- Any tile with "rail" in the name includes the railway down
the middle of the street. These exist only on vertical tiles.

**cross** -- Any tile with "cross" in the name is for a crossroads. It
will need streets running vertically and horizontally on its sides.

## Tiles

### Dropship Tiles

**citycraft_drop_firebird, citycraft_drop_herakles,
citycraft_drop_raptor:** Dropship tiles on a vertical city street with a
rail line down the middle.

### Small UFO Tiles

**citycraft_ufo_scout, citycraft_ufo_fighter, citycraft_ufo_supply:**
UFO tiles within a 4x4 public square. Used in the small assembly.

### Medium UFO Tile

**citycraft_ufo_harvester:** A UFO tile on a 4x4 public square and one
line of vertical street to its left. Used in the medium assembly.

### Incomplete Building Tiles

**citybldl_4x4_1a, citybldr_4x4_1a, citybldr_4x4_2a:** Currently these
are only place holder files and are not implemented in any assembly. The
1a tiles have the underground connection.

### citybldl_4x4_2a

A parking garage on the left side of the street. No underground
connection.

### citystr_cross

A crossroads tile connecting single street tiles vertically and
horizontally.

### citystr_rail_cross

A crossroads tile connecting a vertical street with a rail line (3 tiles
wide) and a single horizontal street.

### citystrc_sw_1a

A street tile with a 90 degree turn. Currently not in use.

### citystrh_1a

A horizontal street tile.

### citystrh_cwl_1a

A horizontal street tile with a crosswalk on its left side.

### citystrh_cwr_1a

A horizontal street tile with a crosswalk on its right side.

### citystrv_1a

A vertical street.

### citystrv_rail_1a

A vertical street with a rail line in the middle and a rail stop, with
the underground link.

### citystrv_rail_2a

A vertical street with a rail line in the middle. Requires
**citystrv_rail_btm2a** on its bottom edge, which then connects to
**citystr_rail_cross** on the bottom. Requires **citystrv_rail_top2a**
on its top edge, which then connects to **citystr_rail_cross** on the
top

## Links

- [Mapping/Random map assembly](Mapping/Random_map_assembly "wikilink")
- [Mapping/Random map parts](Mapping/Random_map_parts "wikilink")

[Category:Contribute](Category:Contribute "wikilink")
[Category:Mapping](Category:Mapping "wikilink")