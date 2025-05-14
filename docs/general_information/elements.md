There are API calls to [CRUD](#operations-on-the-osm-elements) the three basic elements that build the map data for OpenStreetMap. They each return or expect the data for the elements in the **XML format**.

## Elements description

Elements are the basic components of OpenStreetMap's conceptual data model of the physical world. There are three types of elements:

- **nodes** (defining points in space),
    ``` xml title="node_example.xml" linenums="1"
    <node id="25496583" lat="51.5173639" lon="-0.140043" version="1" changeset="203496" user="80n" uid="1238" visible="true" timestamp="2007-01-28T11:40:26Z">
    <tag k="highway" v="traffic_signals"/>
    </node>
    ```
- **ways** (defining linear features and area boundaries as ordered list of nodes),
    ``` xml title="way_example.xml" linenums="1"
    <way id="5090250" visible="true" timestamp="2009-01-19T19:07:25Z" version="8" changeset="816806" user="Blumpsy" uid="64226">
    <nd ref="822403"/>
    <nd ref="21533912"/>
    <nd ref="821601"/>
    <nd ref="21533910"/>
    <nd ref="135791608"/>
    <nd ref="333725784"/>
    <nd ref="333725781"/>
    <nd ref="333725774"/>
    <nd ref="333725776"/>
    <nd ref="823771"/>
    <tag k="highway" v="residential"/>
    <tag k="name" v="Clipstone Street"/>
    <tag k="oneway" v="yes"/>
    </way>
    ```
- **relations** (defining how other elements work together as structured collections of objects – nodes, ways and other relations).
    ``` xml title="relation_example.xml" linenums="1"
    <relation id="13092746" visible="true" version="7" changeset="118825758" timestamp="2022-03-23T15:05:48Z" user="" uid="">
    <member type="node" ref="5690770815" role="stop"/>
    <member type="node" ref="5751940550" role="stop"/>
    ...
    <member type="node" ref="1764649495" role="stop"/>
    <member type="way" ref="96562914" role=""/>
    ...
    <member type="way" ref="928474550" role=""/>
    <tag k="from" v="Encre"/>
    <tag k="name" v="9-Montagnes de Guyane"/>
    <tag k="network" v="Agglo'bus"/>
    <tag k="not:network:wikidata" v="Q3537943"/>
    <tag k="operator" v="CACL"/>
    <tag k="ref" v="9"/>
    <tag k="route" v="bus"/>
    <tag k="source" v="https://www.cacl-guyane.fr/wp-content/uploads/2021/01/PLAN-RESEAU-URBAIN-AGGLO-BUS-1.pdf"/>
    <tag k="to" v="Lycée Balata"/>
    <tag k="type" v="route"/>
    <tag k="website" v="https://www.cacl-guyane.fr/lagglo-au-quotidien/se-deplacer/transport-urbain-2/"/>
    </relation>
    ```
### Operations on the OSM elements

Table with all available calls in API v0.6, including those [not covered in this documentation](../index.md). Calls included in the documentation **are marked in bold**.

| Create, read, update, delete | Available calls |
| :---: | --- |
| ![](https://img.shields.io/badge/GET-green) | **Check available API versions**, **Check API capabilities**, **Receive map data by bbox**, **Receive API permissions**, Read changeset with ID, Download changeset, **Read list of changeset**, **Read node by ID**, **Read way by ID**, **Read relation by ID**, Node with ID history, Way with ID history, Relation with ID history, Node with ID version, Way with ID version, Relation with ID version, Multi fetch nodes parameters, Multi fetch ways parameters, Multi fetch relations parameters, Relations for node with ID, Relations for way with ID, Relations for relation with ID, Read way full references, Read relation full references, Download GPX metadata, Download GPX with ID data, List GPX traces by user, Details of user by ID, Details of multiple users by IDs, **Details of logged-in user**, Read preferences of logged-in user, Read preferences of logged-in user by bbox, Read notes by ID, **Search for notes**, RSS feed notes, Check user blocks by ID, List active blocks |
| ![](https://img.shields.io/badge/POST-blue) | Diff upload changesets by ID, Add a comment to a changeset with ID, Subscribe the discussion of a changeset with ID, Unhide changeset comments with ID, **Create node**, **Create way**, **Create relation**, Redaction for node with ID, Redaction for way with ID, Redaction for relation with ID, Create GPX, **Create note**, Add comment to note with ID, Close fixed notes, Reopen closed note, Subscribe the discussion of a note with ID, Create user blocks |
| ![](https://img.shields.io/badge/PUT-lightblue) | **Create changeset**, Update changeset by ID, **Close changeset**, **Update node by ID**, **Update way by ID**, **Update relation by ID**, Update GPX by ID, Update preferences of the logged-in user |
| ![](https://img.shields.io/badge/DELETE-red) | Unsubscribe from the discussion of a changeset with ID, Hide changeset comment with ID, **Delete node with ID**, **Delete way with ID**, **Delete relation with ID**, Delete GPX with ID, Delete user preferences, Delete a note with ID, Unsubscribe the discussion of a note with ID |

## Common attributes

Within the OSM database, we store these attributes for nodes, ways and relations. Your application may not need to make use of all of them, and some third-party extracts produced from OSM data may not reproduce them all.

| Name | Value | Description |
| :---: | :---: | --- |
| ```id``` | integer (64-bit) | Identifying the element. Positive (>0) and negative (<0) values with their [inside logic](#the-logic-of-positive-and-negative-id-values). |
| ```user``` | (character) string | The display name of the user who last modified the object ([informative only and may be empty](#user-name-changing-case)). |
| ```uid``` | integer | The numeric identifier of the user who last modified the object. User identifiers never change. |
| ```timestamp``` | [^^W3C standard date and time formats^^](https://www.w3.org/TR/NOTE-datetime){:target="_blank"} | Time of the last modification - without fractional seconds (example: *2016-12-31T23:59:59Z*). |
| ```visible``` | true or false | Whether the object is deleted or not in the database (if visible=false then the object should only be returned by history calls). |
| ```version``` | integer | The edit version of the object specified by the [server logic](#version-manage-logic). |
| ```changeset``` | integer | The changeset number in which the object was created or updated (supporting 64-bit is recommended in applications for compatibility with long term evolution of the OSM database; applications that only query data without updating them may ignore this informative attribute). |

#### The logic of positive and negative ID values

??? info "Positive values (>0)"
    Used for all existing elements (and will remain assigned when they are modified or deleted).

??? info "Negative values (<0)"
    Reserved (their is scope limited to the current changeset and never stored in the database) and only used when sending data to the OSM database for identifying new objects to create and reference them in other created or modified objects (the server will replace these temporary identifiers sent by the editing application, by assigning an actual positive identifier for each created object, and will return a mapping from the negative identifiers used to their assigned positive identifiers).

#### User name changing case

!!! note "A user can change their display name at any time"
    The existing elements will reflect the new user name without any version change.

#### Version manage logic

??? info "Object's lifecycle"
    Newly created objects start at version 1 and the value is incremented by the server when a client uploads a new version of the object. The server will reject a new version of an object if the version sent by the client does not match the current version of the object in the database.

## XML caution and notes on nomenclature

The major tools in the OSM universe use an XML format following an XML schema definition that was first used by the API only. The set of OSM XML elements referred to in the documentation is a subset of the actual XML elements found in the data. This means the terms **Element in XML** and **Element in OSM XML** are not synonymous.

!!! warning "Component integrity"
    Elements in the OSM data are defined as either node, way, or relation. XML elements `tag`, `nd`, and `member` are not referred to as elements in OSM XML but they are indeed XML elements.

Users of XML tools should also be aware that nodes, ways and relations share the same object ID space. The OSM objects must always be referred to both with their object `ids` and their respective object type (node, way, relation).