<div class="grid cards" markdown>

- :material-target: **One of the main OpenStreetMap API usability**.

</div>

Creates a new relation element.

!!! warning "To create new relation, **first** you must operate inside [open changeset](open_changeset.md)."
    Insert the ongoing ==changeset ID== to the `request body`. After completing various operations on the element, you should [close a changset](close_changeset.md) (or it will [close automatically](../general_informations/changesets.md#changesets-attributes)). You can also do multiple operations on many elements (create, update, delete) in one ongoing changeset.

In `request body` the way's IDs (==ref==), ==role== and tag ==(k="type" v=" ")== are also required (check the example).

| Body parameters | Inserts options |
| :---: | :---: |
| (member) role= | "outer" / "inner" / "forward" / "backward" |
| (tag) k="type" | v="relation" / v="multipolygon" |

### Request

![](https://img.shields.io/badge/POST-blue)

```
/api/0.6/relations
```

``` xml title="createRelationBody_example.xml" hl_lines="2-6"
<osm>
  <relation changeset="412389">
    <member type="way" ref="4307240014" role="outer"/>
    <member type="way" ref="4307240017" role="outer"/>
    <tag k="type" v="multipolygon"/>
    <tag k="landuse" v="garden"/>
  </relation>
</osm>
```

### Response

![](https://img.shields.io/badge/Response-200%20OK-brightgreen)

``` xml title="relationID_example.xml" linenums="1"
4305233945
```

### Error codes

=== "400 (**Bad Request**)"
    When there are errors parsing the XML (a text message explaining the error is returned). When a changeset ID is missing.
=== "405 (**Method Not Allowed**)"
    If the request is not a (HTTP) **POST** request.
=== "409 (**Conflict**)"
    If the changeset in question has already been closed either by the user or as a result of the auto-closing feature (example: *The changeset 412384 was closed at 2025-04-23 11:51:26 UTC*). Also, if the user trying to update the changeset is not the same as the one that created it.
=== "412 (**Precondition Failed**)"
    When a relation has elements that do not exist (or do not exist anymore) or are not visible.
=== "429 (**Too Many Requests**)"
    When the request has been blocked due to rate limiting.