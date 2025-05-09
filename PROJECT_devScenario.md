# OpenStreetMap API documentation - dev scenario

> Case study intended for [PROJECT_plan](PROJECT_plan.md).

## Persona

> Frontend Dev (junior/mid) delegated to code a simple plugin that will use the OSM API.

## Usability task

> From approximetly 40 endpoints at least 1/3 (min. 13) must be selected and used to work with elements[^1](#footnotes), changesets[^2](#footnotes) and tags[^3](#footnotes). Use only XML request and response format for choosed endpoints (to keep consistent ignore JSON, because all of API call includes XML and only part of them XML + JSON).

---

### Footnotes

[^1]:

[Elements by OSM doc](https://wiki.openstreetmap.org/wiki/Elements)

> Elements are the basic components of OpenStreetMap's conceptual data model of the physical world. There are three types of elements:
- nodes (defining points in space),
- ways (defining linear features and area boundaries),
- relations (defining how other elements work together).

[^2]:

[Changesets by OSM doc](https://wiki.openstreetmap.org/wiki/API_v0.6#Changesets_2)

> Every [modification](#operations-on-elements) of one or more of the elements has to reference an open changeset.

[^3]:

[Tags by OSM docs](https://wiki.openstreetmap.org/wiki/Tags)

> Every element and [changeset](#changesets-attribute) may have any number of tags. A tag is a Key-Value pair of Unicode strings of up to 255 full unicode characters (not bytes) each.