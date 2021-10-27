# INSPIRE-Coverages
A repository for collecting and distributing information on INSPIRE Coverages

## Workshop 
Direct connected with the dutch Geoforum (https://geoforum.nl/t/inspire-coverages)

Date: **Thursday 18 November, 13:15 - 15:30**

Details on the [Workshop](docs/Workshop.md)

## Goals

Provide Elevation and Bathymetry data with WCS on a 1 and 10m grid for the NL Limburg area, following [INSPIRE Good Practice (GP)](https://inspire.ec.europa.eu/coverage-good-practice). This data will be complemented with point based measurement data (e.g. water levels, precipitation forecast) provided via SensorThings API. The results together with usage examples will be presented at the final workshop.

[Detailed overview of the PoC Goals](docs/goals.md)

## Timeline

2021-09-07: Kickoff

End September: Data Identified and Available 

End October: First WCS Online

NOT! 2021-11-20: [Workshop on INSPIRE WCS Proof-of-Concept](docs/Workshop.md)

## Process

Information on the [data provision process](docs/ProvisionProcess.md)

## Data Sources

All [data sources](docs/DataSources.md)

## Servers

DataCove: http://sandbox.datacove.eu:8080/rasdaman/ows#/services

## Issues

Grid resolution: INSPIRE thinks in powers of 10, grids are 1, 10, 100.... m. Various existing EU projects think in 20m grids (unclear what the CRS is)
Approach: provide 1 & 10 m under INSPIRE, continue to provide 20m for the other projects but complying to INSPIRE WCS guidelines. Need to determine CRS for this

Do we provide all elevation in one coverage for NL, or subset by area? What IT Requirements to support this?

How to deal with the fact that canals cross?
- Created an [Issue](https://github.com/INSPIRE-MIF/helpdesk/issues/64) on the INSPIRE Helpdesk (26.10.21)

