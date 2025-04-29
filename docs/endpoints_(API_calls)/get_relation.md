<div class="grid cards" markdown>

- :material-target: **One of the main OpenStreetMap API usability**.

</div>

Returns the XML representation of the relation element. Relation ==ID== is required.

### Request

![](https://img.shields.io/badge/GET-green)

```
/api/0.6/relation/{id}
```

### Response

![](https://img.shields.io/badge/Response-200%20OK-brightgreen)

``` xml linenums="1" hl_lines="3-7"
<?xml version="1.0" encoding="UTF-8"?>
<osm version="0.6" generator="openstreetmap-cgimap 2.0.1.2504221729 (3523566 faffy.openstreetmap.org)" copyright="OpenStreetMap and contributors" attribution="http://www.openstreetmap.org/copyright" license="http://opendatacommons.org/licenses/odbl/1-0/">
    <relation id="4305233945" visible="true" version="1" changeset="412389" timestamp="2025-04-23T15:01:12Z" user="JayStecki" uid="22098">
        <member type="way" ref="4307240014" role="outer"/>
        <member type="way" ref="4307240017" role="outer"/>
        <tag k="landuse" v="garden"/>
        <tag k="type" v="multipolygon"/>
    </relation>
</osm>
```

### Error codes

=== "404 (**Not Found**)"
    Requested resource could not be found.
=== "410 (**Gone**)"
    Requested content is permanently deleted from the server.