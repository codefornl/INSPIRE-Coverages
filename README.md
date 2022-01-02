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

Elevation and bathymetry data from RWS, focused around the area of Limburg, has been made available via WCS servers.

[PoC WCS Servers](docs/Servers.md)

## Issues

All issues identified during the course of this work that could not be resolved within the PoC timeframe have been collected in the Issues section of this repository.

[PoC WCS Servers](https://github.com/codefornl/INSPIRE-Coverages/issues)


## Workshop 
Direct connected with the dutch Geoforum (https://geoforum.nl/t/inspire-coverages)

The INSPIRE Coverage PoC WS was held on **Thursday 18 November, 13:15 - 15:30**

Details on the [Workshop](docs/Workshop.md)
