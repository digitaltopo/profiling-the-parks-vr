# profiling-the-parks-vr
VR version of [Profiling the Parks](http://infowetrust.com/parks/) powered by the [A-Frame](https://aframe.io/) VR framework.

Based on [RJ Andrews's](https://twitter.com/infowetrust) vizualization [Profiling the Parks](http://infowetrust.com/parks/), a data-driven, hand drawn exploration of the US National Parks. 

## Methodology

1. Get [digital elevation model](https://en.wikipedia.org/wiki/Digital_elevation_model) (DEM) data for featured National Parks
1. Create an AOI in [QGIS](http://www.qgis.org) or [GeoJSON.io](http://geojson.io)
1. Crop the DEM data file to an area of interest (AOI) in QGIS
1. Get visual imagery to use for texture ([PlanetScope 3-band scene](https://www.planet.com/products/satellite-imagery/files/Planet_Imagery_Product_Specs.pdf)
	* Merge the imagery in QGIS or using GDAL (gdal_merge, gdal_warp, gdal vrt) if single scene doesn't fill aoi
1. Restart QGIS whenever it crashes
1. Crop the visual imagery to the aoi
1. Save as a jpg/png
1. Use [lunapic](https://www194.lunapic.com/editor/?action=sketch&style=sketch2&redo=1&colorset=1) for crayon/drawing effect

## DEM Resources

* [NASADEM](https://earthdata.nasa.gov/community/community-data-system-programs/measures-projects/nasadem)

#### DEM Sensors

* [ASTER](https://asterweb.jpl.nasa.gov/gdem.asp) - NASA's Advanced Spaceborne Thermal Emission and Reflection Radiometer

#### DEM Data Sources
* [USGS National Map](https://nationalmap.gov/)
	* [National Map Elevation Data](https://nationalmap.gov/elevation.html)
	* [USGS National Map 3DEP Viewer](https://viewer.nationalmap.gov/basic/?basemap=b1&category=ned,nedsrc&title=3DEP%20View) 
* [USGS Earth Explorer](https://earthexplorer.usgs.gov/)
* [NASA EarthData Global Data Explorer](https://earthdata.nasa.gov/)
* [NASA Reverb | Echo](https://reverb.echo.nasa.gov/) - NASA's Earth Observing System Data and Information System program next generation Earth science discovery tool


## Tutorials & Resources

* [Discovering Gale Crater: How we did it](http://graphics.latimes.com/mars-gale-crater-how-we-did-it/)
* [Terrain building with three.js](http://blog.mastermaps.com/2013/10/terrain-building-with-threejs.html)
	* [Converting terrain data to a WebGL-friendly format](http://blog.mastermaps.com/2013/10/terrain-building-with-threejs-part-1.html?m=1)
* [A Gentle Introduction to GDAL](https://medium.com/planet-stories/a-gentle-introduction-to-gdal-part-1-a3253eb96082)

### Useful Commands

#### GDAL

* [gdalinfo](http://www.gdal.org/gdalinfo.html) `gdalinfo -mm {FILENAME}`
* [gdal_translate](http://www.gdal.org/gdal_translate.html) to [ENVI file](https://www.harrisgeospatial.com/docs/ENVIImageFiles.html): `gdal_translate -scale 0 2470 0 65535 -ot UInt16 -outsize 200 200 -of ENVI {INPUT.tif} {OUTPUT.bin}`
* [gdalwarp](https://trac.osgeo.org/gdal/wiki/UserDocs/GdalWarp) `gdalwarp {INPUT1.tif} {INPUT2.tif} {MERGED.tif}`