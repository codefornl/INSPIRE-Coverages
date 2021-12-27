# Issues

## CRS

## RangeType Encoding


# OLD 
## Grid resolution
INSPIRE thinks in powers of 10, grids are 1, 10, 100.... m. Various existing EU projects think in 20m grids (unclear what the CRS is)
Approach: provide 1 & 10 m under INSPIRE, continue to provide 20m for the other projects but complying to INSPIRE WCS guidelines. Need to determine CRS for this

## Granularity
Do we provide all elevation in one coverage for NL, or subset by area? What IT Requirements to support this?

## Unclear terrain
How to deal with the fact that canals cross?
- Created an [Issue](https://github.com/INSPIRE-MIF/helpdesk/issues/64) on the INSPIRE Helpdesk (26.10.21)

## Different Sea Levels

When we merged the elevation data for NL and BE, the NL canals were flying ~10m over the BE terrain. Underlying issue are different base sea levels per country, details at:
- https://de.wikipedia.org/wiki/H%C3%B6he_%C3%BCber_dem_Meeresspiegel

_Note: article is German, but essence understandable_

