## Screenshots

This folder shows screenshots of implementations on:

* Hexagon Geospatial - [LuciadLightspeed](https://www.hexagongeospatial.com/products/luciad-portfolio/luciadlightspeed)
* Ecere - [GNOSIS Map Server](http://ecere.ca/gnosis/)


### OGC API - Tiles on LuciadLightspeed by Hexagon Geospatial

### EPSG:27700 TileMatrixSet

![LuciadLightspeed OGC API - Tiles EPSG:27700 TileMatrixSet](./Hexagon/Luciad_ogc_api_tiles_epsg27700_tilematrixset_screenshot.png)

Image contains Ordnance Survey data © Crown copyright and database rights 2020

### Time and Altitude Dimensions

![LuciadLightspeed OGC API - Tiles Time and Altitude Dimensions](./Hexagon/Luciad_ogc_api_tiles_time_and_altitude_dimensions_screenshot.png)

### Time Dimension

![LuciadLightspeed OGC API - Tiles Time Dimension](./Hexagon/Luciad_ogc_api_tiles_time_dimension_screenshot.png)

### Ecere's 3D client driving tile-based contours generation process on GNOSIS Map Server

#### Worldwide elevation contours at 500 meters (vector tiles)

![Tiled Distributed/Client-driven Process Workflow - Elevation Contours (World)](./Ecere/ecere-tiles-process-contours-world.png)

#### Worldwide elevation contours at 500 meters in the Himalayas (vector tiles)

![Tiled Distributed/Client-driven Process Workflow - Elevation Contours (Himalayas)](./Ecere/ecere-tiles-process-contours-himalayas.png)

#### Daraa, Syria elevation contours at 250 and 50 meters (vector tiles)

![Ecere Tiled Distributed/Client-driven Process Workflow - Elevation Contours (Daraa)](./Ecere/ecere-tiles-process-contours-daraa.png)

#### Sample process execution

This process execution document instructs to render a map including contours, roads and a route.
The contours and route are computed on-the-fly using the _ElevationContours_ and _OSMEcereRoutingEngine_ processes (using Open Routing API).

```json
{
   "id" : "ContoursRoadsAndRouteMap",
   "process" : "https://maps.ecere.com/processes/RenderMap",
   "inputs" : [
      {
         "id" : "Contours250",
         "process" : "https://maps.ecere.com/processes/ElevationContours",
         "inputs" : [
            { "collection" : "https://maps.ecere.com/collections/vtp/Daraa2/Daraa_DTED" }
         ],
         "parameters" : { "distance" : 250 }
      },
      { "collection" : "https://maps.ecere.com/collections/vtp/Daraa2/TransportationGroundCrv" },
      {
         "id" : "MyRoute",
         "process" : "https://maps.ecere.com/processes/OSMEcereRoutingEngine",
         "inputs" : [
            { "collection" : "https://maps.ecere.com/collections/vtp/Daraa2/TransportationGroundCrv" }
         ],
         "parameters" :
         {
            "waypoints": {
               "type": "MultiPoint",
               "coordinates": [
                  [ 36.00210415, 32.54581061 ],
                  [ 36.11221587, 32.67020983 ]
               ]
            }
         }
      }
   ],
   "parameters" : { "style" : "night" }
}
```

Five ways this could be used:

- POST to {process} (e.g. /processes/RenderMap aka /map, or to /processes/ElevationContours) to retrieve output of process (e.g. GeoTIFF, GeoJSON, PNG). Sync or async. Optionally include BBOX, width & height.
- POST to {process}/tiles (e.g. /processes/RenderMap/tiles aka /map/tiles, or to /processes/ElevationContours/tiles) to retrieve tiles template and tileMatrixLink. If a {TileMatrixSetId} is included in the target resource URL, only get templates and links for that one TMS.
- POST to root /tiles (using process or collection(s) specified in JSON) to retrieve tiles template and tileMatrixSetLinks
- POST to /collections to create new _virtual collection_ (for most intents and purposes, same as normal collection)
- GET /collections/{collectionID}/sourceExecution to retrieve execution document from virtual collection


### OGC API - Tiles with OpenLayers

![OGC API - Tiles in OpenLayers](./OpenLayers/map-tiles.gif)

The [draft pull request](https://github.com/openlayers/openlayers/pull/10963) adds support for an `OGCMapTile` source for OpenLayers.  This works with services that implement the map tiles portion of the spec provided that they make their metadata (tiles info, tile matrix set definitions, etc.) [CORS-friendly](https://enable-cors.org/).  In addition, services should be available via HTTPS to avoid being blocked by browsers due to mixed content.  (Unfortunately, resources like http://schemas.opengis.net/tms/1.0/json/examples/WebMercatorQuad.json satisfy neither of these conditions.)

After the spec has settled a bit, this and support for vector tiles will be available in a release of the library.
