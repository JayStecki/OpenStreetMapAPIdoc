<div class="grid cards" markdown>

- :material-target: **One of the main OpenStreetMap API usability**.

</div>

Updates data for a existing relation element.

!!! warning "To update existing relation, **first** you must operate inside [open changeset](open_changeset.md)."
     Insert the ongoing ==changeset ID== to the `request body`. After completing various operations on the element, you should [close a changset](close_changeset.md) (or it will [close automatically](../general_informations/changesets.md#changesets-attributes)). You can also do multiple operations on many elements (create, update, delete) in one ongoing changeset.

In `request body` the ==relation ID==, ==version==, ==role== and tag ==(k="type" v=" ")== is also required (check the example).

| Body parameters | Inserts options |
| :---: | :---: |
| (member) role= | "outer" / "inner" / "forward" / "backward" |
| (tag) k="type" | v="relation" / v="multipolygon" |

!!! note "A full representation of the element as it should be after the update has to be provided."
    Any tags, way-node refs, and relation members that remain unchanged **must be in the update** as well. A version number must be provided as well, it must match the current version of the element in the database.

### Request

![](https://img.shields.io/badge/PUT-lightblue)

```
/api/0.6/relation/{id}
```

``` xml title="updateRelationBody_example.xml" hl_lines="2-6"
<osm>
  <relation id="4305233945" version="1" changeset="412389">
    <member type="way" ref="4307240014" role="outer"/>
    <member type="way" ref="4307240017" role="outer"/>
    <tag k="landuse" v="garden"/>
    <tag k="type" v="multipolygon"/>
    <tag k="name" v="Fragment of plot no 103 on ROD-Association garden"/>
  </relation>
</osm>
```

### Response

![](https://img.shields.io/badge/Response-200%20OK-brightgreen)

```xml title="succesUpdateRelation_example.xml" linenums="1" hl_lines="3-8"
2
```

### Error codes

=== "400 (**Bad Request**)"
    When there are errors parsing the XML – a text message explaining the error is returned (example: *Version is required when updating*). This can also happen if you forget to pass the Content-Length header. When a changeset ID is missing.
=== "404 (**Not Found**)"
    When no element with the given ID could be found (example: *Requested resource could not be found*).
=== "409 (**Conflict**)"
    If the changeset in question has already been closed – either by the user or as a result of the auto-closing feature (example: *The changeset 412384 was closed at 2025-04-23 11:51:26 UTC*). Also, if the user trying to update the changeset is not the same, as the one that created it.
=== "412 (**Precondition Failed**)"
    When a relation has nodes that do not exist, were deleted or aren't visible.
=== "429 (**Too Many Requests**)"
    When the request has been blocked due to rate limiting.