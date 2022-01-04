# Coverages in INSPIRE

![Themes](./pix/Themes.png)

## Overview
- [INSPIRE Themes with Coverage Models](./INSPIRE.md#inspire-themes-with-coverage-models)
- [INSPIRE Theme Geographical grid systems](./INSPIRE.md#inspire-theme-geographical-grid-systems)
- [Download Services for Coverages](./INSPIRE.md#download-services-for-coverages)
- [Required Extension to WCS](./INSPIRE.md#required-extension-to-wcs)
- [INSPIRE Data Models and Schemas](./INSPIRE.md#inspire-data-models-and-schemas)
- [INSPIRE WCS Demonstrator]()

## INSPIRE Themes with Coverage Models
The following INSPIRE Themes make use of Coverage Models:
- [Elevation (EL)](https://inspire.ec.europa.eu/Themes/118/2892) 
- [Geology (GE)](https://inspire.ec.europa.eu/Themes/128/2892) 
- [Land cover (LC)](https://inspire.ec.europa.eu/Themes/123/2892)
- [Land use (LU)](https://inspire.ec.europa.eu/Themes/129/2892)
- [Natural risk zones (NZ)](https://inspire.ec.europa.eu/Themes/140/2892)
- [Orthoimagery (OI)](https://inspire.ec.europa.eu/Themes/124/2892)
- [Soil (SO)](https://inspire.ec.europa.eu/Themes/127/2892)
- [Energy resources (ER)](https://inspire.ec.europa.eu/Themes/134/2892)
- [Species distribution (SD) – App. schema deprecated](https://inspire.ec.europa.eu/Themes/133/2892)

## INSPIRE Theme Geographical grid systems
![gg](./pix/ggS.png)

In addition to the INSPIRE Themes that use grids, there is also a [Geographical Grid Systems Theme](https://inspire.ec.europa.eu/Themes/131/2892), that specifies the grids to be utilized to define the Domain of the Coverage.

Two different grid systems are foreseen for use within INSPIRE:

- **Equal Area Grid:** The grid is based on the ETRS89 Lambert Azimuthal Equal Area (ETRS89-LAEA) coordinate reference system. The grid is hierarchical, with resolutions of 1m, 10m, 100m, 1000m, 10000m and 100000m. The grid orientation is south-north, west-east. The grid is designated as **Grid_ETRS89-LAEA**.
- **Zoned Geographic Grid:** The grid shall be based on the ETRS89-GRS80 geodetic coordinate reference system. The grid orientation shall be south-north and west-east. Factors are defined for 5 latitudinal zones (Table 1 of GG Data Spec) to mitigate the meridian convergence. The grid shall be designated **Grid_ETRS89-GRS80zn_res**, where n represents the number of the zone and res the cell size in angular units as defined in (Table 2 of GG Data Spec, Table 1 of the IR) 

For the Theme Elevation, the **Zoned Geographic Grid MUST** be used based on IR Requirement - Annex III Section 1.7.2 - Geographic Grids to be used for Elevation Data. This requirement further specifies:

> (1) By way of derogation from the requirement in Section 2.2 of Annex II, any grid compatible with one of the following coordinate reference systems may be used for making gridded Elevation data available:
> 
> – two-dimensional geodetic coordinates (latitude and longitude) based on a datum specified in Section 1.2 of Annex II and using the parameters of the GRS80 ellipsoid;
> 
> – plane coordinates using the ETRS89 Lambert Conformal Conic coordinate reference system;
> 
> – plane coordinates using the ETRS89 Transverse Mercator coordinate reference system.
> 
> The grid specified in 2.2.1 of Annex II shall not be used. 

_Note: 2.2.1 specifies the Equal Area Grid_

Based on this, we can use **EPSG::4258** for the horizontal component of the Coverage.

## Download Services for Coverages

As Coverages are formally features, one can provide them via a Web Feature Service (WFS). However, this tends to cause issues due to the size of the coverages, usually many GB. One approach is to subdivide the data into tiles, and providing an individual coverage for each tile. However, this solution is not satisfactory for users, as they must merge the coverages for their area of interest, while at the same time being forced to download data beyond this area of interest.

For the provision of Coverages, the [Open Geospatial Consortium (OGC)](https://www.ogc.org/) has created two dedicated web services within the wider OGC Web Service (OWS) Suite:
- [Web Coverage Service (WCS)](https://www.ogc.org/standards/wcs): allows for subsetting, retrieving data in diverse formats
- [Web Coverage Processing Service (WCPS)](https://www.ogc.org/standards/wcps): adds server side processing to WCS

In order to be utilized within INSPIRE, download services must be implemented in a manner that satisfies the requirements of the [Network Services Regulation](https://inspire.ec.europa.eu/Legislation/Network-Services/41). As some of these requirements go beyond what is specified in the OWS, some extensions are required. Pertaining to WCS, the [Technical Guidance for the implementation of INSPIRE Download Services using Web Coverage Services (WCS)](https://inspire.ec.europa.eu/id/document/tg/download-wcs) details what configurations and extensions are required. This document requires the use of WCS Version 2.0 or higher.

## Required Extension to WCS
The modification required to align WCS with the requirements laid down in the Network Services Regulation pertains to the contents of the GetCapabilities Response document. The following information must be provided in the ows:ExtendedCapabilities section of the GetCapabilities Response:
- Service Metadata: URL
- Supported and Response Language: ISO 3-Letter Code
- Dataset Metadata: URL
- CoverageID: Identifier
- Download Service Location: URL

In the following XML, these concepts are marked with comments

```
<ows:ExtendedCapabilities>
    <inspire_dls:ExtendedCapabilities>
        <inspire_common:MetadataUrl xsi:type="inspire_common:resourceLocatorType">
            <inspire_common:URL>
                <!-- Service Metadata: URL -->
                https://inspire…nl/fbd0d3da-e025-4728-8fd5-22ad5f530511
            </inspire_common:URL>
            <inspire_common:MediaType>application/xml</inspire_common:MediaType>
        </inspire_common:MetadataUrl>
        <inspire_common:SupportedLanguages>
            <inspire_common:DefaultLanguage>
                <!-- Supported Language: ISO 3-Letter Code -->
                <inspire_common:Language>eng</inspire_common:Language>
            </inspire_common:DefaultLanguage>
        </inspire_common:SupportedLanguages>
        <inspire_common:ResponseLanguage>
            <!-- Response Language: ISO 3-Letter Code -->
            <inspire_common:Language>eng</inspire_common:Language>
        </inspire_common:ResponseLanguage>
        <!-- Dataset Metadata: URL -->
        <inspire_dls:SpatialDataSetIdentifier metadataURL="https://inspire...nl/f670705f-f4e9-11e6-81e4"> 
            <!-- CoverageID: Identifier -->
            <inspire_common:Code>INSPIRE_WNZ_5_NAP</inspire_common:Code>
            <!-- Download Service Location: URL -->
            <inspire_common:Namespace>https://inspire…nl/rasdaman/ows</inspire_common:Namespace>
        </inspire_dls:SpatialDataSetIdentifier>
        ...
    </inspire_dls:ExtendedCapabilities>
</ows:ExtendedCapabilities>
```
At present, rasdaman has implemented this extension in their WCS implementation. At time of writing (27.12.2021), GeoSolutions is working on the extension for the GeoServer WCS. 

## INSPIRE Data Models and Schemas

The way the INSPIRE Data Models utilizing Coverages have been specified and then transposed to XML Schema and provided as XSD files, it is not possible to provide them via a WCS. This is due to the use of class derivation for adding additional required attributes to the INSPIRE coverage classes, instead of utilizing the metadata element foreseen in all coverage classes. In order to provide the data via WCS, the data models must first be revised as described in the following sections. This approach has been documented as an [INSPIRE Good Practice](https://inspire.ec.europa.eu/portfolio/good-practice-library). More information on the [INSPIRE Coverage Good Practice](https://inspire.ec.europa.eu/good-practice/ogc-compliant-inspire-coverage-data-and-service-implementation) is available at: https://inspire.ec.europa.eu/good-practice/ogc-compliant-inspire-coverage-data-and-service-implementation

### INSPIRE Elevation Data Model

In the following diagram, one sees how the ElevationGridCoverage class has been derived from RectifiedGridCoverage:

![INSPIRE Elevation Data Model](./pix/INSPIRE%20Elevation%20Model.png)

However, this leads to the ElevationGridCoverage class being extended by all the additional attributes, leading to the following:

![ElevationGridCoverage all attributes](./pix/INSPIRE%20Elevation%20Extension%20Example.png)

### INSPIRE Coverage Good Practice Model

In order to provide the additional attributes specified for the ElevationGridCoverage class via the metadata element of RectifiedGridCoverage, we must first create a new featureType with these attributes as shown below:

![ElevationGridCoverageMetadata](./pix/Elevation%20Good%20Practice.png)

The schema for this featureType is available from https://schema.datacove.eu/ElevationGridCoverageMetadata.xsd

## INSPIRE WCS Demonstrator

On a more general level, we've set up a WCS together with additional information on Coverages and WCS in INSPIRE. This is available at https://inspire-wcs.eu/
