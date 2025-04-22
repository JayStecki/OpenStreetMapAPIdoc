<div class="grid cards" markdown>

- :material-target: **One of the main OpenStreetMap API usability**.

</div>

Updates data from a preexisting element.

!!! note "A full representation of the element as it should be after the update has to be provided."
    Any tags, way-node refs, and relation members that remain unchanged must be in the update as well. A version number must be provided as well, **it must match** the current version of the element in the database.
<!--- all below not done yet-->
### Request

![](https://img.shields.io/badge/PUT-lightblue)

```
/api/0.6/node/{id}
```

### Response

![](https://img.shields.io/badge/Response-200%20OK-brightgreen)

### Error codes

=== "400 (**Bad request**)"
    Body

### Additional