<div class="grid cards" markdown>

- :material-target: **One of the main OpenStreetMap API usability**.

</div>

Creates a new way element.

!!! warning "To create new way, **first** you must operate inside [open changeset](open_changeset.md)."
    Insert the ongoing ==changeset ID== to the `request body`. After completing various operations on the element, you should [close a changset](close_changeset.md) (or it will [close automatically](../general_informations/changesets.md#changesets-attributes)). You can also do multiple operations on many elements (create, update, delete) in one ongoing changeset.

In `request body` the node's IDs (==nd ref==) and ==tag== is also required (check the example).

### Request

![](https://img.shields.io/badge/POST-blue)

```
/api/0.6/ways
```

``` xml title="createWayBody_example.xml" hl_lines="2-5"
<osm>
  <way changeset="412389">
    <nd ref="4359470504"/>
    <nd ref="4359471036"/>
    <tag k="highway" v="footway"/>
    <tag k="JayStecki" v="Boundary for a plot in the ROD-Association garden"/>
  </way>
</osm>
```

### Response

![](https://img.shields.io/badge/Response-200%20OK-brightgreen)

``` xml title="wayID_example.xml" linenums="1"
4307240014
```

### Error codes

=== "400 (**Bad Request**)"
    When there are errors parsing the XML (a text message explaining the error is returned). When a changeset ID is missing, when there are too many nodes for a way.
=== "405 (**Method Not Allowed**)"
    If the request is not a (HTTP) **POST** request.
=== "409 (**Conflict**)"
    If the changeset in question has already been closed either by the user or as a result of the auto-closing feature (example: *The changeset 412384 was closed at 2025-04-23 11:51:26 UTC*). Also, if the user trying to update the changeset is not the same as the one that created it.
=== "412 (**Precondition Failed**)"
    When a way has nodes that do not exist, were deleted or aren't visible.
=== "429 (**Too Many Requests**)"
    When the request has been blocked due to rate limiting.