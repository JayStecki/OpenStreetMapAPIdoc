<div class="grid cards" markdown>

- :material-target: **One of the main OpenStreetMap API usability**.

</div>

Returns an XML document with the home location and the `display_name` of the **logged-in user**.

### Request

![](https://img.shields.io/badge/GET-green)

```
/api/0.6/user/details
```

### Response

![](https://img.shields.io/badge/Response-200%20OK-brightgreen)

``` xml linenums="1" hl_lines="3"
<?xml version="1.0" encoding="UTF-8"?>
<osm version="0.6" generator="OpenStreetMap server" copyright="OpenStreetMap and contributors" attribution="http://www.openstreetmap.org/copyright" license="http://opendatacommons.org/licenses/odbl/1-0/">
    <user id="22098" display_name="JayStecki" account_created="2025-04-22T12:01:23Z">
        <description></description>
        <contributor-terms agreed="true" pd="false"/>
        <img href="https://master.apis.dev.openstreetmap.org/rails/active_storage/representations/redirect/eyJfcmFpbHMiOnsiZGF0YSI6MjUzOCwicHVyIjoiYmxvYl9pZCJ9fQ==--814f0f2f9339174fd575cddf4712700b14608c53/eyJfcmFpbHMiOnsiZGF0YSI6eyJmb3JtYXQiOiJwbmciLCJyZXNpemVfdG9fbGltaXQiOlsxMDAsMTAwXX0sInB1ciI6InZhcmlhdGlvbiJ9fQ==--32ac28fb572ae93b1714c8abd2474f71fba86c73/AVATAR_gitHub_JS2.png"/>
        <roles>
  </roles>
        <changesets count="0"/>
        <traces count="0"/>
        <blocks>
            <received count="0" active="0"/>
        </blocks>
        <home lat="50.805491" lon="16.260287" zoom="3"/>
        <languages>
            <lang>pl</lang>
            <lang>en-US</lang>
            <lang>en</lang>
        </languages>
        <messages>
            <received count="0" unread="0"/>
            <sent count="0"/>
        </messages>
    </user>
</osm>
```

### Error codes

=== "401 (**Unauthorized**)"
    The request is unauthenticated (Couldn't authenticate you).