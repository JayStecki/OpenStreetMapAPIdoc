<div class="grid cards" markdown>

- :material-target: **One of the main OpenStreetMap API usabilities**

</div>

The following command returns:

- All nodes that are inside a given [bounding box](../general_information/bounding_box.md) and any relations that reference them.
- All ways that reference at least one node that is inside a given bounding box, any relations that reference them (the ways), and any nodes outside the bounding box that the ways may reference.
- All relations that reference one of the nodes, ways or relations included due to the above rule (does not apply recursively).

## Request

![](https://img.shields.io/badge/GET-green)

```
/api/0.6/map?bbox=
```

| Left (longitude ) | Bottom (latitude) | Rigt (longitude) | Top (latitude) |
| :---: | :---:| :---:| :---: |
| 100 | 50 | 100 | 50 |

``` title="Example bounding box request"
/api/0.6/map?bbox=100,50,100,50
```

## Response

![](https://img.shields.io/badge/Response-200%20OK-brightgreen)

``` xml linenums="1" hl_lines="3"
<?xml version="1.0" encoding="UTF-8"?>
<osm version="0.6" generator="openstreetmap-cgimap 2.0.1.2504041438 (3164272 faffy.openstreetmap.org)" copyright="OpenStreetMap and contributors" attribution="http://www.openstreetmap.org/copyright" license="http://opendatacommons.org/licenses/odbl/1-0/">
    <bounds minlat="50.0000000" minlon="100.0000000" maxlat="50.0000000" maxlon="100.0000000"/>
    <node id="3199343" visible="true" version="1" changeset="3750" timestamp="2010-04-27T21:37:49Z" user="Melaskia" uid="129" lat="50.0000000" lon="100.0000000">
        <tag k="amenity" v="test"/>
    </node>
    <node id="3199344" visible="true" version="1" changeset="3751" timestamp="2010-04-27T21:42:11Z" user="Melaskia" uid="129" lat="50.0000000" lon="100.0000000">
        <tag k="amenity" v="test"/>
    </node>
    <node id="3199345" visible="true" version="1" changeset="3753" timestamp="2010-04-27T21:43:46Z" user="Melaskia" uid="129" lat="50.0000000" lon="100.0000000">
        <tag k="amenity" v="test"/>
    </node>
</osm>
```

## Error codes

=== "400 (**Bad Request**)"
    The latitudes must be between -90 and 90, longitudes between -180 and 180 and the minima must be less than the maxima (example: *The maximum bbox size is 0.250000, and your request was too large. Either request a smaller area, or use planet.osm*).
=== "509 (**Bandwidth Limit Exceeded**)"
    Error: You have downloaded too much data. Please try again later.