<div class="grid cards" markdown>

- :material-target: **One of the main OpenStreetMap API usabilities**

</div>

Updates data for an existing [node element](../general_information/elements.md#elements-description).

!!! warning "To update existing node you must operate inside an [open changeset](open_changeset.md)"
    Insert the ongoing changeset ID `changeset` to the `request body`. After completing various operations on the element, you should [close a changset](close_changeset.md) (or it will [close automatically](../general_information/changesets.md#changesets-attributes)). You can also do multiple operations on many elements (create, update, delete) in one ongoing changeset.

In `request body` the node ID `id`, latitude `lat`, longitude `lon` and node version `version` are also required (check the example).

!!! note "A full representation of the element as it should be after the update has to be provided"
    Any tags, way-node refs, and relation members that remain unchanged **must be in the update** as well. Also, a version number must be provided as well, it must match the current version of the element in the database.

### Request

![](https://img.shields.io/badge/PUT-lightblue)

```
/api/0.6/node/{id}
```

``` xml title="updateNodeBody_example.xml" hl_lines="2"
<osm>
  <node id="4359470504" lat="50.8038794" lon="16.2646154" version="1" changeset="412389">
    <tag k="amenity" v="garden"/>
    <tag k="name" v="Node (1) for a plot in the ROD-Association garden"/>
  </node>
</osm>
```

### Response

![](https://img.shields.io/badge/Response-200%20OK-brightgreen)

``` xml title="succesUpdateNode_example.xml" linenums="1"
2
```

### Error codes

=== "400 (**Bad Request**)"
    When there are errors parsing the XML – a text message explaining the error is returned (example: *Version is required when updating*). This can also happen if you forget to pass the Content-Length header. When a changeset ID is missing, when a node is outside the world.
=== "404 (**Not Found**)"
    When no element with the given ID could be found (example: *Requested resource could not be found*).
=== "409 (**Conflict**)"
    If the changeset in question has already been closed – either by the user or as a result of the auto-closing feature (example: *The changeset 412384 was closed at 2025-04-23 11:51:26 UTC*). Also if the user trying to update the changeset is not the same, as the one that created it.
=== "429 (**Too Many Requests**)"
    When the request has been blocked due to rate limiting.