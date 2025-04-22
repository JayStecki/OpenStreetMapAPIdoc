<div class="grid cards" markdown>

- :material-target: **One of the main OpenStreetMap API usability**.

</div>

Returns the existing notes in the specified ==[bounding box](get_api_map.md)==. The notes will be ordered by the date of their last change, the most recent one will be first. The list of notes can be returned in several different forms (e.g. as executable JavaScript, XML, RSS, json and GPX) depending on the file extension(1). The comment properties [uid, user, user_url] will be omitted if the comment was anonymous.
{ .annotate }

1. You can specify the format you want the results returned as - by specifying a file extension.

??? info "JOSM, Vespucci and [^^Planet OSM^^](https://planet.openstreetmap.org/notes/){:target="_blank"} output differences."
    XML format returned by the API is different from the, equally undocumented, format used for "osn" format files.

!!! note "Parameters need to call."
    | Parameter | Description | Default value | Allowed values |
    | :---: | --- | :---: | --- |
    | `bbox` | coordinates bounding the area | **none, parameter required** | floating point numbers in degrees, expressing a valid ==bounding box==, not larger than the configured size limit (25 square degrees), not overlapping the dateline |
    | `limit` | number of entries returned | 100 | between 1 and 10000 |
    | `closed` | number of days a note needs to be closed to no longer be returned | 7 | 0 means only open notes are returned / -1 means all notes are returned |

### Request

![](https://img.shields.io/badge/GET-green)

```
/api/0.6/notes?bbox=
```

Example data:

| `bbox` | `limit` | `closed` |
| :---: | :---:| :---:|
| 0.10,51,0.10,51 | 1 | 2 |

![](https://img.shields.io/badge/GET-green)

``` title="Example call"
/api/0.6/notes?bbox=0.10,51,0.10,51&limit=1&closed=2
```

### Response

![](https://img.shields.io/badge/Response-200%20OK-brightgreen)

``` xml linenums="1" hl_lines="14"
<?xml version="1.0" encoding="UTF-8"?>
<osm version="0.6" generator="OpenStreetMap server" copyright="OpenStreetMap and contributors" attribution="http://www.openstreetmap.org/copyright" license="http://opendatacommons.org/licenses/odbl/1-0/">
    <note lon="0.1000000" lat="51.0000000">
        <id>86316</id>
        <url>https://master.apis.dev.openstreetmap.org/api/0.6/notes/86316</url>
        <comment_url>https://master.apis.dev.openstreetmap.org/api/0.6/notes/86316/comment</comment_url>
        <close_url>https://master.apis.dev.openstreetmap.org/api/0.6/notes/86316/close</close_url>
        <date_created>2025-02-05 10:12:49 UTC</date_created>
        <status>open</status>
        <comments>
            <comment>
                <date>2025-02-05 10:12:49 UTC</date>
                <action>opened</action>
                <text>noteTest</text>
                <html>&lt;p dir="auto"&gt;noteTest&lt;/p&gt;</html>
            </comment>
        </comments>
    </note>
</osm>
```

### Error codes

=== "400 (**Bad request**)"
    When any of the limits are crossed (note limit must be between 1 and 10000).