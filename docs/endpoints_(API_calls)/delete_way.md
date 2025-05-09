<div class="grid cards" markdown>

- :material-target: **One of the main OpenStreetMap API usability**.

</div>

Deletes an existing [way element](../general_information/elements.md#elements-description).

!!! warning "To delete existing way, **first** you must operate inside [open changeset](open_changeset.md)."
    Insert the ongoing ==changeset ID== to the `request body`. After completing various operations on the element, you should [close a changset](close_changeset.md) (or it will [close automatically](../general_information/changesets.md#changesets-attributes)). You can also do multiple operations on many elements (create, update, delete) in one ongoing changeset.

In `request body` the ==way ID== and ==version== is also required (check the example).

### Request

![](https://img.shields.io/badge/DELETE-red)

```
/api/0.6/way/{id}
```

``` xml title="deleteWayBody_example.xml" linenums="1" hl_lines="2"
<osm>
  <way id="4307240017" version="1" changeset="412421"/>
</osm>
```

### Response

![](https://img.shields.io/badge/Response-200%20OK-brightgreen)

``` xml title="succesDeleteWay_example.xml" linenums="1"
2
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
    When a way is still member of a relation.
=== "429 (**Too Many Requests**)"
    When the request has been blocked due to rate limiting.