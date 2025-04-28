Internal errors while generating a response.<!--powtórzenie nagłówka--> In the unlikely event of an **internal error** occurring while generating the response to an API call, an error element will be inserted. **Further processing stops at this point**.<!--niepotrzebne pobrubienie-->

!!! warning "Internal error with correct HTTP"
    Even though the HTTP return code is 200, and the response is syntactically correct, the message will be incomplete, and **must be discarded** by editing applications. For further analysis, editing applications **should report** an internal API error back to the user, along with the error message returned by the API call.<!--niepotrzebne pobrubienia-->

``` xml title="wayWithTag_example.xml" linenums="1" hl_lines="18"
<?xml version="1.0" encoding="UTF-8"?>
<osm version="0.6" generator="CGImap 0.8.7 (26234 ubuntu)" copyright="OpenStreetMap and contributors" attribution="http://www.openstreetmap.org/copyright" license="http://opendatacommons.org/licenses/odbl/1-0/">
 <way id="4000392204" visible="true" version="1" changeset="1874689" timestamp="2022-07-26T20:56:27Z" user="mmd2" uid="1">
  <nd ref="5004686582"/>
  <nd ref="5004686236"/>
  <nd ref="5004686540"/>
  <nd ref="5004686705"/>
  <nd ref="5004686546"/>
  <nd ref="5004686468"/>
  <nd ref="5004686472"/>
  <tag k="bicycle" v="use_sidepath"/>
  <tag k="highway" v="secondary"/>
  <tag k="maxspeed" v="50"/>
  <tag k="name" v="Bunderstraat"/>
  <tag k="old_ref" v="N586"/>
  <tag k="surface" v="asphalt"/>
 </way>
 <error>Mismatch in tags key and value size</error>
</osm>
```