<div class="grid cards" markdown>

- :material-target: **One of the main OpenStreetMap API usability**.

</div>

The following command returns:

- all nodes that are inside a given ==bounding box== and any relations that reference them.
- All ways that reference at least one node that is inside a given ==bounding box==, any relations that reference them (the ways), and any nodes outside the ==bounding box== that the ways may reference.
- All relations that reference one of the nodes, ways or relations included due to the above rule (does not apply recursively).

GET/api/0.6/map?==bbox=left,bottom,right,top== - where:

- **Left** is the longitude of the left (westernmost) side of the ==bounding box==.
- **Bottom** is the latitude of the bottom (southernmost) side of the ==bounding box==.
- **Right** is the longitude of the right (easternmost) side of the ==bounding box==.
- **Top** is the latitude of the top (northernmost) side of the ==bounding box==.

!!! note "Bounding box `bbox` explanation"
    While this command returns those relations that reference the aforementioned nodes and ways, the reverse is not true: it does not (necessarily) return all of the nodes and ways that are referenced by these relations (this prevents unreasonably-large result sets).
    ??? example "Case example"
        For example, imagine the case where there is a relation named "England" that references every node in England. The nodes, ways, and relations are retrieved for a bounding box that covers a small portion of England. While the result would include the nodes, ways, and relations as specified by the rules for the command, including the "England" relation, it would (fortuitously) not include every node and way in England. If desired, the nodes and ways referenced by the "England" relation could be retrieved by their respective IDs. Also note that ways which intersect the bounding box but have no nodes within the bounding box will not be returned.

## Request

==Bounding box== data:

| Left (longitude ) | Bottom (latitude) | Rigt (longitude) | Top (latitude) |
| :---: | :---:| :---:| :---: |
| 100 | 50 | 100 | 50 |

![](https://img.shields.io/badge/GET-green)

```
/api/0.6/map?bbox=100,50,100,50
```

## Response

![](https://img.shields.io/badge/Response-200%20OK-brightgreen)

``` xml linenums="1"
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

=== "400 (**Bad request**)"
    The ==latitudes== must be between -90 and 90, ==longitudes== between -180 and 180 and the **minima must be less than the maxima**.