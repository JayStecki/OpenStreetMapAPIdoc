<div class="grid cards" markdown>

- :material-target: **One of the main OpenStreetMap API usability**.

</div>

Creates a new node element.

!!! warning "To create new node, **first** you must operate inside [open changeset](open_changeset.md)."
    Insert the ongoing ==changeset ID== to the `request body`. After completing various operations on the element, you should [close a changset](close_changeset.md) (or it will [close automatically](../general_informations/changesets.md#changesets-attributes)). You can also do multiple operations on many elements (create, update, delete) in one ongoing changeset.

In `request body` the ==longitude== and ==latitude== are also required (check the example).

### Request

![](https://img.shields.io/badge/POST-blue)

```
/api/0.6/nodes
```

``` xml title="createNodeBody_example.xml" hl_lines="2"
<osm>
  <node changeset="412389" lat="50.8039354" lon="16.2648005">
    <tag k="amenity" v="garden"/>
    <tag k="name" v="Node (2nd) for a plot in the ROD-Association garden"/>
  </node>
</osm>
```

### Response

![](https://img.shields.io/badge/Response-200%20OK-brightgreen)

``` xml title="nodeID_example.xml" linenums="1"
4359471036
```

### Error codes

=== "400 (**Bad request**)"
    When there are errors parsing the XML (a text message explaining the error is returned). When a **changeset ID is missing**, when a node is outside the world.<!--niepotrzebne pogrubienie-->
=== "405 (**Method not allowed**)"
    If the request is **not a POST** request.<!--niepotrzebne pogrubienie-->
=== "409 (**Conflict**)"
    If the changeset in question has already been closed either by the user or as a result of the auto-closing feature (example: *The changeset 412384 was closed at 2025-04-23 11:51:26 UTC*). Also, if the user trying to update the changeset is not the same as the one that created it.
=== "429 (**Too many requests**)"
    When the request has been blocked due to rate limiting.