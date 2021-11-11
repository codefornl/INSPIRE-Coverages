# Data Sources

_Note: Value is always in the corner (bottom left)_

## Elevation and Bathymetry Data (Gridded)

*Note: for the first PoC around Limburg, we focus on the file INSPIRE_MN_noord_5_NAP*

### Files bathymetry 1 mtr. bodemhoogte (recommended):

https://www.rijkswaterstaat.nl/apps/geoservices/geodata/dmc/bodemhoogte_1mtr 

### Files bathymetry 5 mtr. bodemhoogte:
https://www.rijkswaterstaat.nl/apps/geoservices/geodata/dmc/bodemhoogte_5mtr

This source looks good! Has the TIF files, XML Snippets and XML Metadata 

**Problem:** Currently in the wrong projection (EPSG:4258), should be in EPSG:3035 (ETRS89-extended / LAEA Europe)

### Files bathymetry 20 mtr. bodemhoogte:
https://www.rijkswaterstaat.nl/apps/geoservices/geodata/dmc/bodemhoogte_20mtr

**Problem:** This page is still totally empty!

### Elevation AHN3:
https://www.rijkswaterstaat.nl/apps/geoservices/geodata/regios/civ/poc_coverages/AHN3/

## Water Level Data (Point Sources)

### Source data from waterinfo

https://waterinfo.rws.nl/api/chart?mapType=waterafvoer&locationCode=Olst(OLST)-1&values=-48,48

### WaterInfo Data in STA

https://ogc-demo.k8s.ilt-dmz.iosb.fraunhofer.de/v1.1/

### Web Viewer

The HTML for the [STA Web Viewer](STAViewer.html) is available.

An online version has been provided at:

http://info.datacove.eu/WaterinfoSTA.html

## Neighboring Data

### DE Rhine Bathymetry

Geoportal der BfG - Metadata to DGM-W of the Rhine: https://geoportal.bafg.de/smartfinderClient/js/apps/portal-integration/index.html?lang=de#/datasets/iso/15b1c01e-4285-4d7d-808d-597236830d86 

Data (URLs to TIFs) available from the following page: https://doi.pangaea.de/10.1594/PANGAEA.919308?format=textfile

Additional information: 
Ein DGM-W bildet die Höhe der Gewässersohle als auch des Gewässerbetts und der näheren Umgebung ab: https://www.bafg.de/DE/08_Ref/M5/03_Geotopographie/DGMW/dgmw.html Sind das in etwa die Daten, die Sie, bzw. die Niederländer suchen?

_Note: info from Lukas Glaw - BfG_

### DE Elevation

Die terrestrische Höhe wird von den Landesvermessungsämtern mit einer Gitterweite von mindestens 1 m erhoben und ist je nach Bundesland frei verfügbar oder kostenpflichtig. NRW hat eine Open Data policy und stellt die Daten frei zur Verfügung. Es gibt inzwischen aber auch ein freies DOM von ganz Deutschland: https://gdz.bkg.bund.de/index.php/default/digitale-geodaten/digitale-gelandemodelle/digitales-oberfaechenmodell-dom1.html

Der Download der DGM-Daten von NRW geht glaub ich über https://www.tim-online.nrw.de/tim-online2/



### BE Elevation

From INSPIRE Geoportal:
https://inspire-geoportal.ec.europa.eu/download_details.html?view=downloadDetails&resourceId=%2FINSPIRE-b285fced-4eb6-11e8-a459-52540023a883_20210618-150902%2Fservices%2F1%2FPullResults%2F1-138%2Fdatasets%2F37&expandedSection=metadata

Issues:
- Wrong CRS
- 20m grid
