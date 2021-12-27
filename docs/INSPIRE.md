# Coverages in INSPIRE

![Themes](./pix/Themes.png)

## Overview
- [INSPIRE Themes with Coverage Models](./INSPIRE.md#inspire-themes-with-coverage-models)
- [INSPIRE Theme Geographical grid systems](./INSPIRE.md#inspire-theme-geographical-grid-systems)

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

For the Theme Elevation, the **Zoned Geographic Grid:** must be used based on IR Requirement - Annex III Section 1.7.2 - Geographic Grids to be used for Elevation Data. This requirement further specifies:

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
