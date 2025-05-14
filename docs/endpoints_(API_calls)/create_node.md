<div class="grid cards" markdown>

- :material-target: **One of the main OpenStreetMap API usabilities**

</div>

Creates a new [node element](../general_information/elements.md#elements-description). In response you will receive node ID.

!!! warning "To create new node you must operate inside an [open changeset](open_changeset.md)"
    Insert the ongoing changeset ID `changeset` to the `request body`. After completing various operations on the element, you should [close a changset](close_changeset.md) (or it will [close automatically](../general_information/changesets.md#changesets-attributes)). You can also do multiple operations on many elements (create, update, delete) in one ongoing changeset.

In `request body` the node's latitude `lat` and longitude `lon` are also required (check the example).

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

=== "400 (**Bad Request**)"
    When there are errors parsing the XML (a text message explaining the error is returned). When a changeset ID is missing, when a node is outside the world.
=== "405 (**Method Not Allowed**)"
    If the request is not a (HTTP) **POST** request.
=== "409 (**Conflict**)"
    If the changeset in question has already been closed - either by the user itself, or as a result of the auto-closing feature (example: *The changeset 412384 was closed at 2025-04-23 11:51:26 UTC*). Also, if the user trying to update the changeset is not the same, as the one that created it.
=== "429 (**Too Many Requests**)"
    When the request has been blocked due to rate limiting.