<div class="grid cards" markdown>

- :material-target: **One of the main OpenStreetMap API usability**.

</div>

Returns the XML representation of the way element. Way ==ID== is required.

### Request

![](https://img.shields.io/badge/GET-green)

```
/api/0.6/way/{id}
```

### Response

![](https://img.shields.io/badge/Response-200%20OK-brightgreen)

``` xml linenums="1" hl_lines="3-8"
<?xml version="1.0" encoding="UTF-8"?>
<osm version="0.6" generator="openstreetmap-cgimap 2.0.1.2504221729 (3523571 faffy.openstreetmap.org)" copyright="OpenStreetMap and contributors" attribution="http://www.openstreetmap.org/copyright" license="http://opendatacommons.org/licenses/odbl/1-0/">
    <way id="4307240014" visible="true" version="1" changeset="412389" timestamp="2025-04-23T13:48:42Z" user="JayStecki" uid="22098">
        <nd ref="4359470504"/>
        <nd ref="4359471036"/>
        <tag k="highway" v="footway"/>
        <tag k="JayStecki" v="Boundary for a plot in the ROD-Association garden"/>
    </way>
</osm>
```

### Error codes

=== "404 (**Not found**)"
    When no element with the given ID could be found (*Requested resource could not be found*).
=== "410 (**Gone**)"
    If the element has been **deleted** (*Requested content is permanently deleted from the server*).