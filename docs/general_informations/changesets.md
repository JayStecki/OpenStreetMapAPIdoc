Every modification (CRUD) of one or more of the [elements](elements.md) has to reference an open changeset.

#### Changesets attributes

- A changeset may contain [tags](tags.md) just like the other elements.
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