Returns the permissions granted to the current API connection.

- If the API client is not authorized, an empty list of permissions will be returned.
- If the API client uses OAuth 2.0, the list will be based on the granted scopes.
<div class="annotate" markdown>
- For previously available Basic Auth, the list of permissions contained all permissions(1).
</div>

1. Basic Auth was removed in June 2024.

## Request

**`GET`** `/api/0.6/permissions`

## Response

Returns the single permissions element containing the permission tags (content type ==application/json==).

``` json title="apiPermission_example.json" linenums="1" hl_lines="4"
{
 "version": "0.6",
 "generator": "OpenStreetMap server",
 "permissions": ["allow_read_prefs", ..., "allow_read_gpx", "allow_write_gpx"]
}
```

??? note "Currently following permissions corresponding to the deprecated ones."
    | OAuth 2.0 | OAuth 1.0 |
    | --- | --- |
    | `allow_read_prefs` | ==read user preferences== |
    | `allow_read_prefs` | ==modify user preferences== |
    | `allow_write_diary` | ==allow_write_diary== |
    | `allow_write_api` | ==modify the map== |
    | `allow_write_changeset_comments` | ==comment on changesets== |
    | `allow_write_redactions` | ==redact element versions== |
    | `allow_read_gpx` | ==read private GPS traces== |
    | `allow_write_gpx` | ==upload GPS traces== |
    | `allow_write_notes` | ==modify notes== |