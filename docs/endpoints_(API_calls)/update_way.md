<div class="grid cards" markdown>

- :material-target: **One of the main OpenStreetMap API usabilities**

</div>

Updates data for a existing [way element](../general_information/elements.md#elements-description).

!!! warning "To update existing way you must operate inside an [open changeset](open_changeset.md)"
    Insert the ongoing changeset ID `changeset` to the request body. After completing various operations on the element, you should [close a changset](close_changeset.md) (or it will [close automatically](../general_information/changesets.md#changesets-attributes)). You can also do multiple operations on many elements (create, update, delete) in one ongoing changeset.

In request body the way ID `id`, way version `version`, node's IDs `nd ref` and way tags `tags` are also required (check the example).

!!! note "A full representation of the element as it should be after the update has to be provided"
    Any tags, way-node refs, and relation members that remain unchanged **must be in the update** as well. Also, a version number must be provided as well, it must match the current version of the element in the database.

### Request

![](https://img.shields.io/badge/PUT-lightblue)

```
/api/0.6/way/{id}
```

``` xml linenums="1" hl_lines="3-8" title="Example body request for update way with ID" hl_lines="2-5"
<osm>
  <way id="4307240014" version="1" changeset="412389">
    <nd ref="4359470504"/>
    <nd ref="4359471036"/>
    <tag k="highway" v="footway"/>
    <tag k="JayStecki" v="Boundary (1) for a plot in the ROD-Association garden"/>
    <tag k="surface" v="gravel"/>
  </way>
</osm>
```

### Response

![](https://img.shields.io/badge/Response-200%20OK-brightgreen)

``` xml title="succesUpdateWay_example.xml" linenums="1"
2
```

### Error codes

=== "400 (**Bad Request**)"
    When there are errors parsing the XML – a text message explaining the error is returned (example: *Version is required when updating*). This can also happen if you forget to pass the Content-Length header. When a changeset ID is missing, when a node is outside the world, when there are too many nodes for a way.
=== "404 (**Not Found**)"
    When no element with the given ID could be found (example: *Requested resource could not be found*).
=== "409 (**Conflict**)"
    If the changeset in question has already been closed – either by the user itself, or as a result of the auto-closing feature (example: *The changeset 412384 was closed at 2025-04-23 11:51:26 UTC*). Also, if the user trying to update the changeset is not the same as the one that created it.
=== "412 (**Precondition Failed**)"
    When a way has nodes that do not exist, were deleted or aren't visible.
=== "429 (**Too Many Requests**)"
    When the request has been blocked due to rate limiting.