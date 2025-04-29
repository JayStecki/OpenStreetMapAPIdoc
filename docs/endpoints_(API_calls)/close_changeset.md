<div class="grid cards" markdown>

- :material-target: **One of the main OpenStreetMap API usability**.

</div>

!!! note "Required after creating/updating/deleting every element (node, way, relation)."
    You should manually [close the changeset](close_changeset.md) after the process, otherwise it will [close automatically](../general_informations/changesets.md#changesets-attributes).

### Request

![](https://img.shields.io/badge/PUT-lightblue)

```
/api/0.6/changeset/{id}/close
```

### Response

![](https://img.shields.io/badge/Response-200%20OK-brightgreen)

``` title="succesCloseChangeset_example.xml" linenums="1"

```

### Error codes

=== "404 (**Not Found**)"
    When no changeset with the given id could be found.
=== "405 (**Method Not Allowed**)"
    If the request is not a (HTTP) **PUT** request.
=== "409 (**Conflict**)"
    If the changeset in question has already been closed either by the user, or as a result of the auto-closing feature (example: *The changeset 412384 was closed at 2025-04-23 11:51:26 UTC*). Also, if the user trying to update the changeset is not the same as the one that created it.