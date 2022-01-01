# INSPIRE-Coverages
A repository for collecting and distributing information on INSPIRE Coverages


## Goals

Provide Elevation and Bathymetry data with WCS on a 1 and 10m grid for the NL Limburg area, following [INSPIRE Good Practice (GP)](https://inspire.ec.europa.eu/good-practice/ogc-compliant-inspire-coverage-data-and-service-implementation). This data will be complemented with point based measurement data (e.g. water levels, precipitation forecast) provided via SensorThings API. The results together with usage examples will be presented at the final workshop.

[Detailed overview of the PoC Goals](docs/goals.md)

## Coverages in a Nutshell
In this section, we provide the fundamentals pertaining to Coverages. We describe the unterlying Coverage Data Models as well as the OGC Web Services foreseen for their provision.

[Coverages in a Nutshell](docs/nutshell.md)

## Coverages in INSPIRE
While this PoC is focused on the provision of Elevation Coverages, INSPIRE utilizes coverages for a diverse range of Themes. In this section, we provide information on the wider context of Coverages in INSPIRE.

[Coverages in INSPIRE](docs/INSPIRE.md)

## Providing Coverages within INSPIRE
In this section, we start putting the theory from the sections above into praxis. We show what information must be collected in addition to the elevation data, and how to import this to a WCS server, using [radsaman](http://rasdaman.org/) as an example. We also discuss some problems faces, and how to resolve them.

[Providing Coverages](docs/ProvidingCoverages.md)

## Using Coverages
Once the elevation data is available via WCS, data for the spatial area of interest can be requested from this service. In this section, we describe how to utilize WCS to access data, as well as use it via common GIS tools.

[Using Coverages](docs/UsingCoverages.md)

## Servers

Elevation and bathymetry data from RWS, focused around the area of Limburg, are available from the following WCS server:

Wetransform: https://coverage-demo.wetransform.eu/rasdaman/ows

Example Request for NL Bathymetry: https://coverage-demo.wetransform.eu/rasdaman/ows?&SERVICE=WCS&VERSION=2.0.1&REQUEST=GetCoverage&COVERAGEID=INSPIRE_WNZ_5_NAP&SUBSET=Y(3117600,3124600)&SUBSET=X(4024000,4031000)&FORMAT=image/tiff

Additional examples, including elevation data from Belgium that overlaps Limburg, but at a lower resolution, are available from the following WCS server:

DataCove: http://sandbox.datacove.eu:8080/rasdaman/ows

Example Request for BE Elevation: http://sandbox.datacove.eu:8080/rasdaman/ows?&SERVICE=WCS&VERSION=2.0.1&REQUEST=GetCoverage&COVERAGEID=INSPIRE_BE_Limburg&SUBSET=Y(3117600,3124600)&SUBSET=X(4024000,4031000)&FORMAT=image/tiff

## Issues

Information on all [issues](docs/Issues.md)

## Workshop 
Direct connected with the dutch Geoforum (https://geoforum.nl/t/inspire-coverages)

The INSPIRE Coverage PoC WS was held on **Thursday 18 November, 13:15 - 15:30**

Details on the [Workshop](docs/Workshop.md)
