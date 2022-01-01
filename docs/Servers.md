# WCS Servers

Elevation and bathymetry data from RWS, focused around the area of Limburg, are available from the following WCS server:

Wetransform: https://coverage-demo.wetransform.eu/rasdaman/ows

Example Request for NL Bathymetry: https://coverage-demo.wetransform.eu/rasdaman/ows?&SERVICE=WCS&VERSION=2.0.1&REQUEST=GetCoverage&COVERAGEID=INSPIRE_WNZ_5_NAP&SUBSET=Y(3117600,3124600)&SUBSET=X(4024000,4031000)&FORMAT=image/tiff

Additional examples, including elevation data from Belgium that overlaps Limburg, but at a lower resolution, are available from the following WCS server:

DataCove: http://sandbox.datacove.eu:8080/rasdaman/ows

Example Request for BE Elevation: http://sandbox.datacove.eu:8080/rasdaman/ows?&SERVICE=WCS&VERSION=2.0.1&REQUEST=GetCoverage&COVERAGEID=INSPIRE_BE_Limburg&SUBSET=Y(3117600,3124600)&SUBSET=X(4024000,4031000)&FORMAT=image/tiff

