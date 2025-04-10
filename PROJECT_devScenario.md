# OpenStreetMap API documentation - dev scenario
> Case study dedicated for [PROJECT_plan](PROJECT_plan.md).
## Persona
> Frontend Dev (junior/mid) delegated to code simple plugin (via usability task), that will be using OpenStreetMap API.
## Usability task
> From approximetly 40 endpoints at least 1/3 (min. 13) must be selected and used to easy work with elements[^1](#footnotes), changesets[^2](#footnotes) and tags[^3](#footnotes). Include JSON format only for choosed endpoints.
---
### Footnotes
[^1]:

[elements by OSM doc](https://wiki.openstreetmap.org/wiki/Elements){:target="_blank"}

Elements are the basic components of OpenStreetMap's conceptual data model of the physical world. There are three types of elements:
- nodes (defining points in space),
- ways (defining linear features and area boundaries),
- relations (defining how other elements work together).

#### Operations on elements:
| CRUD (create, read, update, delete) | calls |
| --- | --- |
| GET | :read, :history, :multifetch, :relations for element, :ways for node, :full |
| POST | :create, :redaction |
| PUT | :update |
| DELETE | :delete |

[^2]:

[changesets by OSM doc](https://wiki.openstreetmap.org/wiki/API_v0.6#Changesets_2){:target="_blank"}

> Every [modification](#operations-on-elements) of one or more of the elements has to reference an open changeset.

#### Changesets attribute

- A changeset may contain tags just like the other elements.
- A new changeset can be opened at any time and a changeset may be referenced from multiple API calls. Also new changeset:
  - can be closed manually.
  - Mechanism is implemented to automatically close changesets:
    - 10,000 edits on a single changeset,
    - the changeset has been open for more than 24 hours,
    - there have been no changes/API calls related to a changeset in 1 hour (i.e. idle timeout).
- Changesets are specifically not atomic - elements added within a changeset will be visible to other users before the changeset is closed.
- Changesets facilitate the implementation of rollbacks.
- Server stores a bounding box for each changeset and allows users to query changesets in an area:
  - API computes the bounding box associated with a changeset.
- It is not possible to delete changesets at the moment, even if they don't contain any changes.

[^3]:

[tags by OSM docs](https://wiki.openstreetmap.org/wiki/Tags){:target="_blank"}

Every element and [changeset](#changesets-attribute) may have any number of tags. A tag is a Key-Value pair of Unicode strings of up to 255 full unicode characters (not bytes) each.

#### Existing keys and tags statistics

At this moment (march 2025) OSM API contains 12941 tags with 101235 keys. Current data here:

https://taginfo.openstreetmap.org/