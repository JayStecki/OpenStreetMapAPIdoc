<div class="grid cards" markdown>

- :material-target: **One of the main usability features OpenStreetMap API**.

</div>

Deletes an existing relation element.

!!! warning "To delete an existing relation, you must **first** operate inside [open changeset](open_changeset.md)."
    Insert the ongoing ==changeset ID== to the `request body`. After completing various operations on the element, you can [close a changset](close_changeset.md) (or it will [close automatically](../general_informations/changesets.md#changesets-attributes)). You can also do multiple operations on many elements (create, update, delete) in one ongoing changeset.

In `request body` the ==relation ID== and ==version== are also required (check the example).

### Request

![](https://img.shields.io/badge/DELETE-red)

```
/api/0.6/relation/{id}
```

``` xml title="deleteRelationBody_example.xml" linenums="1" hl_lines="2"
<osm>
  <relation id="4305233945" version="2" changeset="412421"/>
</osm>
```

### Response

![](https://img.shields.io/badge/Response-200%20OK-brightgreen)

``` xml title="succesDeleteRelation_example.xml" linenums="1"
3
```

### Error codes

=== "400 (**Bad request**)"
    When there are errors parsing the XML (a text message explaining the error is returned). When a **changeset ID is missing** or when a node is outside the world. When the **version** of the provided element does not match the current database version of the element.
=== "404 (**Not found**)"
    When no element with the given ID could be found (*Requested resource could not be found*).
=== "409 (**Conflict**)"
    If the changeset in question has already been closed - either by the user itself, or as a result of the auto-closing feature (example: *The changeset 412384 was closed at 2025-04-23 11:51:26 UTC*). Also if the user trying to update the changeset is not the same, as the one that created it.
=== "410 (**Gone**)"
    If the element has been **deleted** (*Requested content is permanently deleted from the server*).
=== "412 (**Precondition failed**)"
    When a relation is still member of another relation.
=== "429 (**Too many requests**)"
    When the request has been blocked due to rate limiting.