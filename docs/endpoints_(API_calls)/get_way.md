<div class="grid cards" markdown>

- :material-target: **One of the main OpenStreetMap API usability**.

</div>

Returns the XML representation of the element.

### Request

![](https://img.shields.io/badge/GET-green)

```
/api/0.6/way/{id}
```

### Response

![](https://img.shields.io/badge/Response-200%20OK-brightgreen)

``` xml linenums="1" hl_lines="3"
<?xml version="1.0" encoding="UTF-8"?>
<osm version="0.6" generator="openstreetmap-cgimap 2.0.1.2504141747 (1953646 faffy.openstreetmap.org)" copyright="OpenStreetMap and contributors" attribution="http://www.openstreetmap.org/copyright" license="http://opendatacommons.org/licenses/odbl/1-0/">
    <way id="123123" visible="true" version="1" changeset="7001" timestamp="2010-08-11T17:34:58Z" user="mbiker" uid="196">
        <nd ref="4245930"/>
        <nd ref="4245931"/>
        <nd ref="4245932"/>
        <nd ref="4245933"/>
        <nd ref="4245934"/>
        <nd ref="4245935"/>
        <nd ref="4245936"/>
        <nd ref="4245937"/>
        <nd ref="4245938"/>
        <nd ref="4245939"/>
        <nd ref="4245940"/>
        <nd ref="4245941"/>
        <nd ref="4245942"/>
        <nd ref="4245943"/>
        <nd ref="4245944"/>
        <nd ref="4245945"/>
        <nd ref="4245946"/>
        <nd ref="4245947"/>
        <nd ref="4245948"/>
        <nd ref="4245949"/>
        <nd ref="4245950"/>
        <nd ref="4245951"/>
        <nd ref="4245952"/>
        <nd ref="4245953"/>
        <nd ref="4245954"/>
        <nd ref="4245955"/>
        <nd ref="4245956"/>
        <nd ref="4245957"/>
        <nd ref="4245958"/>
        <nd ref="4245959"/>
        <nd ref="4245960"/>
        <nd ref="4245961"/>
        <nd ref="4245962"/>
        <nd ref="4245963"/>
        <nd ref="4245964"/>
        <nd ref="4245965"/>
        <nd ref="4245966"/>
        <nd ref="4245967"/>
        <nd ref="4245968"/>
        <nd ref="4245969"/>
        <nd ref="4245970"/>
        <nd ref="4245971"/>
        <nd ref="4245972"/>
        <nd ref="4245973"/>
        <nd ref="4245974"/>
        <nd ref="4245975"/>
        <nd ref="4245976"/>
        <nd ref="4245977"/>
        <nd ref="4245978"/>
        <nd ref="4245979"/>
        <nd ref="4245980"/>
        <nd ref="4245981"/>
        <nd ref="4245982"/>
        <nd ref="4245983"/>
        <nd ref="4245984"/>
        <nd ref="4245985"/>
        <nd ref="4245986"/>
        <nd ref="4245987"/>
        <nd ref="4245988"/>
        <nd ref="4245989"/>
        <nd ref="4245990"/>
        <nd ref="4245991"/>
        <nd ref="4245992"/>
        <nd ref="4245993"/>
        <nd ref="4245994"/>
        <nd ref="4245995"/>
        <nd ref="4245996"/>
        <nd ref="4245997"/>
        <nd ref="4245998"/>
        <nd ref="4245999"/>
        <nd ref="4246000"/>
        <nd ref="4246001"/>
        <tag k="accuracy:meters" v="10"/>
        <tag k="attribution" v="Natural Resources Canada"/>
        <tag k="oneway" v="yes"/>
        <tag k="source" v="GeobaseNHN_Import_2009"/>
        <tag k="waterway" v="stream"/>
        <tag k="waterway:type" v="observed"/>
    </way>
</osm>
```

### Error codes

=== "404 (**Not found**)"
    Requested resource could not be found.
=== "410 (**Gone**)"
    Requested content is permanently **deleted** from the server.