Returns the permissions granted to the current API connection.

- If the API client is not authorized, an empty list of permissions will be returned.
- If the API client uses OAuth 2.0, the list will be based on the granted scopes.
<div class="annotate" markdown>
- For previously available Basic Auth, the list of permissions contained all permissions(1).
</div>

1. Basic Auth was removed in June 2024.

## Request

![](https://img.shields.io/badge/GET-green)

```
/api/0.6/permissions
```

## Response

![](https://img.shields.io/badge/Response-200%20OK-brightgreen)

``` xml linenums="1"
<?xml version="1.0" encoding="UTF-8"?>
<osm version="0.6" generator="OpenStreetMap server" copyright="OpenStreetMap and contributors" attribution="http://www.openstreetmap.org/copyright" license="http://opendatacommons.org/licenses/odbl/1-0/">
    <permissions>
  </permissions>
</osm>
```
## Additional

??? info "Currently following permissions corresponding to the older ones."
    | OAuth 2.0 | OAuth 1.0 |
    | :---: | :---: |
    | `allow_read_prefs` | ==read user preferences== |
    | `allow_read_prefs` | ==modify user preferences== |
    | `allow_write_diary` | ==allow_write_diary== |
    | `allow_write_api` | ==modify the map== |
    | `allow_write_changeset_comments` | ==comment on changesets== |
    | `allow_write_redactions` | ==redact element versions== |
    | `allow_read_gpx` | ==read private GPS traces== |
    | `allow_write_gpx` | ==upload GPS traces== |
    | `allow_write_notes` | ==modify notes== |