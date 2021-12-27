# Providing Coverages

## Data Sources
The original elevation source data is often point/vector based, this must first be transformed to a grid in accordance with the requirements to [Geographical grid systems](https://github.com/codefornl/INSPIRE-Coverages/blob/main/docs/INSPIRE.md#inspire-theme-geographical-grid-systems). 
For the purposes of this PoC, EPSG::4258 will be used. 
GeoTIFF is a useful format for the transfer of this gridded data from the source database to the WCS server.

As gridded data rapidly becomes unmanageable due to size, one can subset the dataset into tiles for transfer and import to the WCS. 
WCS can import multiple input grids and merge these to one coverage. Such tiling  greatly reduces the amount of memory required by the server.
The elevation data should be transformed to the target CRS close to source. While the gridded data can also be transformed later, this reduces accuracy!

Gdal library was proven to be very useful for both CRS transformation and tiling of larger elevation datasets.

## Additional INSPIRE Attributes
XML Snippets must be created for the additional INSPIRE attributes, that can be provided via the metadata element of the Coverage. 
One XML Snippet must be created per Coverage ID available via the WCS.
