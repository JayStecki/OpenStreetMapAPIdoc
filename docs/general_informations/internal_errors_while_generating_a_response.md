Internal errors while generating a response. In the unlikely event of an **internal error** occurring while generating the response to an API call, an error element will be inserted. **Further processing stops at this point**.

!!! warning "Internal error with correct HTTP"
    Even though the HTTP return code is 200, and the response is syntactically correct, the message will be incomplete, and **must be discarded** by editing applications. For further analysis, editing applications **should report** an internal API error back to the user, along with the error message returned by the API call.

``` json title="wayWithTag_example.json" linenums="1" hl_lines="35"
{
  "version": "0.6",
  "generator": "CGImap 0.8.7 (22730 ubuntu)",
  "copyright": "OpenStreetMap and contributors",
  "attribution": "http://www.openstreetmap.org/copyright",
  "license": "http://opendatacommons.org/licenses/odbl/1-0/",
  "elements": [
    {
      "type": "way",
      "id": 4000392204,
      "timestamp": "2022-07-26T20:56:27Z",
      "version": 1,
      "changeset": 1874689,
      "user": "mmd2",
      "uid": 1,
      "nodes": [
        5004686582,
        5004686236,
        5004686540,
        5004686705,
        5004686546,
        5004686468,
        5004686472
      ],
      "tags": {
        "bicycle": "use_sidepath",
        "highway": "secondary",
        "maxspeed": "50",
        "name": "Bunderstraat",
        "old_ref": "N586",
        "surface": "asphalt"
      }
    },
    {
      "error": "Mismatch in tags key and value size"
    }
  ]
}
```