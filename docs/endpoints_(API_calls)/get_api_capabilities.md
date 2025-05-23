<div class="grid cards" markdown>

- :material-target: **One of the main OpenStreetMap API usabilities**

</div>

This API call is meant to provide information about the capabilities and limitations of the current API.

!!! note "Returned values may change at any time and this XML document only serves as an example"
    Copyright, attribution, and license refers to legal information.

## Request

![](https://img.shields.io/badge/GET-green)

```
/api/capabilities
```

```
/api/0.6/capabilities
```

## Response

![](https://img.shields.io/badge/Response-200%20OK-brightgreen)

``` xml linenums="1" hl_lines="4-21"
<?xml version="1.0" encoding="UTF-8"?>
<osm version="0.6" generator="OpenStreetMap server" copyright="OpenStreetMap and contributors" attribution="https://www.openstreetmap.org/copyright" license="https://opendatacommons.org/licenses/odbl/1-0/">
	<api>
		<version minimum="0.6" maximum="0.6"/>
		<area maximum="0.25"/>
		<note_area maximum="25"/>
		<tracepoints per_page="5000"/>
		<waynodes maximum="2000"/>
		<relationmembers maximum="32000"/>
		<changesets maximum_elements="10000" default_query_limit="100" maximum_query_limit="100"/>
		<notes default_query_limit="100" maximum_query_limit="10000"/>
		<timeout seconds="300"/>
		<status database="online" api="online" gpx="online"/>
	</api>
	<policy>
		<imagery>
			<blacklist regex=".*\.google(apis)?\..*/(vt|kh)[\?/].*([xyz]=.*){3}.*"/>
			<blacklist regex="http://xdworld\.vworld\.kr:8080/.*"/>
			<blacklist regex=".*\.here\.com[/:].*"/>
		</imagery>
	</policy>
</osm>
```

## Additional information

!!! info "Attributes description"
    | Attribute | Description |
    | :---: | --- |
    | `version minimum` `maximum` | API call versions that the server will accept |
    | `area maximum` | Maximum area in square degrees that can be queried by API calls |
    | `tracepoints per_page` | Maximum number of points in a single GPS trace (possibly incorrect) |
    | `waynodes maximum` | Maximum number of nodes that a way may contain |
    | `relationmembers maximum` | Maximum number of members that a relation may contain |
    | `changesets maximum_elements` | Maximum number of combined nodes, ways and relations that can be contained in a changeset |
    | `changesets default_query_limit` `maximum_query_limit` | Default and maximum values of the limit parameter of changeset queries |
    | `notes default_query_limit` `maximum_query_limit` | Default and maximum values of the limit parameter of notes bounding box queries and search |
    | `status` | Returns either online, readonly or offline for each of the database, API and GPX API. The database field is informational, and the API/GPX fields indicate whether a client should expect read and write requests to work (online), only read requests to work (readonly) or no requests to work (offline) |
    | `policy` | Imagery blacklist lists all aerial and map sources, which are not permitted for OSM usage due to copyright. Editors must not show these resources as background layer |