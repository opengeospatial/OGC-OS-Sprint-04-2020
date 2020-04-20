# Shared Datasets

NOTE: Only upload datasets that you have licence to share.

## Ordnance Survey data

OS Open ZoomStack, https://os.uk/business-government/products/open-zoomstack; https://osdatahub.os.uk/downloads/OpenZoomStack

## OGC Vector Tiles Pilot, Phase 2 data

The following are GeoPackage files containing vector tiles data (from the OGC Vector Tiles Pilot, Phase 2 project). Any questions about the files should be directed to @jyutzler :

* https://portal.ogc.org/files/?artifact_id=92623 (108 MB)
* https://portal.ogc.org/files/?artifact_id=92155 (278 MB)

The files were created by harvesting tiles from multiple implementations of OGC API - Tiles.

The following are additional GeoPackage files from Vector Tiles Pilot - Phase 2 demonstrating various capabilities (e.g. attributes table vs. embedded attributes, single vs. multiple layers per tiles, different encodings, R-Tree spatial indexes). 
All examples contain Topographic Data Store profile of OpenStreetMap using Vector Tiles Extensions ( https://gitlab.com/imagemattersllc/ogc-vtp2/-/tree/master/extensions ), also including separate portrayal information in different styles, as well as two DTED Level 1 cells of Daraa, Syria (using tiled gridded coverage extension: http://docs.opengeospatial.org/is/17-066r1/17-066r1.html ). All tile matrix sets are described at http://maps.ecere.com/geoapi/tileMatrixSets .
Any questions about the files should be directed to @jerstlouis :

Mapbox Vector Tiles

* WebMercatorQuad (Embedded attributes, MultiLayer), https://portal.ogc.org/files/?artifact_id=93067
* WorldCRS84Quad (Embedded attributes, MultiLayer), https://portal.ogc.org/files/?artifact_id=92592

* WebMercatorQuad (Attributes table, MultiLayer), https://portal.ogc.org/files/?artifact_id=92567
* WorldCRS84Quad (Attributes table, MultiLayer), https://portal.ogc.org/files/?artifact_id=92566
* WorldMercatorWGS84Quad (Attributes table, MultiLayer), https://portal.ogc.org/files/?artifact_id=92568
* GNOSISGlobalGrid (Attributes table, MultiLayer), https://portal.ogc.org/files/?artifact_id=92565

* WebMercatorQiad (Attributes table, OneLayerPerTile), https://portal.ogc.org/files/?artifact_id=92571
* WorldCRS84Quad (Attributes table, OneLayerPerTile), https://portal.ogc.org/files/?artifact_id=92570
* WorldMercatorWGS84Quad (Attributes table, OneLayerPerTile), https://portal.ogc.org/files/?artifact_id=92572
* GNOSISGlobalGrid (Attributes table, OneLayerPerTile), https://portal.ogc.org/files/?artifact_id=92569

GeoJSON

* WebMercatorQuad (GeoJSON, Attributes table, OneLayerPerTile) https://portal.ogc.org/files/?artifact_id=93070
* WorldCRS84Quad (GeoJSON, Attributes table, OneLayerPerTile) https://portal.ogc.org/files* /?artifact_id=93071
* WebMercatorQuad0 (GeoJSON, Embedded attributes, OneLayerPerTile), https://portal.ogc.org/files/?artifact_id=93069
* WorldCRS84Quad (GeoJSON, Embedded attributes, OneLayerPerTile), https://portal.ogc.org/files/?artifact_id=93068

GNOSIS Map Tiles ( http://docs.opengeospatial.org/per/18-025.html#GMTSpecs )

* GNOSISGlobalGrid (GNOSIS Map Tiles, OneLayerPerTile) https://portal.ogc.org/files/?artifact_id=93072
