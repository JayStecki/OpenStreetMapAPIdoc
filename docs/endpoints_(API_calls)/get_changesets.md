<div class="grid cards" markdown>

- :material-target: **One of the main OpenStreetMap API usabilities**

</div>

A method for getting a list of [changesets](../general_information/changesets.md), that supports filtering by different criteria. Only changesets by public users are returned (returns at most 100 changesets).

??? info "For multiple queries, the results will match all of the requirements"  
    The contents of the returned document are the changesets and their tags. To get the full set of changes associated with a changeset, use the download method on each changeset ID individually. Modification and extension of the basic queries above may be required to support rollback and other uses we find for changesets.

!!! note "Parameters to specify the criteria"
    | Parameter | Syntax | Description |
    | :---: | :---: | :---: |
    | `bbox` | min_lon,min_lat,max_lon,max_lat | Finds changesets within the given [bounding box](../general_information/bounding_box.md) |
    | `user` or `display_name` | #uid / #name | Finds changesets by the user with the given user ID or display name (**providing both is an error**) |
    | `time` | T1 / T1,T2 | Finds changesets closed after T1 / finds changesets that were closed after T1 and created before T2 |
    | `from` | T1 (& to=T2) | Finds changesets created at or after T1, and (optionally) before T2 to requires **from**, but not vice-versa. If **to** is provided alone, it has no effect |
    | `open` or `close` | true | Only finds changesets that are still open but excludes changesets that are closed **or** have reached the element limit for a changeset. Alternatively only finds changesets that are closed **or** have reached the element limit |
    | `changesets` | #cid | Finds changesets with the specified IDs |
    | `order` | newest / oldest | If newest (default), sort from newest changesets first. If oldest, reverse order |
    | `limit` | number (integer) | Specifies the maximum number of changesets returned. A number between 1 and the maximum limit value (currently 100). If omitted, the default limit value is used (currently 100). The actual maximum and default limit values can be found with a [capabilities request](get_api_capabilities.md) |

### Request

![](https://img.shields.io/badge/GET-green)

```
/api/0.6/changesets
```

| bbox | user ID | open/close | order | limit |
| :---: | :---: | :---: | :---: | :---: |
| 14.182, 49.969, 19.011, 51.839 | 22098 | closed | oldest | 10 |

``` title="Request with example body"
/api/0.6/changesets?bbox=14.182,49.969,19.011,51.839&user=22098&closed=true&order=oldest&limit=10
```

### Response

![](https://img.shields.io/badge/Response-200%20OK-brightgreen)

``` xml linenums="1" hl_lines="3-13"
<?xml version="1.0" encoding="UTF-8"?>
<osm version="0.6" generator="OpenStreetMap server" copyright="OpenStreetMap and contributors" attribution="http://www.openstreetmap.org/copyright" license="http://opendatacommons.org/licenses/odbl/1-0/">
    <changeset id="412384" created_at="2025-04-23T10:57:06Z" open="false" comments_count="0" changes_count="1" closed_at="2025-04-23T11:51:26Z" min_lat="50.8038794" min_lon="16.2646154" max_lat="50.8038794" max_lon="16.2646154" uid="22098" user="JayStecki">
        <tag k="comment" v="Open changest for node add"/>
        <tag k="created_by" v="JayStecki Test (via Postman)"/>
    </changeset>
    <changeset id="412389" created_at="2025-04-23T12:06:54Z" open="false" comments_count="0" changes_count="9" closed_at="2025-04-23T17:00:37Z" min_lat="50.8038088" min_lon="16.2646154" max_lat="50.8039354" max_lon="16.2648524" uid="22098" user="JayStecki">
        <tag k="comment" v="Open changeset for add/update/delete elements"/>
        <tag k="created_by" v="JayStecki osmAPIdoc test (via Postman)"/>
    </changeset>
    <changeset id="412421" created_at="2025-04-23T17:37:10Z" open="false" comments_count="0" changes_count="7" closed_at="2025-04-23T18:13:07Z" min_lat="50.8038088" min_lon="16.2646154" max_lat="50.8039354" max_lon="16.2648524" uid="22098" user="JayStecki">
        <tag k="comment" v="Open changeset for delete elements"/>
        <tag k="created_by" v="JayStecki osmAPIdoc continue test (via Postman)"/>
    </changeset>
</osm>
```

### Error codes

=== "400 (**Bad Request**)"
    For misformed parameters, a text message explaining the error is returned. In particular, trying to provide both the `uid` and `display_name` as user query parameters will result in this error.
=== "404 (**Not Found**)"
    No user with the given `uid` or `display_name` could be found.