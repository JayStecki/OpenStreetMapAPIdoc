<div class="grid cards" markdown>

- :material-target: **One of the main OpenStreetMap API usability**.

</div>

Returns the XML representation of the element.

### Request

![](https://img.shields.io/badge/GET-green)

```
/api/0.6/node/{id}
```

### Response

![](https://img.shields.io/badge/Response-200%20OK-brightgreen)

``` xml linenums="1" hl_lines="3"
<?xml version="1.0" encoding="UTF-8"?>
<osm version="0.6" generator="openstreetmap-cgimap 2.0.1.2504141747 (1953647 faffy.openstreetmap.org)" copyright="OpenStreetMap and contributors" attribution="http://www.openstreetmap.org/copyright" license="http://opendatacommons.org/licenses/odbl/1-0/">
    <node id="123123" visible="true" version="1" changeset="310" timestamp="2009-09-15T01:09:39Z" user="green525" uid="12" lat="58.3170981" lon="21.9303157"/>
</osm>
```

### Error codes

=== "404 (**Not found**)"
    Requested resource could not be found.
=== "410 (**Gone**)"
    Requested content is permanently **deleted** from the server.