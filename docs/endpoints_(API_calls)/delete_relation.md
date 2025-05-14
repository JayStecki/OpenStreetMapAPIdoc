<div class="grid cards" markdown>

- :material-target: **One of the main OpenStreetMap API usabilities**

</div>

Deletes an existing [relation element](../general_information/elements.md#elements-description).

!!! warning "To delete existing relation you must operate inside an [open changeset](open_changeset.md)."
    Insert the ongoing changeset ID `changeset` to the `request body`. After completing various operations on the element, you should [close a changset](close_changeset.md) (or it will [close automatically](../general_information/changesets.md#changesets-attributes)). You can also do multiple operations on many elements (create, update, delete) in one ongoing changeset.

In `request body` the relation ID `id` and relation version `version` are also required (check the example).

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

=== "400 (**Bad Request**)"
    When there are errors parsing the XML (a text message explaining the error is returned). When a changeset ID is missing, when a node is outside the world. When the version of the provided element does not match the current database version of the element.
=== "404 (**Not Found**)"
    When no element with the given ID could be found (example: *Requested resource could not be found*).
=== "409 (**Conflict**)"
    If the changeset in question has already been closed either by the user, or as a result of the auto-closing feature (example: *The changeset 412384 was closed at 2025-04-23 11:51:26 UTC*). Also, if the user trying to update the changeset is not the same as the one that created it.
=== "410 (**Gone**)"
    If the element has been deleted (example: *Requested content is permanently deleted from the server*).
=== "412 (**Precondition Failed**)"
    When a relation is still member of another relation.
=== "429 (**Too Many Requests**)"
    When the request has been blocked due to rate limiting.