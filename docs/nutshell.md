# Coverages in a Nutshell

While a lot of “normal” spatial data relies on points, lines and polygons for the representation of spatial objects, this approach doesn’t work when providing data over a larger area where the values vary across the area. A nice example of this is Elevation, what “normal” spatial feature would one use to represent the varying elevation values across a country? While one could serve lots of individual points or little polygons, one for each measurement point, such an approach becomes very inefficient when dealing with high resolution data, e.g. an elevation point every 5m.

## Coverage Domain
Coverage models take a different approach, relying on the regularity of the positioning of the measurement points. If we know that the measurement points are actually located on a rectilinear grid, we don’t need to list every point individually! Instead, all we need to define the basic grid are:
- The origin: a point from which we start our grid
- 2 offset vectors: these are usually expressed as E(ast) and N(orth) or X and Y
- Extent: how many steps do we take in each direction
