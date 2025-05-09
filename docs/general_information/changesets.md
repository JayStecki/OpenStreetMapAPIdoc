Every [CRUD](elements.md#operations-on-osm-elements) modification of one or more of the [elements](elements.md) has to reference an **open changeset**. Changeset process (from open to close) works like a 'mini-commit' mechanism with every element's modification inside.

``` mermaid
stateDiagram-v2
  state "Open changeset (manually)" as OpenChangeset
  state "CRUD operations on elements" as CRUDElements
  state "Close changeset (manually or automatically)" as CloseChangeset

  OpenChangeset --> CRUDElements
  CRUDElements --> CloseChangeset
```

## Changesets attributes

- A changeset may contain [tags](tags.md) just like the other elements.
- A new changeset can be opened at any time and a changeset may be referenced from multiple API calls. Also new changeset:
      - can be closed manually,
      - mechanism is implemented to **automatically close** changesets in case:
          <div class="annotate" markdown>
          - of 10,000 edits on a single changeset(1),
          - the changeset has been open for more than 24 hours,
          - there have been no changes/API calls related to a changeset in 1 hour (so called idle timeout).
            </div>
            1. Some older changesets may contain slightly more than 10k (or previously 50k) changes due to some glitches in the API.
    - Changesets are specifically not atomic – elements added within a changeset will be visible to other users before the changeset is closed.
    - Changesets facilitate the implementation of rollbacks.
    - Server stores a bounding box for each changeset and allows users to query changesets in an area:
          - API computes the bounding box (rules beneath) associated with a changeset.
    - It is not possible to delete changesets at the moment, even if they don't contain any changes.

### Bounding box computation

??? info "Bounding box for [nodes](elements.md#elements-description)."
    Any change to a node, including deletion, adds the node's old and new location to the bounding box.

??? info "Bounding box for [ways](elements.md#elements-description)."
    Any change to a way, including deletion, adds all of the way's nodes to the bounding box.

??? info "Bounding box for [relations](elements.md#elements-description)."
    - Adding or removing nodes or ways from a relation causes them to be added to the changeset bounding box.
    - Adding a relation as a member or changing tag values causes all node and way members to be added to the bounding box.
    - This is similar to how the map call does things and is reasonable on the assumption that adding or removing members doesn't materially change the rest of the relation.

As an optimisation the server will create a buffer slightly larger than the objects to avoid having to update the bounding box too often(1).
{ .annotate }

1. Thus a changeset may have a different bbox than its reversion, and the distance between bbox and the next node may not be constant for all four directions.