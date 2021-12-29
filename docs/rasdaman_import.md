# Rasdaman Data Import


## Overview
- [Installing rasdaman](./rasdaman_import.md#installing-rasdaman)
- [Server Requirements](./rasdaman_import.md#server-requirements)
- [Importing Elevation Data](./rasdaman_import.md#importing-elevation-data)

## Installing rasdaman
Before we can import the coverages to the WCS, we must first install the WCS server. For rasdaman, all information required for installation are available at the following site:

https://doc.rasdaman.org/02_inst-guide.html

## Server Requirements
While especially the number of CPUs required for a WCS server is hard to quantify, as this is also dependant on user behavior, the following information provides a general rule of thumb pertaining to server scoping:
- RAM: 64GB
- Hard Disk: Approx 3 x Data Volume
- CPUs: Depends on degree of parallelization
  - rasdaman runs on 4 cores in parallel
  - 8 CPUs are a basic recommendation, but more will be required if many parallel requests are received

As providing a valid estimate for the ideal number of CPUs for a given WCS, it is recommended to utilize a Virtual Machine (VM) for the WCS server, as VMs allow for simple scaling based on actual usage and performance

## Importing Elevation Data
An import script, wcst_import.sh, is provided together with the rasdaman server deployment. This script is configured by a so-called 'recipe' file in which the necessary 'ingredients' have been added. For more details on wcst_import.sh, recipes and ingredients, see: https://doc.rasdaman.org/05_geo-services-guide.html#data-import

For the provision of elevation data in rasdaman, we must add the following ingredients to the recipe in order to configure wcst_import:
- Local rasdaman service URL ```"config"."service_url": "http://localhost:8080/rasdaman/ows"```
  - Note: this will usually be localhost, as Transactional WCS (WCST) is usually only enabled for localhost
- Coverage ID ```"input"."coverage_id": "INSPIRE_WNZ_5_NAP"```
- Path to gridded data files, e.g. Tif files ```"input"."paths": ["*.tif"]```
- CRS, should always be EPSG/0/3035 ```"recipe"."options"."coverage"."crs": "EPSG/0/4258"```
- Bands, in the case of Elevation, should be
  - name: Elevation ```"recipe"."options"."coverage"."slicer"."bands"."name": "Elevation"```
  - identifier: Grey ```"recipe"."options"."coverage"."slicer"."bands"."identifier": "Grey"```

In addition, setting ```config"."mock": true``` is useful while debugging a recipe. While this value is set to ```true```, all steps except for the actual import will be performed, allowing for checks before starting the actual timeconsuming import process. Once the recipe is deamed valid, this value should be set to ```false```, triggering the actual data import.


```
{
    "config": {
        "service_url": "http://localhost:8080/rasdaman/ows",
        "tmp_directory": "/tmp/",
        "mock": false,
        "automated": true,
        "track_files": false
    },
    "input": {
        "coverage_id": "INSPIRE_WNZ_5_NAP",
        "paths": [
            "*.tif"
        ]
    },
    "recipe": {
        "name": "general_coverage",
        "options": {
            "coverage": {
                "crs": "EPSG/0/4258",
                "metadata": {
                    "type": "xml",
                    "global": {
                        "Title": "'metadata placeholder'"
                    }
                },
                "slicer": {
                    "type": "gdal",
                    "bands": [{
                        "name": "Elevation",
                        "identifier": "Grey"
                    }],
                    "axes": {
                        "long": {
                            "min": "${gdal:minX}",
                            "max": "${gdal:maxX}",
                            "crsOrder": 2,
                            "gridOrder": 1,
                            "resolution": "${gdal:resolutionX}"
                        },
                        "lat": {
                            "min": "${gdal:minY}",
                            "max": "${gdal:maxY}",
                            "crsOrder": 1,
                            "gridOrder": 2,
                            "resolution": "${gdal:resolutionY}"
                        }
                    }
                }
            },
            "tiling": "ALIGNED [0:1023, 0:1023]"
        }
    }
}
```
