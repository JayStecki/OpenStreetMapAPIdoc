Returns a list of available API versions supported by this instance.

## Request

![](https://img.shields.io/badge/GET-green)

```
/api/versions
```

## Response

![](https://img.shields.io/badge/Response-200%20OK-brightgreen)

``` xml linenums="1"
<?xml version="1.0" encoding="UTF-8"?>
<osm generator="OpenStreetMap server" copyright="OpenStreetMap and contributors" attribution="http://www.openstreetmap.org/copyright" license="http://opendatacommons.org/licenses/odbl/1-0/">
    <api>
        <version>0.6</version>
    </api>
</osm>
```