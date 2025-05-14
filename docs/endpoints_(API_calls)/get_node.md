<div class="grid cards" markdown>

- :material-target: **One of the main OpenStreetMap API usabilities**

</div>

Returns the XML representation of the [node element](../general_information/elements.md#elements-description). The node ID `id` is required.

### Request

![](https://img.shields.io/badge/GET-green)

```
/api/0.6/node/{id}
```

``` title="Example node request"
/api/0.6/node/4359470504
```

### Response

![](https://img.shields.io/badge/Response-200%20OK-brightgreen)

``` xml linenums="1" hl_lines="3-6"
<?xml version="1.0" encoding="UTF-8"?>
<osm version="0.6" generator="openstreetmap-cgimap 2.0.1.2504221729 (3523567 faffy.openstreetmap.org)" copyright="OpenStreetMap and contributors" attribution="http://www.openstreetmap.org/copyright" license="http://opendatacommons.org/licenses/odbl/1-0/">
    <node id="4359470504" visible="true" version="1" changeset="412384" timestamp="2025-04-23T11:36:48Z" user="JayStecki" uid="22098" lat="50.8038794" lon="16.2646154">
        <tag k="amenity" v="garden"/>
        <tag k="name" v="Node for a plot in the ROD-Association garden"/>
    </node>
</osm>
```

### Error codes

=== "404 (**Not Found**)"
    When no element with the given ID could be found (example: *Requested resource could not be found*).
=== "410 (**Gone**)"
    If the element has been deleted (example: *Requested content is permanently deleted from the server*).