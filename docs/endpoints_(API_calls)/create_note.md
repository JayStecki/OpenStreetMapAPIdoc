<div class="grid cards" markdown>

- :material-target: **One of the main OpenStreetMap API usabilities**

</div>

Creates a new note for a specific geographic location, which allows administrators/users to verify map data (latitude `lat`, longitude `lon` and comment in `text` are required – check the example).

!!! note "If the request is made as an authenticated user, the note is associated with that user's account"
    If the OAuth access token used does not have the `allow_write_notes` permission, it is created as an anonymous note instead.

### Request

![](https://img.shields.io/badge/POST-blue)

```
/api/0.6/notes
```

| Latitude `lat` | Longitude `lon` | Message `text` |
| :---: | :---: | :---: |
| 50.8038794 | 16.2646154 | NazwaTerenuTo:OgródkidziałkoweMagnolia |

``` title="Example body request for new note for geographic point"
/api/0.6/notes?lat=50.8038794&lon=16.2646154&text=NazwaTerenuTo:OgródkidziałkoweMagnolia
```

### Response

![](https://img.shields.io/badge/Response-200%20OK-brightgreen)

``` xml title="newNoteForMapPoint_example.xml" linenums="1" hl_lines="3-17"
<?xml version="1.0" encoding="UTF-8"?>
<osm version="0.6" generator="OpenStreetMap server" copyright="OpenStreetMap and contributors" attribution="http://www.openstreetmap.org/copyright" license="http://opendatacommons.org/licenses/odbl/1-0/">
    <note lon="16.2646154" lat="50.8038794">
        <id>92059</id>
        <url>https://master.apis.dev.openstreetmap.org/api/0.6/notes/92059</url>
        <comment_url>https://master.apis.dev.openstreetmap.org/api/0.6/notes/92059/comment</comment_url>
        <close_url>https://master.apis.dev.openstreetmap.org/api/0.6/notes/92059/close</close_url>
        <date_created>2025-04-25 15:05:59 UTC</date_created>
        <status>open</status>
        <comments>
            <comment>
                <date>2025-04-25 15:05:59 UTC</date>
                <uid>22098</uid>
                <user>JayStecki</user>
                <user_url>https://master.apis.dev.openstreetmap.org/user/JayStecki</user_url>
                <action>opened</action>
                <text>NazwaTerenuTo:OgródkidziałkoweMagnolia</text>
                <html>&lt;p dir="auto"&gt;NazwaTerenuTo:OgródkidziałkoweMagnolia&lt;/p&gt;</html>
            </comment>
        </comments>
    </note>
</osm>
```

### Error codes

=== "400 (**Bad Request**)"
    If the **text field** was not present.
=== "404 (**Not Found**)"
    Requested resource could not be found (example: *Object not found*).