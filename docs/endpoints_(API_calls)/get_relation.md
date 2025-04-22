<div class="grid cards" markdown>

- :material-target: **One of the main OpenStreetMap API usability**.

</div>

Returns the XML representation of the element.

### Request

![](https://img.shields.io/badge/GET-green)

```
/api/0.6/relation/{id}
```

### Response

![](https://img.shields.io/badge/Response-200%20OK-brightgreen)

``` xml linenums="1" hl_lines="3"
<?xml version="1.0" encoding="UTF-8"?>
<osm version="0.6" generator="openstreetmap-cgimap 2.0.1.2504141747 (1953645 faffy.openstreetmap.org)" copyright="OpenStreetMap and contributors" attribution="http://www.openstreetmap.org/copyright" license="http://opendatacommons.org/licenses/odbl/1-0/">
    <relation id="131" visible="true" version="1" changeset="400" timestamp="2009-09-15T21:14:20Z" user="green525" uid="12">
        <member type="way" ref="5240" role="outer"/>
        <member type="way" ref="5241" role="outer"/>
        <member type="way" ref="5242" role="outer"/>
        <member type="way" ref="5243" role="outer"/>
        <member type="way" ref="5244" role="outer"/>
        <member type="way" ref="5245" role="outer"/>
        <member type="way" ref="5246" role="outer"/>
        <tag k="admin_level" v="9"/>
        <tag k="alt_name" v="Vastse-Roosa"/>
        <tag k="boundary" v="administrative"/>
        <tag k="EHAK:code" v="9131"/>
        <tag k="EHAK:countycode" v="0086"/>
        <tag k="EHAK:parishcode" v="0493"/>
        <tag k="is_in" v="Mõniste vald"/>
        <tag k="name" v="Vastse-Roosa küla"/>
        <tag k="type" v="multipolygon"/>
    </relation>
</osm>
```

### Error codes

=== "404 (**Not found**)"
    Requested resource could not be found.
=== "410 (**Gone**)"
    Requested content is permanently **deleted** from the server.