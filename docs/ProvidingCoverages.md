# Providing Coverages

## Overview
- [Data Sources](./ProvidingCoverages.md#data-sources)
- [Additional INSPIRE Attributes](./ProvidingCoverages.md#additional-inspire-attributes)

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

![ElevationGridCoverageMetadata](./pix/Elevation%20Good%20Practice.png)

This requires the provision of the following information, with the values from the example below in []:
- beginLifespanVersion: the time this electronic object was created [2021-04-09T00:00:00+01:00]
- domainExtent: spatial extent of the coverage in WGS84 coordinates
  - westBoundLongitude: western extent of the coverage [3.9632793]
  - eastBoundLongitude: eastern extent of the coverage [4.8789582]
  - southBoundLatitude: southern extent of the coverage [51.8526434]
  - northBoundLatitude: northern extent of the coverage [52.0129335]
- inspireId: INSPIRE identifier of the coverage
  - localId: A local identifier, assigned by the data provider. For consistency, use the CoverageID [INSPIRE_WNZ_5_NAP]
  - namespace: Namespace uniquely identifying the data source of the spatial object [https://www.rijkswaterstaat.nl]
- propertyType: the elevation property represented by the elevation grid coverage. Must be 'height' or 'depth'  [depth]
- surfaceType: the type of elevation surface that the coverage describes in relation to the Earth's bare surface. Must be 'DTM' or 'DSM'  [DTM]

In the following XML example, the values listed above are encoded:

```
<?xml version="1.0" encoding="UTF-8"?>
<el-covmd-ks:ElevationGridCoverageMetadata xmlns:el-covmd-ks="http://inspire.ec.europa.eu/schemas/el-covmd/4.0"
    <el-covmd-ks:beginLifespanVersion>2021-04-09T00:00:00+01:00</el-covmd-ks:beginLifespanVersion>
    <el-covmd-ks:domainExtent>
        <gmd:EX_Extent>
            <gmd:geographicElement>
                <gmd:EX_GeographicBoundingBox>
                    <gmd:westBoundLongitude><gco:Decimal>3.9632793</gco:Decimal></gmd:westBoundLongitude>
                    <gmd:eastBoundLongitude><gco:Decimal>4.8789582</gco:Decimal></gmd:eastBoundLongitude>
                    <gmd:southBoundLatitude><gco:Decimal>51.8526434</gco:Decimal></gmd:southBoundLatitude>
                    <gmd:northBoundLatitude><gco:Decimal>52.0129335</gco:Decimal></gmd:northBoundLatitude>
                </gmd:EX_GeographicBoundingBox>
            </gmd:geographicElement>
        </gmd:EX_Extent>
    </el-covmd-ks:domainExtent>
    <el-covmd-ks:inspireId>
        <base:Identifier>
            <base:localId>INSPIRE_WNZ_5_NAP</base:localId>
            <base:namespace>https://www.rijkswaterstaat.nl</base:namespace>
        </base:Identifier>
    </el-covmd-ks:inspireId>
    <el-covmd-ks:propertyType>depth</el-covmd-ks:propertyType>
    <el-covmd-ks:surfaceType>DTM</el-covmd-ks:surfaceType>
</el-covmd-ks:ElevationGridCoverageMetadata>
```

## Importing Data

Putting it all together, in order to import one coverage, you need:
- 1 Coverage ID
- Gridded data, e.g. Tif
  - Can be multiple files
- 1 XML Snippet (as described above in [Additional INSPIRE Attributes](./ProvidingCoverages.md#additional-inspire-attributes))
- Language (usually default English)
- Metadata URLS for
  - Service Metadata (ISO 19119)
  - Dataset Metadata (ISO 19115)

