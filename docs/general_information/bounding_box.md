Becasue OSM API calls refer to [^^geographic data on maps^^](https://wiki.openstreetmap.org/wiki/Changeset#Geographical_size_of_changesets){:target="blank"}, most calls must have a frame around them. A bounding box (**bbox**) is just such a form of border around the map area where the call occurs. Is defined by two longitudes and two latitudes, where:

- Latitude is a decimal number between -90.0 and 90.0.
- Longitude is a decimal number between -180.0 and 180.0.

They usually follow the standard format of:

- bbox=left,bottom,right,top
- bbox = min Longitude, min Latitude, max Longitude, max Latitude

Let's consider example API call (refers to the Greater London area):

![](https://img.shields.io/badge/GET-green)

```
/api/0.6/map?bbox=left,bottom,right,top
```

```
/api/0.6/map?bbox=51.2867602,51.6918741,-0.5103751,0.3340155
```

Where:

- **Left** is the longitude of the left (westernmost) side of the bounding box.
- **Bottom** is the latitude of the bottom (southernmost) side of the bounding box.
- **Right** is the longitude of the right (easternmost) side of the bounding box.
- **Top** is the latitude of the top (northernmost) side of the bounding box.

!!! note "Bounding box `bbox` explanation"
    While this command returns those relations that reference the aforementioned nodes and ways, the reverse is not true: it does not (necessarily) return all of the nodes and ways that are referenced by these relations (this prevents unreasonably-large result sets).
    ??? example "Case example"
        For example, imagine the case where there is a relation named "England" that references every node in England. The nodes, ways, and relations are retrieved for a bounding box that covers a small portion of England. While the result would include the nodes, ways, and relations as specified by the rules for the command, including the "England" relation, it would (fortuitously) not include every node and way in England. If desired, the nodes and ways referenced by the "England" relation could be retrieved by their respective IDs. Also note that ways which intersect the bounding box but have no nodes within the bounding box will not be returned.

## Visually defining a bounding box

Several utilities have been created by the community to provide a graphical interface for selecting a bounding box on a reference map:

- [^^Bbox tool^^](https://norbertrenner.de/osm/bbox.html){:target="blank"} by Norbert Renner.
- [^^Bounding box tool^^](https://boundingbox.klokantech.com/){:target="blank"} by Klokan Technologies.
- [^^XAPI Query Builder^^](https://harrywood.co.uk/maps/uixapi/){:target="blank"} by Harry Wood.

You can also just use the OpenStreetMap website – following the instruction specified at the OSM [^^page^^](https://wiki.openstreetmap.org/wiki/Bounding_box){:target="blank"} reffered to bounding box.