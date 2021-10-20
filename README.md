# INSPIRE-Coverages
A repository for collecting and distributing information on INSPIRE Coverages

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


# WS Info
Direct connected with the dutch Geoforum (https://geoforum.nl/t/inspire-coverages)

We would like to invite you to take note of our experiences.

# Workshop (moment to decide)
# Wednesday- or thursdayafternoon on  17 - 18 - 24 or 25 november 
- Online
- Doodle the workshop (yes,no,may be)

# Purpose
Sharing the results and experiences with the INSPIRE GoodPractice Coverages.
We will show and interact the results and a bit of use. The promairy focus will be on support the provision.

# Target audience
Current providers, not users. 
Team members Data-providers (AHN, Bathymetry, WaterInfo, orthofoto's e.a. uit Duitsland, België, Luxemburg)
Team members INSPIRE-services RWS (RWS, Sweco, WetRansform, PDOK)
Team members INSPIRE operationeel overleg (MinBzK, MinIenW)
Gebruikers en studenten grensoverschrijdende raster en sensor data (Copernicus, SeadataNed, OSPAR, ISRIC, ...)

# Explanation
Raster data (coverages) are extremely important to spatially analyze dynamic phenomena such as soilchanges, floading, noise pollution.
To do this across international borders, an INSPIRE GoodPractice coverages was established at the beginning of 2021. In order to bring the experts together and get to know the process, the components and the issues, a Proof off Concept (PoC) has been carried out since September.

# PoC
The PoC INSPIRE Goodpractivce Coverages includes the INSPIRE compliant provision of grid and if possible sensor data.
There is knowledge and experience gained with the collecting, conversion and publication of the coverage data. 

In the PoC we process AS-IS data from the source into the data as defined by INSPIRE. 
In the data we distinguish bathymetry, altitude and water quality and water quantity related data.

Expected results are:
- Process
- Experiences
- Issues and solutions
- INSPIRE Goodpractice compliant services

# Participants
The following parties are participating in the chain: JRC, MinBzK, Geonovum, INSPIRE operational consultation, Sweco, DataCov, WetRansform, PDOK and Rijkswaterstaat.

