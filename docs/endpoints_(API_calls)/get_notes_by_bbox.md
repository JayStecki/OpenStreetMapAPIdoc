<div class="grid cards" markdown>

- :material-target: **One of the main OpenStreetMap API usability**.

</div>

Returns the existing notes in the specified [bounding box](get_api_map.md). The notes will be ordered by the date of their last change; the most recent one will be first. The list of notes can be returned in several different forms (for example as executable JavaScript, XML, RSS, json and GPX), depending on the file extension(1). The comment properties (uid, user, user_url) will be omitted if the comment was anonymous.
{ .annotate }

1. You can specify the format you want the results returned as by specifying a file extension.

??? info "JOSM, Vespucci and [^^Planet OSM^^](https://planet.openstreetmap.org/notes/){:target="_blank"} output differences."
    XML format returned by the API is different from the, equally undocumented format used for "osn" format files.

!!! note "Parameters need to call."
    | Parameter | Description | Default value | Allowed values |
    | :---: | --- | :---: | --- |
    | `bbox` | coordinates bounding the area | **none, parameter required** | Floating point numbers in degrees, expressing a valid bounding box `bbox`, not larger than the configured size limit (25 square degrees), not overlapping the dateline |
    | `limit` | number of entries returned | 100 | Between 1 and 10000 |
    | `closed` | number of days a note needs to be closed to no longer be returned | 7 | Value 0 means only open notes are returned / -1 means all notes are returned |

### Request

![](https://img.shields.io/badge/GET-green)

```
/api/0.6/notes?bbox=
```

| `bbox` | `limit` | `closed` |
| :---: | :---:| :---:|
| 14.182,49.969,19.011,51.839 | 3 | 5 |

``` title="Example note request"
/api/0.6/notes?bbox=14.182,49.969,19.011,51.839&limit=3&closed=5
```

### Response

![](https://img.shields.io/badge/Response-200%20OK-brightgreen)

``` xml linenums="1" hl_lines="14-74"
<?xml version="1.0" encoding="UTF-8"?>
<osm version="0.6" generator="OpenStreetMap server" copyright="OpenStreetMap and contributors" attribution="http://www.openstreetmap.org/copyright" license="http://opendatacommons.org/licenses/odbl/1-0/">
    <note lon="14.3922498" lat="50.0432752">
        <id>78907</id>
        <url>https://master.apis.dev.openstreetmap.org/api/0.6/notes/78907</url>
        <comment_url>https://master.apis.dev.openstreetmap.org/api/0.6/notes/78907/comment</comment_url>
        <close_url>https://master.apis.dev.openstreetmap.org/api/0.6/notes/78907/close</close_url>
        <date_created>2024-11-09 12:30:05 UTC</date_created>
        <status>open</status>
        <comments>
            <comment>
                <date>2024-11-09 12:30:05 UTC</date>
                <action>opened</action>
                <text>Odyseova cesta (climbing):

Suggested changes:
author=Lukáš Čermák, 2010


Submitted from https://osmapp.org/node/11660046022</text>
                <html>&lt;p dir="auto"&gt;Odyseova cesta (climbing):&lt;/p&gt;

&lt;p dir="auto"&gt;Suggested changes:
&lt;br /&gt;author=Lukáš Čermák, 2010&lt;/p&gt;

&lt;p dir="auto"&gt;Submitted from &lt;a href="https://osmapp.org/node/11660046022" rel="nofollow noopener noreferrer" dir="auto"&gt;https://osmapp.org/node/11660046022&lt;/a&gt;&lt;/p&gt;</html>
            </comment>
        </comments>
    </note>
    <note lon="14.3921871" lat="50.0432804">
        <id>78906</id>
        <url>https://master.apis.dev.openstreetmap.org/api/0.6/notes/78906</url>
        <comment_url>https://master.apis.dev.openstreetmap.org/api/0.6/notes/78906/comment</comment_url>
        <close_url>https://master.apis.dev.openstreetmap.org/api/0.6/notes/78906/close</close_url>
        <date_created>2024-11-09 12:29:33 UTC</date_created>
        <status>open</status>
        <comments>
            <comment>
                <date>2024-11-09 12:29:33 UTC</date>
                <action>opened</action>
                <text>Golem (climbing):

Suggested changes:
author=Emil Pohořelský, Lukáš Čermák, 2010


Submitted from https://osmapp.org/node/11660046021</text>
                <html>&lt;p dir="auto"&gt;Golem (climbing):&lt;/p&gt;

&lt;p dir="auto"&gt;Suggested changes:
&lt;br /&gt;author=Emil Pohořelský, Lukáš Čermák, 2010&lt;/p&gt;

&lt;p dir="auto"&gt;Submitted from &lt;a href="https://osmapp.org/node/11660046021" rel="nofollow noopener noreferrer" dir="auto"&gt;https://osmapp.org/node/11660046021&lt;/a&gt;&lt;/p&gt;</html>
            </comment>
        </comments>
    </note>
    <note lon="17.6666290" lat="51.5801754">
        <id>68803</id>
        <url>https://master.apis.dev.openstreetmap.org/api/0.6/notes/68803</url>
        <comment_url>https://master.apis.dev.openstreetmap.org/api/0.6/notes/68803/comment</comment_url>
        <close_url>https://master.apis.dev.openstreetmap.org/api/0.6/notes/68803/close</close_url>
        <date_created>2024-08-11 07:15:51 UTC</date_created>
        <status>open</status>
        <comments>
            <comment>
                <date>2024-08-11 07:15:51 UTC</date>
                <uid>20836</uid>
                <user>SchweizerFahrer</user>
                <user_url>https://master.apis.dev.openstreetmap.org/user/SchweizerFahrer</user_url>
                <action>opened</action>
                <text>Droga już jest otwarta

#OsmAnd</text>
                <html>&lt;p dir="auto"&gt;Droga już jest otwarta&lt;/p&gt;

&lt;p dir="auto"&gt;#OsmAnd&lt;/p&gt;</html>
            </comment>
        </comments>
    </note>
</osm>
```

### Error codes

=== "400 (**Bad Request**)"
    When any of the limits are crossed (example: *Note limit must be between 1 and 10000*).