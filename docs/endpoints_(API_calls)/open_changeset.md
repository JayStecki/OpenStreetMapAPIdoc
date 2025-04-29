<div class="grid cards" markdown>

- :material-target: **One of the main OpenStreetMap API usability**.

</div>

!!! note "Required before creating/updating/deleting every element (node, way, relation)."
    You should manually [close the changeset](close_changeset.md) after the process, otherwise it will [close automatically](../general_informations/changesets.md#changesets-attributes).

### Request

![](https://img.shields.io/badge/PUT-lightblue)

```
/api/0.6/changeset/create
```

``` xml title="changesetBody_example.xml"
<osm>
  <changeset>
    <tag k="created_by" v="JayStecki Test (via Postman)"/>
    <tag k="comment" v="Open changeset for node add"/>
  </changeset>
</osm>
```

### Response

![](https://img.shields.io/badge/Response-200%20OK-brightgreen)

``` xml title="changesetID_example.xml" linenums="1"
412384
```

### Error codes

=== "400 (**Bad Request**)"
    When there are errors parsing the XML.
=== "405 (**Method Not Allowed**)"
    If the request is not a (HTTP) **PUT** request.