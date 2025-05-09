Version numbers and optimistic locking. The planet dump, diffs and the API calls for elements will return a ```version``` attribute for each element ([node, way and relation](elements.md#elements-description)). These version numbers are used for optimistic locking.

``` xml title="nodeVersion_example.xml" linenums="1"
<node id="68" ... version="12"/>
```

To upload a new version of an object, the client will need to provide the `version` of the object it is modifying. If the version supplied is not the same as the server's current version, an error will be returned. This means that any client that is updating data will need to save the version numbers of the original data. One element can be updated multiple times during one [changeset](changesets.md) and its version number is increased each time so there can be multiple history versions of a single element for one changeset.

## Error codes

HTTP status code (400-500).

=== "409 (**Conflict**)"
    Conflict between the current state of a resource and the client's request.