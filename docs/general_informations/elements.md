There are API calls to [CRUD](#operations-on-osm-elements) the three basic **elements**, that make up the **map data** for OpenStreetMap. They each return or expect the data for the elements in a **XML format**.

## Elements description

Elements are the basic components of OpenStreetMap's conceptual data model of the physical world. There are **three types** of elements:

- **nodes** (defining points in space).
    ``` xml title="node_example.xml" linenums="1"
    <node id="25496583" lat="51.5173639" lon="-0.140043" version="1" changeset="203496" user="80n" uid="1238" visible="true" timestamp="2007-01-28T11:40:26Z">
    <tag k="highway" v="traffic_signals"/>
    </node>
    ```
- **ways** (defining linear features and area boundaries as ordered list of nodes).
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
### Operations on OSM elements
| CRUD (create, read, update, delete) | calls |
| :---: | --- |
| ![](https://img.shields.io/badge/GET-green) | :material-check: :read, :history, :multifetch, :relations for element, :ways for node, :full |
| ![](https://img.shields.io/badge/POST-blue) | :material-check-all: :create, :redaction |
| ![](https://img.shields.io/badge/PUT-lightblue) | :material-update: :update |
| ![](https://img.shields.io/badge/DELETE-red) | :material-close: :delete |

## Common attributes

Within the OSM database, we store these attributes for nodes, ways and relations. Your application may not need to make use of all of them, and some third-party extracts produced from OSM data may not reproduce them all.

| Name | Value | Description |
| :---: | --- | --- |
| ```id``` | integer (64-bit) | Identifying the element. Positive (>0) and negative (<0) values with their [inside logic](#id-positive-and-negative-values-logic). |
| ```user``` | (character) string | The display name of the user who last modified the object ([**informative only and may be empty**](#user-name-changing-case)). |
| ```uid``` | integer | The numeric identifier of the user who last modified the object. **User identifiers never change.** |
| ```timestamp``` | [^^W3C standard date and time formats^^](https://www.w3.org/TR/NOTE-datetime){:target="_blank"} | Time of the last modification - without fractional seconds (e.g. ==2016-12-31T23:59:59Z==). |
| ```visible``` | ==true== or ==false== | Whether the object is deleted or not in the database (if ==visible=false== then the object should only be returned by history calls). |
| ```version``` | integer | The edit version of the object specified by the [server logic](#version-manage-logic). |
| ```changeset``` | integer | The changeset number in which the object was created or updated (supporting 64-bit is recommended in applications for compatibility with long term evolution of the OSM database, but applications that only query data without updating them may ignore this informative attribute). |

#### ID positive and negative values logic

??? info "Positive values (>0)."
    Are used for all existing elements (and will remain assigned when they are modified or deleted).

??? info "Negative values (<0)."
    Are reserved (their scope limited to the current changeset and never stored in the database) and only used when sending data to the OSM database for identifying new objects to create and reference them in other created or modified objects (the server will replace these temporary identifiers sent by the editing application, by assigning an actual positive identifier for each created object, and will return a mapping from the negative identifiers used to their assigned positive identifiers).

#### User name changing case

!!! note "A user can change their display name at any time."
    Existing elements will reflect the new user name **without** needing any version change.

#### Version manage logic

??? info "Object's lifecycle."
    Newly created objects start at version 1 and the value is incremented by the server when a client uploads a new version of the object. The server will reject a new version of an object if the version sent by the client does not match the current version of the object in the database.

## XML Caution and Notes on Nomenclature

The major tools in the OSM universe use an XML format following a XML schema definition that was first used by the API only. The set of Elements in OSM XML that are referred to as elements in documentation are a subset of the actual XML elements found in the data. i.e. the **term Element in XML** and the **term Element in OSM XML** are not synonymous.

!!! warning "Component integrity"
    Elements in OSM data are defined as one of node, way, and relation. XML elements tag, nd, and member are not referred to as elements in OSM XML but they are indeed XML elements.

Users of XML tools should also be aware that nodes, ways and relations share the same object id space. OSM Objects must always be referred to both with their object ids and their respective object type (node, way, relation).